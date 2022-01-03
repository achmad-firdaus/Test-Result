# PHP FPM CGI VS NO FPM CGI <img src="https://raw.githubusercontent.com/MartinHeinz/MartinHeinz/master/wave.gif" width="30px">

#### LIST
- [Test Case 👻](#test-case-)
- [FPM CGI 👻](#fpm-cgi-)
- [No FPM CGI 👻](#no-fpm-cgi-)

#### TEST CASE 👻
* I use AB tetst in Server(BIONIC) and cURL for request in Windows
* I will AB test with 2000 request and 1000 concurrency reuest

#### FPM CGI 👻
USING INTERNET CONNECTION:
- I have used AB, cURL, Http Request and the result:

        cURL -> is normal and fast response
        
        AB ->
        Benchmarking 192.168.43.105 (be patient)
        Completed 200 requests
        Completed 400 requests
        Completed 600 requests
        Completed 800 requests
        Completed 1000 requests
        Completed 1200 requests
        Completed 1400 requests
        Completed 1600 requests
        Completed 1800 requests
        Completed 2000 requests
        Finished 2000 requests

        Server Software:        Apache/2.4.29
        Server Hostname:        192.168.43.105
        Server Port:            80

        Document Path:          /web-fpm-cgi
        Document Length:        322 bytes

        Concurrency Level:      1000
        Time taken for tests:   1.141 seconds
        Complete requests:      2000
        Failed requests:        0
        Non-2xx responses:      2000
        Total transferred:      1112000 bytes
        HTML transferred:       644000 bytes
        Requests per second:    1753.34 [#/sec] (mean)
        Time per request:       570.339 [ms] (mean)
        Time per request:       0.570 [ms] (mean, across all concurrent requests)
        Transfer rate:          952.01 [Kbytes/sec] received

        Connection Times (ms)
                      min  mean[+/-sd] median   max
        Connect:        0   43  51.7     27     175
        Processing:    62  282 277.6    157     960
        Waiting:       30  281 278.1    157     960
        Total:        124  325 312.1    161    1075

        Percentage of the requests served within a certain time (ms)
          50%    161
          66%    186
          75%    401
          80%    649
          90%    999
          95%   1039
          98%   1060
          99%   1067
         100%   1075 (longest request)

NOT USING INTERNET CONNECTION:
- Sometimes for the first time you use cURL it will be like this and so on it will be normal again:

       cURL & AB test is normal and fast response


#### NO FPM CGI 👻
USING INTERNET CONNECTION:
- I have used cURL, Http Request and the result:

        Everything is normal

- But if there is an incorrect code, it will take a long time to request. This the result:

        Benchmarking 192.168.43.148 (be patient)
        Completed 200 requests
        Completed 400 requests
        Completed 600 requests
        Completed 800 requests
        Completed 1000 requests
        Completed 1200 requests
        Completed 1400 requests
        Completed 1600 requests
        Completed 1800 requests
        Completed 2000 requests
        Finished 2000 requests

        Server Software:        Apache/2.4.29
        Server Hostname:        192.168.43.148
        Server Port:            80

        Document Path:          /web-no-fpm-cgi
        Document Length:        325 bytes

        Concurrency Level:      1000
        Time taken for tests:   2.681 seconds
        Complete requests:      2000
        Failed requests:        0
        Non-2xx responses:      2000
        Total transferred:      1124000 bytes
        HTML transferred:       650000 bytes
        Requests per second:    745.99 [#/sec] (mean)
        Time per request:       1340.499 [ms] (mean)
        Time per request:       1.340 [ms] (mean, across all concurrent requests)
        Transfer rate:          409.42 [Kbytes/sec] received

        Connection Times (ms)
                      min  mean[+/-sd] median   max
        Connect:        0   31  33.1     27      84
        Processing:    15  670 1013.7    123    2591
        Waiting:       13  669 1013.7    122    2591
        Total:         79  702 1037.5    129    2663

        Percentage of the requests served within a certain time (ms)
          50%    129
          66%    145
          75%    240
          80%   2346
          90%   2623
          95%   2642
          98%   2657
          99%   2661
         100%   2663 (longest request)

NOT USING INTERNET CONNECTION:
- Sometimes for the first time you use cURL it will be like this and so on it will be normal again:

        C:\Users\ACHMAD FIRDAUS>curl http://192.168.43.148/web-no-fpm-cgi
        curl: (7) Failed to connect to 192.168.43.148 port 80: Timed out
