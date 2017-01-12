---
title: Openblas
date: 2016-12-30 09:36:50
tags:
	- D05
	- CentOS
categories:
	- Estuary
	- Documents
---
- **Source code:**
  ```bash
  git clone https://github.com/xianyi/OpenBLAS.git
  git reset --hard d4da3fb
  ```
- **Build:**
  ```bash
  cd OpenBLAS
  make TARGET=ARMV8 BINARY=64
  cd benchmark
  make TARGET=ARMV8 BINARY=64

  ```
- **Test:**
  ```bash
  cd OpenBLAS
  cd benchmark
  export OPENBLAS_NUM_THREADS=1
  taskset -c 0 ./sgemm.goto 200 4000 200
  export OPENBLAS_NUM_THREADS=10
  taskset -c 0-9 ./sgemm.goto 200 4000 200
  export OPENBLAS_NUM_THREADS=32
  taskset -c 0-31 ./sgemm.goto 200 4000 200
  export OPENBLAS_NUM_THREADS=64
  taskset -c 0-63 ./sgemm.goto 200 4000 200

  ```
- **Result:**
  ```bash
[root@CentOS benchmark]# export OPENBLAS_NUM_THREADS=1
[root@CentOS benchmark]# taskset -c 0 ./sgemm.goto 200 4000 200
From : 200  To : 4000 Step=200 : Trans=N
   SIZE          Flops          Time
    200x200 :    13050.57 MFlops   0.001226 sec
    400x400 :    15250.80 MFlops   0.008393 sec
    600x600 :    15842.75 MFlops   0.027268 sec
    800x800 :    16012.26 MFlops   0.063951 sec
   1000x1000 :    16043.64 MFlops   0.124660 sec
   1200x1200 :    16204.81 MFlops   0.213270 sec
   1400x1400 :    16164.00 MFlops   0.339520 sec
   1600x1600 :    16208.01 MFlops   0.505429 sec
   1800x1800 :    15983.32 MFlops   0.729761 sec
   2000x2000 :    15934.35 MFlops   1.004120 sec
   2200x2200 :    15797.80 MFlops   1.348036 sec
   2400x2400 :    15938.38 MFlops   1.734681 sec
   2600x2600 :    15938.08 MFlops   2.205535 sec
   2800x2800 :    15888.81 MFlops   2.763202 sec
   3000x3000 :    15864.48 MFlops   3.403830 sec
   3200x3200 :    16002.03 MFlops   4.095480 sec
   3400x3400 :    15734.69 MFlops   4.995840 sec
   3600x3600 :    15941.05 MFlops   5.853568 sec
   3800x3800 :    15974.95 MFlops   6.869756 sec
   4000x4000 :    15964.01 MFlops   8.018037 sec
[root@CentOS benchmark]# export OPENBLAS_NUM_THREADS=10
[root@CentOS benchmark]# taskset -c 0-9 ./sgemm.goto 200 4000 200
From : 200  To : 4000 Step=200 : Trans=N
   SIZE          Flops          Time
    200x200 :    55172.41 MFlops   0.000290 sec
    400x400 :   126357.35 MFlops   0.001013 sec
    600x600 :   116066.63 MFlops   0.003722 sec
    800x800 :   118477.38 MFlops   0.008643 sec
   1000x1000 :   120489.19 MFlops   0.016599 sec
   1200x1200 :   125385.48 MFlops   0.027563 sec
   1400x1400 :   120006.12 MFlops   0.045731 sec
   1600x1600 :   122370.94 MFlops   0.066944 sec
   1800x1800 :   122201.39 MFlops   0.095449 sec
   2000x2000 :   125269.13 MFlops   0.127725 sec
   2200x2200 :   123197.96 MFlops   0.172860 sec
   2400x2400 :   125177.14 MFlops   0.220871 sec
   2600x2600 :   123513.70 MFlops   0.284600 sec
   2800x2800 :   124502.32 MFlops   0.352636 sec
   3000x3000 :   124612.89 MFlops   0.433342 sec
   3200x3200 :   125271.19 MFlops   0.523153 sec
   3400x3400 :   124629.80 MFlops   0.630732 sec
   3600x3600 :   127306.71 MFlops   0.732970 sec
   3800x3800 :   126268.36 MFlops   0.869133 sec
   4000x4000 :   124512.17 MFlops   1.028012 sec
[root@CentOS benchmark]# export OPENBLAS_NUM_THREADS=32
[root@CentOS benchmark]# taskset -c 0-31 ./sgemm.goto 200 4000 200
From : 200  To : 4000 Step=200 : Trans=N
   SIZE          Flops          Time
    200x200 :      416.28 MFlops   0.038436 sec
    400x400 :     1970.14 MFlops   0.064970 sec
    600x600 :     4696.72 MFlops   0.091979 sec
    800x800 :     9740.04 MFlops   0.105133 sec
   1000x1000 :    80635.41 MFlops   0.024803 sec
   1200x1200 :   355738.55 MFlops   0.009715 sec
   1400x1400 :   352133.46 MFlops   0.015585 sec
   1600x1600 :   337925.91 MFlops   0.024242 sec
   1800x1800 :   356686.34 MFlops   0.032701 sec
   2000x2000 :   346530.36 MFlops   0.046172 sec
   2200x2200 :   350886.44 MFlops   0.060692 sec
   2400x2400 :   355441.28 MFlops   0.077785 sec
   2600x2600 :   367602.61 MFlops   0.095625 sec
   2800x2800 :   369686.76 MFlops   0.118760 sec
   3000x3000 :   359068.81 MFlops   0.150389 sec
   3200x3200 :   378820.81 MFlops   0.173000 sec
   3400x3400 :   367639.77 MFlops   0.213818 sec
   3600x3600 :   386994.03 MFlops   0.241120 sec
   3800x3800 :   378948.97 MFlops   0.289601 sec
   4000x4000 :   375380.88 MFlops   0.340987 sec
[root@CentOS benchmark]# export OPENBLAS_NUM_THREADS=64
[root@CentOS benchmark]# taskset -c 0-63 ./sgemm.goto 200 4000 200
From : 200  To : 4000 Step=200 : Trans=N
   SIZE          Flops          Time
    200x200 :       58.45 MFlops   0.273748 sec
    400x400 :    70368.33 MFlops   0.001819 sec
    600x600 :   155283.97 MFlops   0.002782 sec
    800x800 :   237476.81 MFlops   0.004312 sec
   1000x1000 :   351185.25 MFlops   0.005695 sec
   1200x1200 :   374674.76 MFlops   0.009224 sec
   1400x1400 :   443869.30 MFlops   0.012364 sec
   1600x1600 :   477834.81 MFlops   0.017144 sec
   1800x1800 :   523659.87 MFlops   0.022274 sec
   2000x2000 :   588841.45 MFlops   0.027172 sec
   2200x2200 :   581159.26 MFlops   0.036644 sec
   2400x2400 :   561095.89 MFlops   0.049275 sec
   2600x2600 :   580449.14 MFlops   0.060560 sec
   2800x2800 :   601218.76 MFlops   0.073025 sec
   3000x3000 :   558595.65 MFlops   0.096671 sec
   3200x3200 :   583418.65 MFlops   0.112331 sec
   3400x3400 :   565460.09 MFlops   0.139016 sec
   3600x3600 :   593191.57 MFlops   0.157305 sec
   3800x3800 :   582796.09 MFlops   0.188306 sec
   4000x4000 :   566542.15 MFlops   0.225932 sec
  ```
