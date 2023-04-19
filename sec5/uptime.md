## uptime: How busy is the system

The `uptime` command shows the current time, how long the system has been up, and the load average. The **load average** reflects the number of jobs waiting to be run. It describes how "busy" the system is. As an example: 

```bash
uptime
```
will have results similar to this:

```bash
17:46:20 up 11 days, 10:08,  1 user,  load average: 0.37, 0.21, 0.25
```
These metrics alone are meaningless and are more useful when looked at as a time series as opposed to a snapshot. On the VM where I ran this this could be problematic if it remained like this but on more powerful machine perhaps not. This depends on the hardware and CPU of the system.