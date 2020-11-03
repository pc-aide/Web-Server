# Benchmark

## Acronym
* TG - Target Group
* ELB - Elastic Load Balancer

## Util
* apache2-utils

[<img src="https://i.imgur.com/dmwk99c.png">](https://i.imgur.com/dmwk99c.png)

## Switchs
1. -n (requests)
2. -c (concurrent
    * Nbr of multiple request to perform at a time

--

## Web App
* Node.js:

[<img src="https://i.imgur.com/XzIXto0.png">](https://i.imgur.com/XzIXto0.png)

---

## Examples
### 01 - EBL
````shell
ab -n 100 -c 5 http://<ELB>
````
[<img src="https://i.imgur.com/6k60lQq.png">](https://i.imgur.com/6k60lQq.png)

* TG:

[<img src="https://i.imgur.com/3hNJ6Qk.png">](https://i.imgur.com/3hNJ6Qk.png)

* ELB:
