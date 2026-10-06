# OSTEP Ch.4 Homework Answers
## Q1
- Prediction / 预测:the state table is below.
```
Time        PID: 0        PID: 1           CPU           IOs
  1        RUNNING         READY             1          
  2        RUNNING         READY             1          
  3        RUNNING         READY             1          
  4        RUNNING         READY             1          
  5        RUNNING         READY             1          
  6           DONE       RUNNING             1          
  7           DONE       RUNNING             1          
  8           DONE       RUNNING             1          
  9           DONE       RUNNING             1          
 10           DONE       RUNNING             1          
```
total time:10
CPU utilization:100%
- Reasoning / 理由:两个进程都只用cpu时，cpu不会空闲。
- Verified result / 验证结果:
- Analysis / 分析:
## Q2
- Prediction / 预测:the state table is below.
```
Time        PID: 0        PID: 1           CPU           IOs
  1        RUNNING         READY             1          
  2        RUNNING         READY             1          
  3        RUNNING         READY             1          
  4        RUNNING         READY             1          
  5           DONE        RUN:io             1          
  6           DONE       BLOCKED                           1
  7           DONE       BLOCKED                           1
  8           DONE       BLOCKED                           1
  9           DONE       BLOCKED                           1
 10           DONE       BLOCKED                           1
 11           DONE   RUN:io_done             1          
```
total time:11
CPU utilization:6/11
- Reasoning / 理由:pid0结束前pid1在等待。一次IO需要7个tick
- Verified result / 验证结果:
- Analysis / 分析:
## Q3
- Prediction / 预测:the state table is below.
```
Time        PID: 0        PID: 1           CPU           IOs
  1         RUN:io         READY             1          
  2        BLOCKED       RUNNING             1             1
  3        BLOCKED       RUNNING             1             1
  4        BLOCKED       RUNNING             1             1
  5        BLOCKED       RUNNING             1             1
  6        BLOCKED          DONE                           1
  7    RUN:io_done          DONE             1          
```
total time:7
CPU utilization:6/7
- Reasoning / 理由:IO阻塞时cpu在运行其他进程
- Verified result / 验证结果:
- Analysis / 分析:
## Q4
- Prediction / 预测:the state table is below.
```
Time        PID: 0        PID: 1           CPU           IOs
  1         RUN:io         READY             1          
  2        BLOCKED         READY                           1
  3        BLOCKED         READY                           1
  4        BLOCKED         READY                           1
  5        BLOCKED         READY                           1
  6        BLOCKED         READY                           1
  7    RUN:io_done         READY             1          
  8           DONE       RUNNING             1          
  9           DONE       RUNNING             1          
 10           DONE       RUNNING             1          
 11           DONE       RUNNING             1             
```
total time:11
CPU utilization:6/11
- Reasoning / 理由:如果等待时不切换，CPU会等待IO结束后再运行其他进程
- Verified result / 验证结果:
- Analysis / 分析:
## Q5
- Prediction / 预测:the state table is below.
```
Time        PID: 0        PID: 1           CPU           IOs
  1         RUN:io         READY             1          
  2        BLOCKED       RUNNING             1             1
  3        BLOCKED       RUNNING             1             1
  4        BLOCKED       RUNNING             1             1
  5        BLOCKED       RUNNING             1             1
  6        BLOCKED          DONE                           1
  7    RUN:io_done          DONE             1              
```
total time:7
CPU utilization:6/7
- Reasoning / 理由:等待时切换，因此IO传输时CPU会处理其他进程，时间缩短
- Verified result / 验证结果:
- Analysis / 分析:
## Q6
- Prediction / 预测:the state table is below.
```
Time        PID: 0        PID: 1        PID: 2        PID: 3           CPU           IOs
  1         RUN:io         READY         READY         READY             1          
  2        BLOCKED       RUNNING         READY         READY             1             1
  3        BLOCKED       RUNNING         READY         READY             1             1
  4        BLOCKED       RUNNING         READY         READY             1             1
  5        BLOCKED       RUNNING         READY         READY             1             1
  6        BLOCKED       RUNNING         READY         READY             1             1
  7          READY          DONE       RUNNING         READY             1          
  8          READY          DONE       RUNNING         READY             1          
  9          READY          DONE       RUNNING         READY             1          
 10          READY          DONE       RUNNING         READY             1          
 11          READY          DONE       RUNNING         READY             1          
 12          READY          DONE          DONE       RUNNING             1          
 13          READY          DONE          DONE       RUNNING             1          
 14          READY          DONE          DONE       RUNNING             1          
 15          READY          DONE          DONE       RUNNING             1          
 16          READY          DONE          DONE       RUNNING             1          
 17    RUN:io_done          DONE          DONE          DONE             1          
 18         RUN:io          DONE          DONE          DONE             1          
 19        BLOCKED          DONE          DONE          DONE                           1
 20        BLOCKED          DONE          DONE          DONE                           1
 21        BLOCKED          DONE          DONE          DONE                           1
 22        BLOCKED          DONE          DONE          DONE                           1
 23        BLOCKED          DONE          DONE          DONE                           1
 24    RUN:io_done          DONE          DONE          DONE             1          
 25         RUN:io          DONE          DONE          DONE             1          
 26        BLOCKED          DONE          DONE          DONE                           1
 27        BLOCKED          DONE          DONE          DONE                           1
 28        BLOCKED          DONE          DONE          DONE                           1
 29        BLOCKED          DONE          DONE          DONE                           1
 30        BLOCKED          DONE          DONE          DONE                           1
 31    RUN:io_done          DONE          DONE          DONE             1            
```
total time:31
CPU utilization:21/31
- Reasoning / 理由:IO传输结束后始终处于READY状态，等待其他进程结束CPU空闲时继续。
- Verified result / 验证结果:
- Analysis / 分析:
## Q7
- Prediction / 预测:the state table is below.
```
Time        PID: 0        PID: 1        PID: 2        PID: 3           CPU           IOs
  1         RUN:io         READY         READY         READY             1          
  2        BLOCKED       RUNNING         READY         READY             1             1
  3        BLOCKED       RUNNING         READY         READY             1             1
  4        BLOCKED       RUNNING         READY         READY             1             1
  5        BLOCKED       RUNNING         READY         READY             1             1
  6        BLOCKED       RUNNING         READY         READY             1             1
  7    RUN:io_done          DONE         READY         READY             1          
  8         RUN:io          DONE         READY         READY             1          
  9        BLOCKED          DONE       RUNNING         READY             1             1
 10        BLOCKED          DONE       RUNNING         READY             1             1
 11        BLOCKED          DONE       RUNNING         READY             1             1
 12        BLOCKED          DONE       RUNNING         READY             1             1
 13        BLOCKED          DONE       RUNNING         READY             1             1
 14    RUN:io_done          DONE          DONE         READY             1          
 15         RUN:io          DONE          DONE         READY             1          
 16        BLOCKED          DONE          DONE       RUNNING             1             1
 17        BLOCKED          DONE          DONE       RUNNING             1             1
 18        BLOCKED          DONE          DONE       RUNNING             1             1
 19        BLOCKED          DONE          DONE       RUNNING             1             1
 20        BLOCKED          DONE          DONE       RUNNING             1             1
 21    RUN:io_done          DONE          DONE          DONE             1          
```
total time:21
CPU utilization:100%
- Reasoning / 理由:IO传输完立刻抢回CPU，减少IO进程的等待时间，提升传输速度。
- Verified result / 验证结果:
- Analysis / 分析:
## Q8
- Prediction / 预测:the state table is below.(s1)
```
Time        PID: 0        PID: 1           CPU           IOs
  1         RUN:io         READY             1          
  2        BLOCKED       RUNNING             1             1
  3        BLOCKED        RUN:io             1             1
  4        BLOCKED       BLOCKED                           2
  5        BLOCKED       BLOCKED                           2
  6        BLOCKED       BLOCKED                           2
  7    RUN:io_done       BLOCKED             1             1
  8         RUN:io       BLOCKED             1             1
  9        BLOCKED   RUN:io_done             1             1
 10        BLOCKED        RUN:io             1             1
 11        BLOCKED       BLOCKED                           2
 12        BLOCKED       BLOCKED                           2
 13        BLOCKED       BLOCKED                           2
 14    RUN:io_done       BLOCKED             1             1
 15        RUNNING       BLOCKED             1             1
 16           DONE   RUN:io_done             1            
```
total time:16
CPU utilization:10/16
the state table is below.(s2)
```
Time        PID: 0        PID: 1           CPU           IOs
  1         RUN:io         READY             1          
  2        BLOCKED       RUNNING             1             1
  3        BLOCKED        RUN:io             1             1
  4        BLOCKED       BLOCKED                           2
  5        BLOCKED       BLOCKED                           2
  6        BLOCKED       BLOCKED                           2
  7    RUN:io_done       BLOCKED             1             1
  8         RUN:io       BLOCKED             1             1
  9        BLOCKED   RUN:io_done             1             1
 10        BLOCKED        RUN:io             1             1
 11        BLOCKED       BLOCKED                           2
 12        BLOCKED       BLOCKED                           2
 13        BLOCKED       BLOCKED                           2
 14    RUN:io_done       BLOCKED             1             1
 15        RUNNING       BLOCKED             1             1
 16           DONE   RUN:io_done             1          
```
total time:16
CPU utilization:10/16
the state table is below.(s3)
```
Time        PID: 0        PID: 1           CPU           IOs
  1        RUNNING         READY             1          
  2         RUN:io         READY             1          
  3        BLOCKED        RUN:io             1             1
  4        BLOCKED       BLOCKED                           2
  5        BLOCKED       BLOCKED                           2
  6        BLOCKED       BLOCKED                           2
  7        BLOCKED       BLOCKED                           2
  8    RUN:io_done       BLOCKED             1             1
  9        RUNNING         READY             1          
 10           DONE   RUN:io_done             1          
 11           DONE        RUN:io             1          
 12           DONE       BLOCKED                           1
 13           DONE       BLOCKED                           1
 14           DONE       BLOCKED                           1
 15           DONE       BLOCKED                           1
 16           DONE       BLOCKED                           1
 17           DONE   RUN:io_done             1          
 18           DONE       RUNNING             1          
```
total time:18
CPU utilization:50%
- Reasoning / 理由:根据控制台实际输出的IO和CPU指令顺序进行了预测。
- Verified result / 验证结果:
- Analysis / 分析: