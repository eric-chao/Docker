### Configuration

* [Predixy](https://github.com/joyieldInc/predixy "predixy") Configuration
    <pre><code><font face="黑体">Please update redis-predixy-cfg.yaml for you personal config.</font></code></pre>

### Benchmark

* [Predixy](https://github.com/joyieldInc/predixy "predixy") Benchmark Scripts
    <pre><code><font face="黑体">redis-benchmark -t get,set -c 1000 -n 500000 -q -r 3000 -h adhoc-predixy -p 6379 -P 20 -d 100</font></code></pre>
