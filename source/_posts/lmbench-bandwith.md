---
title: lmbench_bandwith
date: 2016-12-28 15:48:17
tags:
	- D05
	- CentOS
categories:
 	- Estuary
	- Documents
---

- **Dependency:**
  ```bash
  yum install numactl
  ```

- **Source code:**
  *Openlab:192.168.1.101:/home/chenzhihui/Ali-test/lmbench-3.0-a9*

- **Build:**
  ```bash
  cd lmbench-3.0-a9
  sed -i 's/--static//' src/Makefile
  sed -i 's/-O/-O2/g' src/Makefile
  make OS=lmbench
  ```
- **Test**
  Local memory access:
  ```bash
taskset -c 0 ./bw_mem -P 1 -N 5 32M rd
taskset -c 0 ./bw_mem -P 1 -N 5 32M frd
taskset -c 0 ./bw_mem -P 1 -N 5 32M wr
taskset -c 0 ./bw_mem -P 1 -N 5 32M fwr
taskset -c 0 ./bw_mem -P 1 -N 5 32M bzero
taskset -c 0 ./bw_mem -P 1 -N 5 32M rdwr
taskset -c 0 ./bw_mem -P 1 -N 5 32M cp
taskset -c 0 ./bw_mem -P 1 -N 5 32M fcp
taskset -c 0 ./bw_mem -P 1 -N 5 32M bcopy

taskset -c 0-3 ./bw_mem -P 4 -N 5 32M rd
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M frd
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M wr
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M fwr
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M bzero
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M rdwr
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M cp
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M fcp
taskset -c 0-3 ./bw_mem -P 4 -N 5 32M bcopy

taskset -c 0-15 ./bw_mem -P 16 -N 5 32M rd
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M frd
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M wr
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M fwr
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M bzero
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M rdwr
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M cp
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M fcp
taskset -c 0-15 ./bw_mem -P 16 -N 5 32M bcopy

taskset -c 0-31 ./bw_mem -P 32 -N 5 32M rd
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M frd
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M wr
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M fwr
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M bzero
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M rdwr
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M cp
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M fcp
taskset -c 0-31 ./bw_mem -P 32 -N 5 32M bcopy

numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
  ```
  <!--more-->
  Result:
  ```bash
[root@CentOS lmbench]# taskset -c 0 ./bw_mem -P 1 -N 5 32M rd
32.00 8395.64
[root@CentOS lmbench]# taskset -c 0 ./bw_mem -P 1 -N 5 32M frd
32.00 6948.21
[root@CentOS lmbench]# taskset -c 0 ./bw_mem -P 1 -N 5 32M wr
32.00 6380.86
[root@CentOS lmbench]# taskset -c 0 ./bw_mem -P 1 -N 5 32M fwr
32.00 8917.37
[root@CentOS lmbench]# taskset -c 0 ./bw_mem -P 1 -N 5 32M bzero
32.00 8916.13
[root@CentOS lmbench]# taskset -c 0 ./bw_mem -P 1 -N 5 32M rdwr
32.00 5416.38
[root@CentOS lmbench]# taskset -c 0 ./bw_mem -P 1 -N 5 32M cp
32.00 4793.29
[root@CentOS lmbench]# taskset -c 0 ./bw_mem -P 1 -N 5 32M fcp
32.00 6465.95
[root@CentOS lmbench]# taskset -c 0 ./bw_mem -P 1 -N 5 32M bcopy
32.00 6384.68
[root@CentOS lmbench]# taskset -c 0-3 ./bw_mem -P 4 -N 5 32M rd
32.00 12948.02
[root@CentOS lmbench]# taskset -c 0-3 ./bw_mem -P 4 -N 5 32M frd
32.00 12115.30
[root@CentOS lmbench]# taskset -c 0-3 ./bw_mem -P 4 -N 5 32M wr
32.00 11049.81
[root@CentOS lmbench]# taskset -c 0-3 ./bw_mem -P 4 -N 5 32M fwr
32.00 19268.99
[root@CentOS lmbench]# taskset -c 0-3 ./bw_mem -P 4 -N 5 32M bzero
32.00 19272.67
[root@CentOS lmbench]# taskset -c 0-3 ./bw_mem -P 4 -N 5 32M rdwr
32.00 6645.70
[root@CentOS lmbench]# taskset -c 0-3 ./bw_mem -P 4 -N 5 32M cp
32.00 6186.32
[root@CentOS lmbench]# taskset -c 0-3 ./bw_mem -P 4 -N 5 32M fcp
32.00 9166.27
[root@CentOS lmbench]# taskset -c 0-3 ./bw_mem -P 4 -N 5 32M bcopy
32.00 5689.13
[root@CentOS lmbench]# taskset -c 0-15 ./bw_mem -P 16 -N 5 32M rd
32.00 25158.52
[root@CentOS lmbench]# taskset -c 0-15 ./bw_mem -P 16 -N 5 32M frd
32.00 26114.56
[root@CentOS lmbench]# taskset -c 0-15 ./bw_mem -P 16 -N 5 32M wr
32.00 12522.02
[root@CentOS lmbench]# taskset -c 0-15 ./bw_mem -P 16 -N 5 32M fwr
32.00 26202.75
[root@CentOS lmbench]# taskset -c 0-15 ./bw_mem -P 16 -N 5 32M bzero
32.00 26228.31
[root@CentOS lmbench]# taskset -c 0-15 ./bw_mem -P 16 -N 5 32M rdwr
32.00 12374.53
[root@CentOS lmbench]# taskset -c 0-15 ./bw_mem -P 16 -N 5 32M cp
32.00 8183.33
[root@CentOS lmbench]# taskset -c 0-15 ./bw_mem -P 16 -N 5 32M fcp
32.00 11715.58
[root@CentOS lmbench]# taskset -c 0-15 ./bw_mem -P 16 -N 5 32M bcopy
32.00 9639.48
[root@CentOS lmbench]# 
[root@CentOS lmbench]# taskset -c 0-31 ./bw_mem -P 32 -N 5 32M rd
32.00 50322.30
[root@CentOS lmbench]# taskset -c 0-31 ./bw_mem -P 32 -N 5 32M frd
32.00 51266.66
[root@CentOS lmbench]# taskset -c 0-31 ./bw_mem -P 32 -N 5 32M wr
32.00 25096.06
[root@CentOS lmbench]# taskset -c 0-31 ./bw_mem -P 32 -N 5 32M fwr
32.00 53000.32
[root@CentOS lmbench]# taskset -c 0-31 ./bw_mem -P 32 -N 5 32M bzero
32.00 53157.12
[root@CentOS lmbench]# taskset -c 0-31 ./bw_mem -P 32 -N 5 32M rdwr
32.00 24512.41
[root@CentOS lmbench]# taskset -c 0-31 ./bw_mem -P 32 -N 5 32M cp
32.00 16165.50
[root@CentOS lmbench]# taskset -c 0-31 ./bw_mem -P 32 -N 5 32M fcp
32.00 23315.59
[root@CentOS lmbench]# taskset -c 0-31 ./bw_mem -P 32 -N 5 32M bcopy
32.00 19182.88
[root@CentOS lmbench]# 
[root@CentOS lmbench]# numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd
32.00 99172.21
[root@CentOS lmbench]# numactl -C 0-31,32-63 ./bw_mem -P 64 -N 5 32M rd

  ```
  Cross die memory access:
  ```bash
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M rd
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M frd
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M wr
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M fwr
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M bzero
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M rdwr
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M cp
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M fcp
numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M bcopy

numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M rd
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M frd
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M wr
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M fwr
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M bzero
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M rdwr
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M cp
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M fcp
numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M bcopy

numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M rd
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M frd
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M wr
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M fwr
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M bzero
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M rdwr
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M cp
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M fcp
numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M bcopy
  ```
  Result:
  ```bash
[root@CentOS lmbench]# numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M rd
32.00 7083.56
[root@CentOS lmbench]# numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M frd
32.00 5934.72
[root@CentOS lmbench]# numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M wr
32.00 6237.82
[root@CentOS lmbench]# numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M fwr
32.00 4240.10
[root@CentOS lmbench]# numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M bzero
32.00 4242.91
[root@CentOS lmbench]# numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M rdwr
32.00 4328.42
[root@CentOS lmbench]# numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M cp
32.00 4377.56
[root@CentOS lmbench]# numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M fcp
32.00 3956.48
[root@CentOS lmbench]# numactl -C 0 -m 1 ./bw_mem -P 1 -N 5 32M bcopy
32.00 3961.87
[root@CentOS lmbench]# numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M rd
32.00 9252.93
[root@CentOS lmbench]# numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M frd
32.00 9908.16
[root@CentOS lmbench]# numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M wr
32.00 10491.16
[root@CentOS lmbench]# numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M fwr
32.00 13883.77
[root@CentOS lmbench]# numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M bzero
32.00 13875.67
[root@CentOS lmbench]# numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M rdwr
32.00 6387.84
[root@CentOS lmbench]# numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M cp
32.00 4825.84
[root@CentOS lmbench]# numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M fcp
32.00 7599.01
[root@CentOS lmbench]# numactl -C 0-3 -m 1 ./bw_mem -P 4 -N 5 32M bcopy
32.00 4761.99
[root@CentOS lmbench]# 
[root@CentOS lmbench]# numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M rd
32.00 23330.67
[root@CentOS lmbench]# numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M frd
32.00 24077.52
[root@CentOS lmbench]# numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M wr
32.00 12578.12
[root@CentOS lmbench]# numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M fwr
32.00 26199.88
[root@CentOS lmbench]# numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M bzero
32.00 26142.08
[root@CentOS lmbench]# numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M rdwr
32.00 12118.53
[root@CentOS lmbench]# numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M cp
32.00 8141.88
[root@CentOS lmbench]# numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M fcp
32.00 11497.53
[root@CentOS lmbench]# numactl -C 0-15 -m 1 ./bw_mem -P 16 -N 5 32M bcopy
32.00 9424.97

  ```
