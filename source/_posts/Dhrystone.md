---
title: Dhrystone
date: 2016-12-29 14:40:01
tags:
	- D05
	- CentOS
categories:
	- Estuary
	- Documents
---
- **Source code:**
  *Openlab:192.168.1.101:/home/chenzhihui/All-test/dhrystone/dhrystone-2.1*

- **Build:**
  ```bash
  cd dhrystone-2.1
  make unix
  ```
- **Test:**
  ```bash
  cd dhrystone-2.1
  taskset -c 0 ./gcc_dry2<<EOF
  1000000000
  EOF
  ```
- **Result:**
  ```bash
[root@CentOS dhrystone-2.1]# taskset -c 0 ./gcc_dry2<<EOF
> 1000000000
> EOF

Dhrystone Benchmark, Version 2.1 (Language: C)

Program compiled without 'register' attribute

Please give the number of runs through the benchmark: 
Execution starts, 1000000000 runs through Dhrystone
Execution ends

Final values of the variables used in the benchmark:

Int_Glob:            5
        should be:   5
Bool_Glob:           1
        should be:   1
Ch_1_Glob:           A
        should be:   A
Ch_2_Glob:           B
        should be:   B
Arr_1_Glob[8]:       7
        should be:   7
Arr_2_Glob[8][7]:    1000000010
        should be:   Number_Of_Runs + 10
Ptr_Glob->
  Ptr_Comp:          96206864
        should be:   (implementation-dependent)
  Discr:             0
        should be:   0
  Enum_Comp:         2
        should be:   2
  Int_Comp:          17
        should be:   17
  Str_Comp:          DHRYSTONE PROGRAM, SOME STRING
        should be:   DHRYSTONE PROGRAM, SOME STRING
Next_Ptr_Glob->
  Ptr_Comp:          96206864
        should be:   (implementation-dependent), same as above
  Discr:             0
        should be:   0
  Enum_Comp:         1
        should be:   1
  Int_Comp:          18
        should be:   18
  Str_Comp:          DHRYSTONE PROGRAM, SOME STRING
        should be:   DHRYSTONE PROGRAM, SOME STRING
Int_1_Loc:           5
        should be:   5
Int_2_Loc:           13
        should be:   13
Int_3_Loc:           7
        should be:   7
Enum_Loc:            1
        should be:   1
Str_1_Loc:           DHRYSTONE PROGRAM, 1'ST STRING
        should be:   DHRYSTONE PROGRAM, 1'ST STRING
Str_2_Loc:           DHRYSTONE PROGRAM, 2'ND STRING
        should be:   DHRYSTONE PROGRAM, 2'ND STRING

Microseconds for one run through Dhrystone:    0.2 
Dhrystones per Second:                      6423983.0
  ```