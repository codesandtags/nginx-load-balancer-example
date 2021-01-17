# Nginx Load Balancer Example

## What is the goal in this lab?

The idea behind is to demostrate how easy is to implement a load balancer using nginx. Also I use a tool to load the test and verify the things are working as expected.

## Tools
* [Load Test](https://www.npmjs.com/package/loadtest)
* [Docker Node Image](https://hub.docker.com/_/node)
* [Nginx](https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/)

## How to run the load test

The options to run the load test are:

* **-t** = seconds
* **-c** = number of clients I create
* **--rps** = request per second


### Pointing to load balancer in nginx
```
loadtest -t 5 -c 100 --rps 100 http://localhost:80

INFO Requests: 0, requests per second: 0, mean latency: 0 ms
INFO
INFO Target URL:          http://localhost:80
INFO Max time (s):        5
INFO Concurrency level:   100
INFO Agent:               none
INFO Requests per second: 100
INFO
INFO Completed requests:  498
INFO Total errors:        0
INFO Total time:          5.005191427 s
INFO Requests per second: 99
INFO Mean latency:        8.8 ms
INFO
INFO Percentage of the requests served within a certain time
INFO   50%      7 ms
INFO   90%      15 ms
INFO   95%      18 ms
INFO   99%      27 ms
INFO  100%      46 ms (longest request)
```

### Pointing to local server without load balancer
```
loadtest -t 5 -c 100 --rps 100 http://localhost:3000

INFO Requests: 0, requests per second: 0, mean latency: 0 ms
INFO
INFO Target URL:          http://localhost:3000
INFO Max time (s):        5
INFO Concurrency level:   100
INFO Agent:               none
INFO Requests per second: 100
INFO
INFO Completed requests:  499
INFO Total errors:        0
INFO Total time:          5.004102952 s
INFO Requests per second: 100
INFO Mean latency:        2.6 ms
INFO
INFO Percentage of the requests served within a certain time
INFO   50%      2 ms
INFO   90%      4 ms
INFO   95%      4 ms
INFO   99%      10 ms
INFO  100%      40 ms (longest request)
```

