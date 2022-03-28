# 测试方法



```sh
esrally race --pipeline=benchmark-only --target-hosts=127.0.0.1:9200 --offline --track=$track_name
```





# geopoint

## 场景介绍

Point coordinates from PlanetOSM



## 性能对比

baseline：SSD，raceid：248990c0-8161-473e-ad55-e04b088a9843

contender：PMEM，raceid：0467961a-7d07-463c-bf04-c62e1cdf5c1a

|                                                       Metric |          Task |   Baseline |  Contender |     Diff | Unit  |  Diff % |
| -----------------------------------------------------------: | ------------: | ---------: | ---------: | -------: | ----- | ------: |
|                   Cumulative indexing time of primary shards |               |    18.3226 |    22.5511 |  4.22843 | min   | +23.08% |
|            Min cumulative indexing time across primary shard |               |    3.56928 |     4.1734 |  0.60412 | min   | +16.93% |
|         Median cumulative indexing time across primary shard |               |    3.64033 |     4.4681 |  0.82777 | min   | +22.74% |
|            Max cumulative indexing time across primary shard |               |    3.75087 |    4.87172 |  1.12085 | min   | +29.88% |
|          Cumulative indexing throttle time of primary shards |               |          0 |          0 |        0 | min   |   0.00% |
|   Min cumulative indexing throttle time across primary shard |               |          0 |          0 |        0 | min   |   0.00% |
| Median cumulative indexing throttle time across primary shard |               |          0 |          0 |        0 | min   |   0.00% |
|   Max cumulative indexing throttle time across primary shard |               |          0 |          0 |        0 | min   |   0.00% |
|                      Cumulative merge time of primary shards |               |    10.7986 |    8.98578 | -1.81282 | min   | -16.79% |
|                     Cumulative merge count of primary shards |               |         85 |         99 |       14 |       | +16.47% |
|               Min cumulative merge time across primary shard |               |     1.9748 |    1.62397 | -0.35083 | min   | -17.77% |
|            Median cumulative merge time across primary shard |               |    2.08465 |    1.77198 | -0.31267 | min   | -15.00% |
|               Max cumulative merge time across primary shard |               |    2.52868 |     2.0452 | -0.48348 | min   | -19.12% |
|             Cumulative merge throttle time of primary shards |               |    6.35328 |    3.89815 | -2.45513 | min   | -38.64% |
|      Min cumulative merge throttle time across primary shard |               |    1.09192 |    0.59265 | -0.49927 | min   | -45.72% |
|   Median cumulative merge throttle time across primary shard |               |    1.16298 |   0.782983 |    -0.38 | min   | -32.67% |
|      Max cumulative merge throttle time across primary shard |               |     1.6468 |   0.962517 | -0.68428 | min   | -41.55% |
|                    Cumulative refresh time of primary shards |               |     1.0383 |    0.96045 | -0.07785 | min   |  -7.50% |
|                   Cumulative refresh count of primary shards |               |        234 |        227 |       -7 |       |  -2.99% |
|             Min cumulative refresh time across primary shard |               |   0.188633 |   0.175683 | -0.01295 | min   |  -6.87% |
|          Median cumulative refresh time across primary shard |               |   0.208533 |     0.1956 | -0.01293 | min   |  -6.20% |
|             Max cumulative refresh time across primary shard |               |   0.228167 |   0.207367 |  -0.0208 | min   |  -9.12% |
|                      Cumulative flush time of primary shards |               |   0.716817 |    0.05485 | -0.66197 | min   | -92.35% |
|                     Cumulative flush count of primary shards |               |         15 |         15 |        0 |       |   0.00% |
|               Min cumulative flush time across primary shard |               |   0.130333 |    0.00895 | -0.12138 | min   | -93.13% |
|            Median cumulative flush time across primary shard |               |   0.144583 |     0.0097 | -0.13488 | min   | -93.29% |
|               Max cumulative flush time across primary shard |               |   0.150633 |  0.0169833 | -0.13365 | min   | -88.73% |
|                                      Total Young Gen GC time |               |     12.816 |     11.885 |   -0.931 | s     |  -7.26% |
|                                     Total Young Gen GC count |               |       2438 |       2366 |      -72 |       |  -2.95% |
|                                        Total Old Gen GC time |               |      2.495 |      2.144 |   -0.351 | s     | -14.07% |
|                                       Total Old Gen GC count |               |         80 |         75 |       -5 |       |  -6.25% |
|                                                   Store size |               |    3.47638 |    3.51909 |  0.04271 | GB    |  +1.23% |
|                                                Translog size |               |    2.75152 |    2.75161 |   0.0001 | GB    |   0.00% |
|                                       Heap used for segments |               |     25.616 |    24.4421 | -1.17392 | MB    |  -4.58% |
|                                     Heap used for doc values |               | 0.00577164 | 0.00651932 |  0.00075 | MB    | +12.95% |
|                                          Heap used for terms |               |    23.4191 |    22.2898 | -1.12926 | MB    |  -4.82% |
|                                          Heap used for norms |               |          0 |          0 |        0 | MB    |   0.00% |
|                                         Heap used for points |               |   0.887051 |   0.803267 | -0.08378 | MB    |  -9.45% |
|                                  Heap used for stored fields |               |    1.30414 |    1.34251 |  0.03838 | MB    |  +2.94% |
|                                                Segment count |               |         89 |         97 |        8 |       |  +8.99% |
|                                                   error rate |  index-append |          0 |          0 |        0 | %     |   0.00% |
|                                               Min Throughput |       polygon |    2.00314 |    2.00276 | -0.00038 | ops/s |  -0.02% |
|                                              Mean Throughput |       polygon |    2.00381 |    2.00334 | -0.00047 | ops/s |  -0.02% |
|                                            Median Throughput |       polygon |    2.00376 |     2.0033 | -0.00047 | ops/s |  -0.02% |
|                                               Max Throughput |       polygon |    2.00468 |     2.0041 | -0.00058 | ops/s |  -0.03% |
|                                      50th percentile latency |       polygon |    42.9952 |    49.9167 |  6.92152 | ms    | +16.10% |
|                                      90th percentile latency |       polygon |    44.0159 |    50.8497 |  6.83376 | ms    | +15.53% |
|                                      99th percentile latency |       polygon |    46.9132 |    64.5628 |  17.6496 | ms    | +37.62% |
|                                     100th percentile latency |       polygon |    57.0224 |    64.6243 |  7.60196 | ms    | +13.33% |
|                                 50th percentile service time |       polygon |    41.6529 |    48.5961 |  6.94327 | ms    | +16.67% |
|                                 90th percentile service time |       polygon |    42.4593 |    49.4364 |  6.97714 | ms    | +16.43% |
|                                 99th percentile service time |       polygon |    45.3663 |    62.8227 |  17.4564 | ms    | +38.48% |
|                                100th percentile service time |       polygon |     55.575 |      62.99 |  7.41505 | ms    | +13.34% |
|                                                   error rate |       polygon |          0 |          0 |        0 | %     |   0.00% |
|                                               Min Throughput |          bbox |    2.00517 |     2.0047 | -0.00047 | ops/s |  -0.02% |
|                                              Mean Throughput |          bbox |    2.00627 |     2.0057 | -0.00057 | ops/s |  -0.03% |
|                                            Median Throughput |          bbox |    2.00619 |    2.00563 | -0.00056 | ops/s |  -0.03% |
|                                               Max Throughput |          bbox |    2.00771 |    2.00701 |  -0.0007 | ops/s |  -0.03% |
|                                      50th percentile latency |          bbox |    47.7979 |    54.7911 |  6.99318 | ms    | +14.63% |
|                                      90th percentile latency |          bbox |    48.4823 |    56.6091 |  8.12684 | ms    | +16.76% |
|                                      99th percentile latency |          bbox |    51.0398 |     66.608 |  15.5683 | ms    | +30.50% |
|                                     100th percentile latency |          bbox |    51.6791 |    68.1788 |  16.4997 | ms    | +31.93% |
|                                 50th percentile service time |          bbox |    46.5148 |    53.4588 |  6.94392 | ms    | +14.93% |
|                                 90th percentile service time |          bbox |    47.2439 |     54.752 |  7.50815 | ms    | +15.89% |
|                                 99th percentile service time |          bbox |    49.9271 |    65.1091 |   15.182 | ms    | +30.41% |
|                                100th percentile service time |          bbox |    50.1761 |    66.7616 |  16.5855 | ms    | +33.05% |
|                                                   error rate |          bbox |          0 |          0 |        0 | %     |   0.00% |
|                                               Min Throughput |      distance |    5.00847 |    5.00788 | -0.00059 | ops/s |  -0.01% |
|                                              Mean Throughput |      distance |    5.01021 |    5.00953 | -0.00069 | ops/s |  -0.01% |
|                                            Median Throughput |      distance |    5.01007 |     5.0094 | -0.00067 | ops/s |  -0.01% |
|                                               Max Throughput |      distance |    5.01243 |    5.01168 | -0.00075 | ops/s |  -0.01% |
|                                      50th percentile latency |      distance |    8.31504 |     9.3455 |  1.03046 | ms    | +12.39% |
|                                      90th percentile latency |      distance |    8.82937 |    12.1794 |  3.35004 | ms    | +37.94% |
|                                      99th percentile latency |      distance |    11.7103 |    12.9658 |  1.25557 | ms    | +10.72% |
|                                     100th percentile latency |      distance |    11.7197 |    14.6333 |  2.91357 | ms    | +24.86% |
|                                 50th percentile service time |      distance |    7.33868 |    8.34372 |  1.00504 | ms    | +13.70% |
|                                 90th percentile service time |      distance |     7.6353 |    11.2445 |  3.60919 | ms    | +47.27% |
|                                 99th percentile service time |      distance |    10.3584 |    11.6395 |  1.28116 | ms    | +12.37% |
|                                100th percentile service time |      distance |    10.8163 |    13.8835 |  3.06723 | ms    | +28.36% |
|                                                   error rate |      distance |          0 |          0 |        0 | %     |   0.00% |
|                                               Min Throughput | distanceRange |   0.500634 |   0.500589 |   -5e-05 | ops/s |  -0.01% |
|                                              Mean Throughput | distanceRange |    0.50077 |   0.500715 |   -5e-05 | ops/s |  -0.01% |
|                                            Median Throughput | distanceRange |    0.50076 |   0.500705 |   -5e-05 | ops/s |  -0.01% |
|                                               Max Throughput | distanceRange |   0.500946 |   0.500879 |   -7e-05 | ops/s |  -0.01% |
|                                      50th percentile latency | distanceRange |    1141.19 |    1221.08 |  79.8904 | ms    |  +7.00% |
|                                      90th percentile latency | distanceRange |    1151.59 |    1240.84 |  89.2443 | ms    |  +7.75% |
|                                      99th percentile latency | distanceRange |    1160.39 |    1261.99 |  101.597 | ms    |  +8.76% |
|                                     100th percentile latency | distanceRange |    1162.25 |    1289.65 |  127.396 | ms    | +10.96% |
|                                 50th percentile service time | distanceRange |    1139.61 |    1219.66 |  80.0511 | ms    |  +7.02% |
|                                 90th percentile service time | distanceRange |     1149.6 |    1239.01 |  89.4126 | ms    |  +7.78% |
|                                 99th percentile service time | distanceRange |    1158.38 |    1260.73 |  102.347 | ms    |  +8.84% |
|                                100th percentile service time | distanceRange |    1160.22 |    1287.89 |  127.666 | ms    | +11.00% |
|                                                   error rate | distanceRange |          0 |          0 |        0 | %     |   0.00% |



# nyc_taxis

## 场景介绍

Taxi rides in New York in 2015



## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：2b5f6784-5ed1-4aa4-b9b9-867a4764ce40





# so

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：c8c4423a-0748-4520-b5d3-1831f2aed8d7





# dense_vector

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：46d449ea-cb50-4403-8318-5c1a98e16630





# geopointshape

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：f663fe19-a516-4391-9740-1d021609ed6e



# noaa

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：



# geoshape

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：





# http_logs

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：bcbdac0a-3042-4baa-b197-ea40dbc3b9fe





# pmc

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：03f1191b-b1e1-4b8f-8f6a-3b3e2975f4c9



# geonames

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：dd034827-ce45-4ffe-befe-bc1a523ff83a



# nested

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：



# metricbeat

## 场景介绍





## 性能对比

baseline：SSD，raceid：528c206d-abd2-4bbb-b55a-8e65af5a4a4d

contender：PMEM，raceid：





# percolator

## 场景介绍





## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：











































