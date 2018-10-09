### Configuration

* [Predixy](https://github.com/joyieldInc/predixy "predixy") Configuration
  >Please first update redis-predixy-cfg.yaml for your personal config.
   More details, please see [predix official doc](https://github.com/joyieldInc/predixy "predixy")

### Benchmark

* [Predixy](https://github.com/joyieldInc/predixy "predixy") Benchmark Scripts
  >redis-benchmark -t get,set -c 1000 -n 500000 -q -r 3000 -h adhoc-predixy -p 6379 -P 20 -d 100
