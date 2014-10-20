---
layout: post
title:  Poor Man Profiler - knowing CPU usage
keywords: profiler
quote: 
---

We usually face a situation that we don't know which parts in the program use more CPU time. Therefore, there are so many application profiler out there. For instance, [Oprofile](http://oprofile.sourceforge.net/news/) is a famous profiler, which could be used to monitor the application. [Poor Man Profiler](http://poormansprofiler.org/), however, could further provide the benefit of tracking the complete stack and profiling all threads of to the same process.

<!--more-->

Using Poor Man Profiler does not have to install other packages, as long as you have GDB in your computer (so it is for *nix-system only). The core of the profiler only relies on one line of code:

	gdb -ex "set pagination 0" -ex "thread apply all bt" -batch -p pid_of_your_program

## Demonstration

To demonstrate its powerness, I worte a perl program in the below. 

~~~ perl
#!/usr/bin/env perl -w
#############################################################
# poor_man_profiler.pl                                      #
#############################################################

use strict;
use warnings;

my $proc_name = shift @ARGV;

$SIG{INT}  = \&signal_handler;

my $output_string = "";
my %output_agg;
my %lib_agg;


my $stop_flag = 0;

my $result;
my $item;

print "START profiling....press [Ctrl-C] to stop\n";

my $pid = `pidof $proc_name`;

while(!$stop_flag) {
	$result = `gdb -ex "set pagination 0" -ex "thread apply all bt" -batch -p $pid`;
	
	for (split /^/, $result) {
		if ($_ =~ /^Thread/) {
			if ($output_string ne "") {
				if (not exists $output_agg{$output_string}) {
					$output_agg{$output_string} = 1;
				} else {
					$output_agg{$output_string}++;
				}

				$output_string = "";
			}
		}
		
		if ($_ =~ /^\#/) {
			my @s_result = split(' ', $_);

			if ($output_string ne "") {
				$output_string = $output_string.", ";
			}
			
			if ($s_result[2] eq "in") {
				$output_string = $output_string.$s_result[3];
			} elsif ($s_result[3] eq "at") {
				$output_string = "[at]".$output_string.$s_result[1];
			}
			
			if ($s_result[@s_result-1] ne "()") {
				my $get_lib = (split /\//, (split /:/, $s_result[@s_result-1])[0])[-1];
				
				if (not exists $lib_agg{$get_lib}) {
					$lib_agg{$get_lib} = 1;
				} else {
					$lib_agg{$get_lib}++;
				}
			
			
				$output_string = $output_string."(".$get_lib.")";
			}
		}
	}
	
	if ($output_string ne "") {
		if (not exists $output_agg{$output_string}) {
			$output_agg{$output_string} = 1;
		} else {
			$output_agg{$output_string}++;
		}
	}

	sleep (1);
}

print "profiling STOP!!!\n";

print "==\n";
my $total_output_percentage = 0;
foreach $item (keys %output_agg) {
	$total_output_percentage += $output_agg{$item};
}

my $output_percentage;
print "   samples |  %  | stack path\n";
foreach $item (sort {$output_agg{$b} <=> $output_agg{$a}} keys %output_agg) {
	$output_percentage = $output_agg{$item}/$total_output_percentage*100;
	printf "%10d | %3d | %s\n", ($output_agg{$item}, $output_percentage, $item);
}

print "==\n";
my $total_lib_percentage = 0;
foreach $item (keys %lib_agg) {
	$total_lib_percentage += $lib_agg{$item};
}

my $lib_percentage;
print "   samples |  %  | model name\n";
foreach $item (sort {$lib_agg{$b} <=> $lib_agg{$a}} keys %lib_agg) {
	$lib_percentage = $lib_agg{$item}/$total_lib_percentage*100;
	printf "%10d | %3d | %s\n", ($lib_agg{$item}, $lib_percentage, $item);
}

exit;

sub signal_handler {
    $stop_flag = 1;
}
~~~

The usage of this command is:

	$ perl poor_man_profiler.pl process_name
	
The example output is:

~~~
$ sudo perl poor_man_profiler.pl top
START profiling....press [Ctrl-C] to stop
^Cprofiling STOP!!!
==
   samples |  %  | stack path
        13 | 100 | __kernel_vsyscall, select(libc.so.6), ??, __libc_start_main(libc.so.6), ??
==
   samples |  %  | model name
        14 | 100 | libc.so.6
~~~

> I use `sudo` to run my program because this program is not belong to me.