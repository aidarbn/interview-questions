<details>
<summary>What is cache penetration, cache breakdown and cache avalanche? How to solve these problems?</summary>

A **“Cache avalanche"** is when a significant number of caches expire at the same time, which leads to a large number of requests that don't hit the cache and instead directly query the database. This puts a lot of pressure on the database and can potentially cause it to crash.

Solutions: Randomized Expiration Times, Hot Data with No Expiration

**Cache penetration** occurs when a cache that was previously hot expires, resulting in numerous concurrent requests. Without concurrent control, they may all bypass the if(data == null) judgment condition and enter the logic of loading DB data into the cache, putting huge pressure on the DB and even causing it to crash.

Cache penetration can actually be understood as a special case of cache avalanche, so the solution proposed can be further optimized based on the solution of cache avalanche.

Solution: Adding Lock and Queuing, Hotspot data never expires (same as in cache avalanche)

**Cache breakdown** refers to data that is neither in the cache nor in the database. However, users still continuously initiate a large number of requests, causing each request to go to the database, thus overwhelming the database.

Under normal circumstances, this situation is unlikely to occur if you follow the standard page operations. For example, the products you click on from the e-commerce homepage or list page must exist. But someone may forge requests, change the goodsId to 0 and then initiate a large number of requests with the purpose of bringing down your system😱, so it is necessary to prevent tragedies from happening in advance.

Solutions: Parameter verification, Cache empty values, Bloom filters

Bloom filter is a special data structure that can determine if data definitely not exist.

[https://code.likeagirl.io/cache-series-how-to-solve-cache-avalanche-breakdown-and-penetration-problems-196b1f7834d8](https://code.likeagirl.io/cache-series-how-to-solve-cache-avalanche-breakdown-and-penetration-problems-196b1f7834d8)

[https://brilliant.org/wiki/bloom-filter/#:~:text=A%20bloom%20filter%20is%20a,is%20added%20to%20the%20set.](https://brilliant.org/wiki/bloom-filter/#:~:text=A%20bloom%20filter%20is%20a,is%20added%20to%20the%20set.)
</details>
