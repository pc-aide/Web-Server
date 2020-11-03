# Benchmark

## Util
* apache2-utils

[<img src="https://i.imgur.com/dmwk99c.png">](https://i.imgur.com/dmwk99c.png)

## Switchs
1. -n (requests)
2. -c (concurrent
    * Nbr of multiple request to perform at a time

--

## Examples
### 01 - EBL
````shell
ab -n 100 -c 5 http://<ELB>
````
[<img src="https://i.imgur.com/6k60lQq.png">](https://i.imgur.com/6k60lQq.png)
