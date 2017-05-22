---
title: Stream
date: 2016-12-27 17:30:31
tags:
  - D05
  - CentOS
categories:
  - Estuary
  - Documents
---

- **Denpendency:**
  ```bash
  yum install numactl
  ```

- **Source code:**
- **Source code:**
  *Openlab:192.168.1.101:/home/chenzhihui/Ali-test/lmbench-3.0-a9/*
- **Build:**
  ```bash
  cd lmbench-3.0-a9
  sed -i 's/--static//' src/Makefile # 去掉src/Makefile里面的--static
  sed -i 's/-O/-O2/g' src/Makefile # 使用 O2 级别优化
  make OS=lmbench
  numactl -H  # 查看node信息,然后修改下面对应参数
  ```
- **Test:**
  ```bash
  cd ./bin/lmbench/
  for((i=0;i<10;i++));do
	  numactl --cpunodebind=0,1,2,3 --localalloc ./stream -v 1 -M 200M -P 64
	  numactl --cpunodebind=0,1,2,3 --localalloc ./stream -v 2 -M 200M -P 64
  done
  ```
- **Result:**
  ```bash
  STREAM copy latency: 11.02 nanoseconds
  STREAM copy bandwidth: 92887.14 MB/sec
  STREAM scale latency: 10.91 nanoseconds
  STREAM scale bandwidth: 93895.07 MB/sec
  STREAM add latency: 19.55 nanoseconds
  STREAM add bandwidth: 78581.77 MB/sec
  STREAM triad latency: 17.78 nanoseconds
  STREAM triad bandwidth: 86376.82 MB/sec
  STREAM2 fill latency: 5.50 nanoseconds
  STREAM2 fill bandwidth: 93006.92 MB/sec
  STREAM2 copy latency: 11.96 nanoseconds
  STREAM2 copy bandwidth: 85626.90 MB/sec
  STREAM2 daxpy latency: 16.81 nanoseconds
  STREAM2 daxpy bandwidth: 91353.52 MB/sec
  STREAM2 sum latency: 5.64 nanoseconds
  STREAM2 sum bandwidth: 90723.52 MB/sec
  STREAM copy latency: 11.36 nanoseconds
  STREAM copy bandwidth: 90103.92 MB/sec
  STREAM scale latency: 11.99 nanoseconds
  STREAM scale bandwidth: 85420.32 MB/sec
  STREAM add latency: 17.92 nanoseconds
  STREAM add bandwidth: 85696.45 MB/sec
  STREAM triad latency: 17.07 nanoseconds
  STREAM triad bandwidth: 89992.01 MB/sec
  STREAM2 fill latency: 5.19 nanoseconds
  STREAM2 fill bandwidth: 98571.02 MB/sec
  STREAM2 copy latency: 11.49 nanoseconds
  STREAM2 copy bandwidth: 89100.74 MB/sec
  STREAM2 daxpy latency: 17.54 nanoseconds
  STREAM2 daxpy bandwidth: 87568.84 MB/sec
  STREAM2 sum latency: 5.72 nanoseconds
  STREAM2 sum bandwidth: 89579.78 MB/sec
  STREAM copy latency: 11.00 nanoseconds
  STREAM copy bandwidth: 93126.35 MB/sec
  STREAM scale latency: 11.11 nanoseconds
  STREAM scale bandwidth: 92144.49 MB/sec
  STREAM add latency: 16.89 nanoseconds
  STREAM add bandwidth: 90959.14 MB/sec
  STREAM triad latency: 16.71 nanoseconds
  STREAM triad bandwidth: 91928.34 MB/sec
  STREAM2 fill latency: 5.16 nanoseconds
  STREAM2 fill bandwidth: 99283.67 MB/sec
  STREAM2 copy latency: 11.12 nanoseconds
  STREAM2 copy bandwidth: 92066.56 MB/sec
  STREAM2 daxpy latency: 16.17 nanoseconds
  STREAM2 daxpy bandwidth: 95005.80 MB/sec
  STREAM2 sum latency: 5.65 nanoseconds
  STREAM2 sum bandwidth: 90652.56 MB/sec
  STREAM copy latency: 11.09 nanoseconds
  STREAM copy bandwidth: 92372.01 MB/sec
  STREAM scale latency: 11.01 nanoseconds
  STREAM scale bandwidth: 92994.33 MB/sec
  STREAM add latency: 16.76 nanoseconds
  STREAM add bandwidth: 91662.48 MB/sec
  STREAM triad latency: 16.67 nanoseconds
  STREAM triad bandwidth: 92133.35 MB/sec
  STREAM2 fill latency: 5.33 nanoseconds
  STREAM2 fill bandwidth: 96002.96 MB/sec
  STREAM2 copy latency: 11.05 nanoseconds
  STREAM2 copy bandwidth: 92641.23 MB/sec
  STREAM2 daxpy latency: 16.56 nanoseconds
  STREAM2 daxpy bandwidth: 92753.55 MB/sec
  STREAM2 sum latency: 5.26 nanoseconds
  STREAM2 sum bandwidth: 97369.11 MB/sec
  STREAM copy latency: 10.97 nanoseconds
  STREAM copy bandwidth: 93310.84 MB/sec
  STREAM scale latency: 11.14 nanoseconds
  STREAM scale bandwidth: 91948.55 MB/sec
  STREAM add latency: 17.00 nanoseconds
  STREAM add bandwidth: 90338.64 MB/sec
  STREAM triad latency: 17.78 nanoseconds
  STREAM triad bandwidth: 86365.35 MB/sec
  STREAM2 fill latency: 5.40 nanoseconds
  STREAM2 fill bandwidth: 94829.88 MB/sec
  STREAM2 copy latency: 11.12 nanoseconds
  STREAM2 copy bandwidth: 92102.40 MB/sec
  STREAM2 daxpy latency: 17.24 nanoseconds
  STREAM2 daxpy bandwidth: 89112.14 MB/sec
  STREAM2 sum latency: 5.33 nanoseconds
  STREAM2 sum bandwidth: 95998.75 MB/sec
  STREAM copy latency: 11.54 nanoseconds
  STREAM copy bandwidth: 88709.78 MB/sec
  STREAM scale latency: 12.01 nanoseconds
  STREAM scale bandwidth: 85248.54 MB/sec
  STREAM add latency: 18.01 nanoseconds
  STREAM add bandwidth: 85300.02 MB/sec
  STREAM triad latency: 16.59 nanoseconds
  STREAM triad bandwidth: 92608.47 MB/sec
  STREAM2 fill latency: 5.57 nanoseconds
  STREAM2 fill bandwidth: 91893.86 MB/sec
  STREAM2 copy latency: 11.30 nanoseconds
  STREAM2 copy bandwidth: 90605.30 MB/sec
  STREAM2 daxpy latency: 17.84 nanoseconds
  STREAM2 daxpy bandwidth: 86102.14 MB/sec
  STREAM2 sum latency: 5.36 nanoseconds
  STREAM2 sum bandwidth: 95490.63 MB/sec
  STREAM copy latency: 11.05 nanoseconds
  STREAM copy bandwidth: 92702.74 MB/sec
  STREAM scale latency: 11.41 nanoseconds
  STREAM scale bandwidth: 89771.22 MB/sec
  STREAM add latency: 16.51 nanoseconds
  STREAM add bandwidth: 93035.91 MB/sec
  STREAM triad latency: 16.68 nanoseconds
  STREAM triad bandwidth: 92108.20 MB/sec
  STREAM2 fill latency: 5.51 nanoseconds
  STREAM2 fill bandwidth: 92857.87 MB/sec
  STREAM2 copy latency: 12.41 nanoseconds
  STREAM2 copy bandwidth: 82539.81 MB/sec
  STREAM2 daxpy latency: 16.60 nanoseconds
  STREAM2 daxpy bandwidth: 92529.92 MB/sec
  STREAM2 sum latency: 5.66 nanoseconds
  STREAM2 sum bandwidth: 90535.45 MB/sec
  STREAM copy latency: 11.05 nanoseconds
  STREAM copy bandwidth: 92661.04 MB/sec
  STREAM scale latency: 11.16 nanoseconds
  STREAM scale bandwidth: 91785.73 MB/sec
  STREAM add latency: 17.22 nanoseconds
  STREAM add bandwidth: 89172.75 MB/sec
  STREAM triad latency: 17.37 nanoseconds
  STREAM triad bandwidth: 88431.40 MB/sec
  STREAM2 fill latency: 5.80 nanoseconds
  STREAM2 fill bandwidth: 88271.38 MB/sec
  STREAM2 copy latency: 11.01 nanoseconds
  STREAM2 copy bandwidth: 93000.74 MB/sec
  STREAM2 daxpy latency: 17.25 nanoseconds
  STREAM2 daxpy bandwidth: 89033.97 MB/sec
  STREAM2 sum latency: 5.74 nanoseconds
  STREAM2 sum bandwidth: 89146.25 MB/sec
  STREAM copy latency: 11.86 nanoseconds
  STREAM copy bandwidth: 86317.33 MB/sec
  STREAM scale latency: 11.84 nanoseconds
  STREAM scale bandwidth: 86488.11 MB/sec
  STREAM add latency: 17.58 nanoseconds
  STREAM add bandwidth: 87382.70 MB/sec
  STREAM triad latency: 16.60 nanoseconds
  STREAM triad bandwidth: 92543.11 MB/sec
  STREAM2 fill latency: 5.54 nanoseconds
  STREAM2 fill bandwidth: 92387.31 MB/sec
  STREAM2 copy latency: 12.19 nanoseconds
  STREAM2 copy bandwidth: 84031.60 MB/sec
  STREAM2 daxpy latency: 16.38 nanoseconds
  STREAM2 daxpy bandwidth: 93746.68 MB/sec
  STREAM2 sum latency: 5.30 nanoseconds
  STREAM2 sum bandwidth: 96674.95 MB/sec
  STREAM copy latency: 11.27 nanoseconds
  STREAM copy bandwidth: 90890.54 MB/sec
  STREAM scale latency: 13.07 nanoseconds
  STREAM scale bandwidth: 78364.68 MB/sec
  STREAM add latency: 16.65 nanoseconds
  STREAM add bandwidth: 92249.23 MB/sec
  STREAM triad latency: 17.79 nanoseconds
  STREAM triad bandwidth: 86326.67 MB/sec
  STREAM2 fill latency: 5.11 nanoseconds
  STREAM2 fill bandwidth: 100242.17 MB/sec
  STREAM2 copy latency: 12.13 nanoseconds
  STREAM2 copy bandwidth: 84419.38 MB/sec
  STREAM2 daxpy latency: 17.03 nanoseconds
  STREAM2 daxpy bandwidth: 90219.87 MB/sec
  STREAM2 sum latency: 5.92 nanoseconds
  STREAM2 sum bandwidth: 86414.64 MB/sec

  ```
