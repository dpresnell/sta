sta
==

Simple statistics from the command line interface (CLI), fast.

### Description

This tool is a lightweight, basic, fast tool for calculating basic descriptive stastics from the command line. Inspired by https://github.com/nferraz/st, this project differs in that it is written in c++, allowing for the fast computation of statistics given large data sets. It works with stdin, so can be used downline of other programs. 

### Installing st

### Usage
    cat file | sta [options]

#### Using sta

Imagine you have this sample file:

    $ cat numbers.txt
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10

To run sta is simple: 

	$ cat numbers.txt | sta
	N	max	min	sum	mean	sd	
	0	10	1	55	5.5	2.87228	 

To extract individual bits of information:

	$ cat numbers.txt | sta --sum --sd --var
	sum	sd	var	
	55	2.87228	8.25

sta runs in sample mode by default (meaning we normalise with N). If you want to output the population variance/standard deviation, just add the flag --population

	$ cat numbers.txt | sta --sum --sd --var --population
	sum	sd	var	
	55	3.02765	9.16667	

Worried about precision? You can calculate variance instead using the  compsensated variant algorithm (http://en.wikipedia.org/wiki/Algorithms_for_calculating_variance#Compensated_variant): 

	$ cat numbers.txt | sta --var --population --compensated

### Formating

sta works with long doubles, and can process numbers in the following formats:
	
	4.7858757E-39
	4.7858757e-39
	4.7858757

### Options

	--sum
	--mean
	--min
	--max
	--sd
	--sderr
	--population
	--compensated

### ToDo

	--Add online varient
	--Prettify code

### Contributing

I've not written c++ in a long time, so please do send comments, suggestions and bug reports to:

https://github.com/simonccarter/sta/issues

Or fork the code on github:

https://github.com/simonccarter/sta
