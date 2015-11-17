# nginx
A repository of configuration files for testing nginx at 500k requests per second

nginx.conf is tuned specifically to be used with a C4.8XLarge AWS Ubuntu Image. You should see 25-30K per machine in proxy mode with zero errors with this config.

In the config files there are several limits which are maximum of 2^20 (1048576) which will crash SYSCTL if you try and increase them. Others are USHORT integers in the kernel so can hold a maximum of 65536, a lot of the guides you will find on the internet will increase figures tied to these numbers into the hundreds of thousands, but they actually get limited by the kernel to 65535 starting at 0. There are no errors for these configurations, but you can check the trimming behaviour at run time.
