# bkunifylogbeat

## Test environment

1. Linux VM_1_177_centos 4.14.105-1-tlinux3-0011
2. CPU: 32 cores, Intel(R) Xeon(R) CPU E5-26xx v4
3. Mem：64G

## Collection performance

| Single log size (KB) | Log collection speed (MB/s) | CPU single core usage (%) | Memory usage (MB) |
| :---------------: | :------------------: | :--------------: | :----------------: |
| 0.1 | 7.42 | 83.5 | 143.69 |
| 0.2 | 13.41 | 83.2 | 153.09 |
| 1 | 44.22 | 80.2 | 344.34 |