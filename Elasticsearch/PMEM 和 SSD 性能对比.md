# 测试方法



```sh
esrally race --pipeline=benchmark-only --target-hosts=127.0.0.1:9200 --offline --track=$track_name
```



# geopoint

## 场景介绍

数据量：2.3 GB

场景描述：Point coordinates from PlanetOSM



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

数据量：74.3 GB

场景描述：Taxi rides in New York in 2015



## 性能对比

baseline：SSD，raceid：f2d62a11-adba-4e9b-9a41-b8ce6e6df5c6

contender：PMEM，raceid：2b5f6784-5ed1-4aa4-b9b9-867a4764ce40

|                                                       Metric |                Task |  Baseline |  Contender |     Diff |   Unit |     Diff % |
| -----------------------------------------------------------: | ------------------: | --------: | ---------: | -------: | -----: | ---------: |
|                   Cumulative indexing time of primary shards |                     |   165.091 |    224.176 |  59.0849 |    min |    +35.79% |
|            Min cumulative indexing time across primary shard |                     |         0 |      4.513 |    4.513 |    min |      0.00% |
|         Median cumulative indexing time across primary shard |                     |         0 |     4.9914 |   4.9914 |    min |      0.00% |
|            Max cumulative indexing time across primary shard |                     |   165.091 |    194.912 |  29.8216 |    min |    +18.06% |
|          Cumulative indexing throttle time of primary shards |                     |         0 |          0 |        0 |    min |      0.00% |
|   Min cumulative indexing throttle time across primary shard |                     |         0 |          0 |        0 |    min |      0.00% |
| Median cumulative indexing throttle time across primary shard |                     |         0 |          0 |        0 |    min |      0.00% |
|   Max cumulative indexing throttle time across primary shard |                     |         0 |          0 |        0 |    min |      0.00% |
|                      Cumulative merge time of primary shards |                     |   68.6997 |    83.2859 |  14.5861 |    min |    +21.23% |
|                     Cumulative merge count of primary shards |                     |       244 |        462 |      218 |        |    +89.34% |
|               Min cumulative merge time across primary shard |                     |         0 |    1.53747 |  1.53747 |    min |      0.00% |
|            Median cumulative merge time across primary shard |                     |         0 |     1.8562 |   1.8562 |    min |      0.00% |
|               Max cumulative merge time across primary shard |                     |   68.6997 |    72.2745 |  3.57472 |    min |     +5.20% |
|             Cumulative merge throttle time of primary shards |                     |   4.33663 |    5.55982 |  1.22318 |    min |    +28.21% |
|      Min cumulative merge throttle time across primary shard |                     |         0 |   0.426317 |  0.42632 |    min |      0.00% |
|   Median cumulative merge throttle time across primary shard |                     |         0 |   0.672783 |  0.67278 |    min |      0.00% |
|      Max cumulative merge throttle time across primary shard |                     |   4.33663 |    1.68252 | -2.65412 |    min |    -61.20% |
|                    Cumulative refresh time of primary shards |                     |  0.902633 |    1.76077 |  0.85813 |    min |    +95.07% |
|                   Cumulative refresh count of primary shards |                     |       104 |        358 |      254 |        |   +244.23% |
|             Min cumulative refresh time across primary shard |                     |         0 |  0.0606667 |  0.06067 |    min |      0.00% |
|          Median cumulative refresh time across primary shard |                     |         0 |    0.18455 |  0.18455 |    min |      0.00% |
|             Max cumulative refresh time across primary shard |                     |  0.902633 |   0.782117 | -0.12052 |    min |    -13.35% |
|                      Cumulative flush time of primary shards |                     |   2.34492 |   0.386333 | -1.95858 |    min |    -83.52% |
|                     Cumulative flush count of primary shards |                     |        27 |         40 |       13 |        |    +48.15% |
|               Min cumulative flush time across primary shard |                     |         0 | 0.00943333 |  0.00943 |    min |      0.00% |
|            Median cumulative flush time across primary shard |                     |         0 |    0.01445 |  0.01445 |    min |      0.00% |
|               Max cumulative flush time across primary shard |                     |   2.34492 |     0.3076 | -2.03732 |    min |    -86.88% |
|                                      Total Young Gen GC time |                     |    95.321 |     93.456 |   -1.865 |      s |     -1.96% |
|                                     Total Young Gen GC count |                     |     14976 |      14906 |      -70 |        |     -0.47% |
|                                        Total Old Gen GC time |                     |    55.533 |     59.386 |    3.853 |      s |     +6.94% |
|                                       Total Old Gen GC count |                     |      1523 |       1597 |       74 |        |     +4.86% |
|                                                   Store size |                     |   29.3156 |    29.9845 |  0.66896 |     GB |     +2.28% |
|                                                Translog size |                     |  0.510754 |    1.06763 |  0.55688 |     GB |   +109.03% |
|                                       Heap used for segments |                     |   90.0968 |    89.5677 | -0.52915 |     MB |     -0.59% |
|                                     Heap used for doc values |                     | 0.0446129 |    1.48523 |  1.44061 |     MB |  +3229.14% |
|                                          Heap used for terms |                     |   74.2777 |    72.0998 | -2.17789 |     MB |     -2.93% |
|                                          Heap used for norms |                     |         0 |          0 |        0 |     MB |      0.00% |
|                                         Heap used for points |                     |   10.3621 |    10.4667 |  0.10455 |     MB |     +1.01% |
|                                  Heap used for stored fields |                     |   5.41232 |     5.5159 |  0.10358 |     MB |     +1.91% |
|                                                Segment count |                     |       117 |        161 |       44 |        |    +37.61% |
|                                               Min Throughput |               index |   99420.7 |    98532.9 | -887.802 | docs/s |     -0.89% |
|                                              Mean Throughput |               index |    104795 |     102619 | -2175.45 | docs/s |     -2.08% |
|                                            Median Throughput |               index |    104953 |     102078 | -2874.67 | docs/s |     -2.74% |
|                                               Max Throughput |               index |    110899 |     107404 | -3495.03 | docs/s |     -3.15% |
|                                      50th percentile latency |               index |   589.925 |    702.331 |  112.406 |     ms |    +19.05% |
|                                      90th percentile latency |               index |   1311.01 |    1135.07 | -175.932 |     ms |    -13.42% |
|                                      99th percentile latency |               index |   2817.79 |    1793.67 | -1024.12 |     ms |    -36.34% |
|                                    99.9th percentile latency |               index |   4587.99 |    2987.49 |  -1600.5 |     ms |    -34.88% |
|                                   99.99th percentile latency |               index |   5920.07 |    3633.19 | -2286.88 |     ms |    -38.63% |
|                                     100th percentile latency |               index |   6796.16 |    3722.02 | -3074.14 |     ms |    -45.23% |
|                                 50th percentile service time |               index |   589.925 |    702.331 |  112.406 |     ms |    +19.05% |
|                                 90th percentile service time |               index |   1311.01 |    1135.07 | -175.932 |     ms |    -13.42% |
|                                 99th percentile service time |               index |   2817.79 |    1793.67 | -1024.12 |     ms |    -36.34% |
|                               99.9th percentile service time |               index |   4587.99 |    2987.49 |  -1600.5 |     ms |    -34.88% |
|                              99.99th percentile service time |               index |   5920.07 |    3633.19 | -2286.88 |     ms |    -38.63% |
|                                100th percentile service time |               index |   6796.16 |    3722.02 | -3074.14 |     ms |    -45.23% |
|                                                   error rate |               index |         0 |          0 |        0 |      % |      0.00% |
|                                               Min Throughput |             default |   3.01488 |    3.02001 |  0.00513 |  ops/s |     +0.17% |
|                                              Mean Throughput |             default |   3.02421 |    3.03263 |  0.00842 |  ops/s |     +0.28% |
|                                            Median Throughput |             default |   3.02207 |    3.02968 |  0.00761 |  ops/s |     +0.25% |
|                                               Max Throughput |             default |   3.04269 |    3.05772 |  0.01503 |  ops/s |     +0.49% |
|                                      50th percentile latency |             default |   3.76753 |    3.23765 | -0.52989 |     ms |    -14.06% |
|                                      90th percentile latency |             default |   4.37645 |    3.78563 | -0.59082 |     ms |    -13.50% |
|                                      99th percentile latency |             default |   5.73874 |    4.04152 | -1.69722 |     ms |    -29.57% |
|                                     100th percentile latency |             default |   6.88348 |    4.11631 | -2.76717 |     ms |    -40.20% |
|                                 50th percentile service time |             default |   2.67136 |    2.17214 | -0.49922 |     ms |    -18.69% |
|                                 90th percentile service time |             default |   3.09221 |    2.35616 | -0.73604 |     ms |    -23.80% |
|                                 99th percentile service time |             default |   4.34351 |    2.47142 |  -1.8721 |     ms |    -43.10% |
|                                100th percentile service time |             default |   5.94937 |    2.49922 | -3.45015 |     ms |    -57.99% |
|                                                   error rate |             default |         0 |          0 |        0 |      % |      0.00% |
|                                               Min Throughput |               range |  0.702157 |   0.701786 | -0.00037 |  ops/s |     -0.05% |
|                                              Mean Throughput |               range |  0.703544 |   0.702929 | -0.00061 |  ops/s |     -0.09% |
|                                            Median Throughput |               range |  0.703226 |   0.702665 | -0.00056 |  ops/s |     -0.08% |
|                                               Max Throughput |               range |  0.706382 |   0.705274 | -0.00111 |  ops/s |     -0.16% |
|                                      50th percentile latency |               range |   654.034 |    938.887 |  284.853 |     ms |    +43.55% |
|                                      90th percentile latency |               range |    658.28 |    947.006 |  288.726 |     ms |    +43.86% |
|                                      99th percentile latency |               range |     662.2 |    953.977 |  291.778 |     ms |    +44.06% |
|                                     100th percentile latency |               range |   663.695 |     961.87 |  298.174 |     ms |    +44.93% |
|                                 50th percentile service time |               range |   652.366 |    937.636 |   285.27 |     ms |    +43.73% |
|                                 90th percentile service time |               range |   656.205 |    945.858 |  289.653 |     ms |    +44.14% |
|                                 99th percentile service time |               range |   660.137 |    953.154 |  293.017 |     ms |    +44.39% |
|                                100th percentile service time |               range |   661.729 |    960.641 |  298.912 |     ms |    +45.17% |
|                                                   error rate |               range |         0 |          0 |        0 |      % |      0.00% |
|                                               Min Throughput | distance_amount_agg |   2.01136 |    2.00239 | -0.00897 |  ops/s |     -0.45% |
|                                              Mean Throughput | distance_amount_agg |   2.01868 |    2.00392 | -0.01477 |  ops/s |     -0.73% |
|                                            Median Throughput | distance_amount_agg |   2.01698 |    2.00357 | -0.01341 |  ops/s |     -0.66% |
|                                               Max Throughput | distance_amount_agg |   2.03355 |    2.00703 | -0.02652 |  ops/s |     -1.30% |
|                                      50th percentile latency | distance_amount_agg |   3.28081 |    377.875 |  374.594 |     ms | +11417.75% |
|                                      90th percentile latency | distance_amount_agg |   3.71972 |    381.541 |  377.821 |     ms | +10157.24% |
|                                      99th percentile latency | distance_amount_agg |   3.98386 |    383.788 |  379.804 |     ms |  +9533.57% |
|                                     100th percentile latency | distance_amount_agg |   4.04577 |    386.327 |  382.281 |     ms |  +9448.90% |
|                                 50th percentile service time | distance_amount_agg |   1.95902 |     376.77 |  374.811 |     ms | +19132.55% |
|                                 90th percentile service time | distance_amount_agg |   2.13652 |    380.508 |  378.371 |     ms | +17709.72% |
|                                 99th percentile service time | distance_amount_agg |   2.35042 |    382.616 |  380.265 |     ms | +16178.63% |
|                                100th percentile service time | distance_amount_agg |   2.48071 |    385.786 |  383.305 |     ms | +15451.46% |
|                                                   error rate | distance_amount_agg |         0 |          0 |        0 |      % |      0.00% |
|                                               Min Throughput |       autohisto_agg |   1.44303 |     1.4974 |  0.05436 |  ops/s |     +3.77% |
|                                              Mean Throughput |       autohisto_agg |   1.46767 |    1.49856 |  0.03088 |  ops/s |     +2.10% |
|                                            Median Throughput |       autohisto_agg |    1.4704 |    1.49869 |  0.02829 |  ops/s |     +1.92% |
|                                               Max Throughput |       autohisto_agg |   1.48012 |    1.49912 |    0.019 |  ops/s |     +1.28% |
|                                      50th percentile latency |       autohisto_agg |   490.032 |    546.737 |  56.7047 |     ms |    +11.57% |
|                                      90th percentile latency |       autohisto_agg |   495.555 |    556.652 |  61.0965 |     ms |    +12.33% |
|                                      99th percentile latency |       autohisto_agg |   501.054 |    568.211 |  67.1567 |     ms |    +13.40% |
|                                     100th percentile latency |       autohisto_agg |   504.812 |    574.132 |  69.3206 |     ms |    +13.73% |
|                                 50th percentile service time |       autohisto_agg |    488.93 |     545.73 |  56.8006 |     ms |    +11.62% |
|                                 90th percentile service time |       autohisto_agg |   494.402 |    555.249 |  60.8472 |     ms |    +12.31% |
|                                 99th percentile service time |       autohisto_agg |   499.717 |     567.07 |  67.3534 |     ms |    +13.48% |
|                                100th percentile service time |       autohisto_agg |   504.316 |    573.238 |  68.9214 |     ms |    +13.67% |
|                                                   error rate |       autohisto_agg |         0 |          0 |        0 |      % |      0.00% |
|                                               Min Throughput |  date_histogram_agg |    1.5025 |    1.50175 | -0.00074 |  ops/s |     -0.05% |
|                                              Mean Throughput |  date_histogram_agg |   1.50407 |    1.50284 | -0.00123 |  ops/s |     -0.08% |
|                                            Median Throughput |  date_histogram_agg |   1.50371 |    1.50259 | -0.00112 |  ops/s |     -0.07% |
|                                               Max Throughput |  date_histogram_agg |   1.50719 |    1.50504 | -0.00215 |  ops/s |     -0.14% |
|                                      50th percentile latency |  date_histogram_agg |   485.877 |    541.873 |  55.9967 |     ms |    +11.52% |
|                                      90th percentile latency |  date_histogram_agg |   493.491 |    549.795 |  56.3042 |     ms |    +11.41% |
|                                      99th percentile latency |  date_histogram_agg |   504.993 |    568.926 |  63.9332 |     ms |    +12.66% |
|                                     100th percentile latency |  date_histogram_agg |   505.997 |    569.573 |  63.5765 |     ms |    +12.56% |
|                                 50th percentile service time |  date_histogram_agg |   484.949 |    541.007 |  56.0579 |     ms |    +11.56% |
|                                 90th percentile service time |  date_histogram_agg |   492.628 |    549.232 |  56.6042 |     ms |    +11.49% |
|                                 99th percentile service time |  date_histogram_agg |   503.845 |    568.322 |  64.4776 |     ms |    +12.80% |
|                                100th percentile service time |  date_histogram_agg |   504.642 |    568.563 |  63.9215 |     ms |    +12.67% |
|                                                   error rate |  date_histogram_agg |         0 |          0 |        0 |      % |      0.00% |



# so

## 场景介绍

数据量：33.1 GB

场景描述：Indexing benchmark using up to questions and answers from StackOverflow



## 性能对比

baseline：SSD，raceid：b62dffd0-197f-4737-b152-997448a0b6ae

contender：PMEM，raceid：c8c4423a-0748-4520-b5d3-1831f2aed8d7

|                                                       Metric |         Task |    Baseline |  Contender |     Diff |   Unit |    Diff % |
| -----------------------------------------------------------: | -----------: | ----------: | ---------: | -------: | -----: | --------: |
|                   Cumulative indexing time of primary shards |              |     312.561 |    406.247 |  93.6854 |    min |   +29.97% |
|            Min cumulative indexing time across primary shard |              |           0 |      4.513 |    4.513 |    min |     0.00% |
|         Median cumulative indexing time across primary shard |              |     28.8402 |     20.579 | -8.26119 |    min |   -28.64% |
|            Max cumulative indexing time across primary shard |              |     165.091 |    194.912 |  29.8216 |    min |   +18.06% |
|          Cumulative indexing throttle time of primary shards |              | 0.000766667 |          0 | -0.00077 |    min |  -100.00% |
|   Min cumulative indexing throttle time across primary shard |              |           0 |          0 |        0 |    min |     0.00% |
| Median cumulative indexing throttle time across primary shard |              |           0 |          0 |        0 |    min |     0.00% |
|   Max cumulative indexing throttle time across primary shard |              | 0.000766667 |          0 | -0.00077 |    min |  -100.00% |
|                      Cumulative merge time of primary shards |              |     189.941 |    202.075 |  12.1346 |    min |    +6.39% |
|                     Cumulative merge count of primary shards |              |         999 |       1366 |      367 |        |   +36.74% |
|               Min cumulative merge time across primary shard |              |           0 |    1.53747 |  1.53747 |    min |     0.00% |
|            Median cumulative merge time across primary shard |              |     22.4441 |    12.2865 | -10.1576 |    min |   -45.26% |
|               Max cumulative merge time across primary shard |              |     68.6997 |    72.2745 |  3.57472 |    min |    +5.20% |
|             Cumulative merge throttle time of primary shards |              |     56.1792 |    46.1088 | -10.0704 |    min |   -17.93% |
|      Min cumulative merge throttle time across primary shard |              |           0 |   0.426317 |  0.42632 |    min |     0.00% |
|   Median cumulative merge throttle time across primary shard |              |     4.33663 |    1.30721 | -3.02943 |    min |   -69.86% |
|      Max cumulative merge throttle time across primary shard |              |     11.9303 |    9.49347 | -2.43685 |    min |   -20.43% |
|                    Cumulative refresh time of primary shards |              |     16.5207 |    16.6363 |  0.11557 |    min |    +0.70% |
|                   Cumulative refresh count of primary shards |              |        1663 |       1986 |      323 |        |   +19.42% |
|             Min cumulative refresh time across primary shard |              |           0 |  0.0606667 |  0.06067 |    min |     0.00% |
|          Median cumulative refresh time across primary shard |              |    0.902633 |   0.489125 | -0.41351 |    min |   -45.81% |
|             Max cumulative refresh time across primary shard |              |     3.17297 |    2.99217 |  -0.1808 |    min |    -5.70% |
|                      Cumulative flush time of primary shards |              |     13.2078 |    1.02655 | -12.1812 |    min |   -92.23% |
|                     Cumulative flush count of primary shards |              |          98 |        112 |       14 |        |   +14.29% |
|               Min cumulative flush time across primary shard |              |           0 | 0.00943333 |  0.00943 |    min |     0.00% |
|            Median cumulative flush time across primary shard |              |     2.04268 |   0.069425 | -1.97326 |    min |   -96.60% |
|               Max cumulative flush time across primary shard |              |     2.34492 |     0.3076 | -2.03732 |    min |   -86.88% |
|                                      Total Young Gen GC time |              |      37.463 |     37.543 |     0.08 |      s |    +0.21% |
|                                     Total Young Gen GC count |              |        7521 |       7649 |      128 |        |    +1.70% |
|                                        Total Old Gen GC time |              |      30.306 |     34.192 |    3.886 |      s |   +12.82% |
|                                       Total Old Gen GC count |              |         951 |       1051 |      100 |        |   +10.52% |
|                                                   Store size |              |     88.3506 |      88.02 | -0.33055 |     GB |    -0.37% |
|                                                Translog size |              |      3.2016 |    3.71422 |  0.51262 |     GB |   +16.01% |
|                                       Heap used for segments |              |     109.355 |    108.094 | -1.26118 |     MB |    -1.15% |
|                                     Heap used for doc values |              |    0.126404 |    1.56427 |  1.43787 |     MB | +1137.52% |
|                                          Heap used for terms |              |     86.0402 |    83.1528 | -2.88742 |     MB |    -3.36% |
|                                          Heap used for norms |              |   0.0435791 |  0.0460205 |  0.00244 |     MB |    +5.60% |
|                                         Heap used for points |              |     10.7845 |    10.8909 |  0.10643 |     MB |    +0.99% |
|                                  Heap used for stored fields |              |     12.3605 |      12.44 |   0.0795 |     MB |    +0.64% |
|                                                Segment count |              |         474 |        538 |       64 |        |   +13.50% |
|                                               Min Throughput | index-append |     40511.9 |    50493.8 |  9981.92 | docs/s |   +24.64% |
|                                              Mean Throughput | index-append |     46804.4 |    53815.1 |  7010.66 | docs/s |   +14.98% |
|                                            Median Throughput | index-append |     46603.4 |    53630.3 |  7026.84 | docs/s |   +15.08% |
|                                               Max Throughput | index-append |     53165.3 |    57700.4 |  4535.07 | docs/s |    +8.53% |
|                                      50th percentile latency | index-append |     751.156 |    756.588 |  5.43125 |     ms |    +0.72% |
|                                      90th percentile latency | index-append |     1385.35 |    1118.73 | -266.621 |     ms |   -19.25% |
|                                      99th percentile latency | index-append |     3072.94 |    1373.89 | -1699.05 |     ms |   -55.29% |
|                                    99.9th percentile latency | index-append |     4293.85 |    1564.16 | -2729.69 |     ms |   -63.57% |
|                                     100th percentile latency | index-append |      5218.4 |    1864.55 | -3353.84 |     ms |   -64.27% |
|                                 50th percentile service time | index-append |     751.156 |    756.588 |  5.43125 |     ms |    +0.72% |
|                                 90th percentile service time | index-append |     1385.35 |    1118.73 | -266.621 |     ms |   -19.25% |
|                                 99th percentile service time | index-append |     3072.94 |    1373.89 | -1699.05 |     ms |   -55.29% |
|                               99.9th percentile service time | index-append |     4293.85 |    1564.16 | -2729.69 |     ms |   -63.57% |
|                                100th percentile service time | index-append |      5218.4 |    1864.55 | -3353.84 |     ms |   -64.27% |
|                                                   error rate | index-append |           0 |          0 |        0 |      % |     0.00% |



# dense_vector

## 场景介绍

数据量：19.5 GB

场景描述：Benchmark for dense vector indexing and search



## 性能对比

baseline：SSD，raceid：55c75187-02e0-4161-8373-028aaf220f08

contender：PMEM，raceid：46d449ea-cb50-4403-8318-5c1a98e16630

|                                                       Metric |                                   Task |    Baseline |  Contender |     Diff |   Unit |    Diff % |
| -----------------------------------------------------------: | -------------------------------------: | ----------: | ---------: | -------: | -----: | --------: |
|                   Cumulative indexing time of primary shards |                                        |     336.746 |    431.715 |  94.9688 |    min |   +28.20% |
|            Min cumulative indexing time across primary shard |                                        |           0 |      4.513 |    4.513 |    min |     0.00% |
|         Median cumulative indexing time across primary shard |                                        |     26.5126 |    25.4684 |  -1.0442 |    min |    -3.94% |
|            Max cumulative indexing time across primary shard |                                        |     165.091 |    194.912 |  29.8216 |    min |   +18.06% |
|          Cumulative indexing throttle time of primary shards |                                        | 0.000766667 |          0 | -0.00077 |    min |  -100.00% |
|   Min cumulative indexing throttle time across primary shard |                                        |           0 |          0 |        0 |    min |     0.00% |
| Median cumulative indexing throttle time across primary shard |                                        |           0 |          0 |        0 |    min |     0.00% |
|   Max cumulative indexing throttle time across primary shard |                                        | 0.000766667 |          0 | -0.00077 |    min |  -100.00% |
|                      Cumulative merge time of primary shards |                                        |     227.734 |    237.356 |  9.62177 |    min |    +4.23% |
|                     Cumulative merge count of primary shards |                                        |        1019 |       1387 |      368 |        |   +36.11% |
|               Min cumulative merge time across primary shard |                                        |           0 |    1.53747 |  1.53747 |    min |     0.00% |
|            Median cumulative merge time across primary shard |                                        |     23.1199 |    22.4983 | -0.62162 |    min |    -2.69% |
|               Max cumulative merge time across primary shard |                                        |     68.6997 |    72.2745 |  3.57472 |    min |    +5.20% |
|             Cumulative merge throttle time of primary shards |                                        |      83.478 |    69.9677 | -13.5103 |    min |   -16.18% |
|      Min cumulative merge throttle time across primary shard |                                        |           0 |   0.426317 |  0.42632 |    min |     0.00% |
|   Median cumulative merge throttle time across primary shard |                                        |     6.70773 |    1.68252 | -5.02522 |    min |   -74.92% |
|      Max cumulative merge throttle time across primary shard |                                        |     27.2988 |    23.8589 |  -3.4399 |    min |   -12.60% |
|                    Cumulative refresh time of primary shards |                                        |     17.4856 |     17.556 |  0.07035 |    min |    +0.40% |
|                   Cumulative refresh count of primary shards |                                        |        1773 |       2097 |      324 |        |   +18.27% |
|             Min cumulative refresh time across primary shard |                                        |           0 |  0.0606667 |  0.06067 |    min |     0.00% |
|          Median cumulative refresh time across primary shard |                                        |     0.89855 |   0.782117 | -0.11643 |    min |   -12.96% |
|             Max cumulative refresh time across primary shard |                                        |     3.18668 |    2.99333 | -0.19335 |    min |    -6.07% |
|                      Cumulative flush time of primary shards |                                        |     16.9625 |    3.93978 | -13.0227 |    min |   -76.77% |
|                     Cumulative flush count of primary shards |                                        |         144 |        158 |       14 |        |    +9.72% |
|               Min cumulative flush time across primary shard |                                        |           0 | 0.00943333 |  0.00943 |    min |     0.00% |
|            Median cumulative flush time across primary shard |                                        |     2.09033 |   0.121183 | -1.96915 |    min |   -94.20% |
|               Max cumulative flush time across primary shard |                                        |     3.68175 |    2.90753 | -0.77422 |    min |   -21.03% |
|                                      Total Young Gen GC time |                                        |      12.593 |     13.078 |    0.485 |      s |    +3.85% |
|                                     Total Young Gen GC count |                                        |        3376 |       3381 |        5 |        |    +0.15% |
|                                        Total Old Gen GC time |                                        |       8.992 |      10.24 |    1.248 |      s |   +13.88% |
|                                       Total Old Gen GC count |                                        |         235 |        235 |        0 |        |     0.00% |
|                                                   Store size |                                        |     83.8597 |    84.6223 |  0.76262 |     GB |    +0.91% |
|                                                Translog size |                                        |     3.70463 |    4.21725 |  0.51262 |     GB |   +13.84% |
|                                       Heap used for segments |                                        |     117.122 |    115.513 |  -1.6091 |     MB |    -1.37% |
|                                     Heap used for doc values |                                        |   0.0856628 |    1.51824 |  1.43258 |     MB | +1672.34% |
|                                          Heap used for terms |                                        |      87.768 |    84.5305 | -3.23749 |     MB |    -3.69% |
|                                          Heap used for norms |                                        |   0.0158691 |  0.0164795 |  0.00061 |     MB |    +3.85% |
|                                         Heap used for points |                                        |     15.0188 |    15.1248 |  0.10602 |     MB |    +0.71% |
|                                  Heap used for stored fields |                                        |     14.2336 |    14.3228 |  0.08918 |     MB |    +0.63% |
|                                                Segment count |                                        |         248 |        297 |       49 |        |   +19.76% |
|                                     100th percentile latency |                           create-index |     12.6993 |    8.80851 | -3.89083 |     ms |   -30.64% |
|                                100th percentile service time |                           create-index |     12.6993 |    8.80851 | -3.89083 |     ms |   -30.64% |
|                                                   error rate |                           create-index |         100 |        100 |        0 |      % |     0.00% |
|                                               Min Throughput |                           index-append |     5808.88 |    6258.29 |  449.402 | docs/s |    +7.74% |
|                                              Mean Throughput |                           index-append |     6086.75 |    6355.27 |  268.521 | docs/s |    +4.41% |
|                                            Median Throughput |                           index-append |     6017.54 |    6288.38 |  270.842 | docs/s |    +4.50% |
|                                               Max Throughput |                           index-append |     7626.72 |    7915.62 |  288.906 | docs/s |    +3.79% |
|                                      50th percentile latency |                           index-append |     602.252 |    609.744 |  7.49158 |     ms |    +1.24% |
|                                      90th percentile latency |                           index-append |     667.328 |    649.546 |  -17.782 |     ms |    -2.66% |
|                                      99th percentile latency |                           index-append |     4880.81 |    5181.16 |  300.348 |     ms |    +6.15% |
|                                    99.9th percentile latency |                           index-append |     5430.33 |    5346.41 |   -83.92 |     ms |    -1.55% |
|                                     100th percentile latency |                           index-append |     6679.78 |    5405.91 | -1273.87 |     ms |   -19.07% |
|                                 50th percentile service time |                           index-append |     602.252 |    609.744 |  7.49158 |     ms |    +1.24% |
|                                 90th percentile service time |                           index-append |     667.328 |    649.546 |  -17.782 |     ms |    -2.66% |
|                                 99th percentile service time |                           index-append |     4880.81 |    5181.16 |  300.348 |     ms |    +6.15% |
|                               99.9th percentile service time |                           index-append |     5430.33 |    5346.41 |   -83.92 |     ms |    -1.55% |
|                                100th percentile service time |                           index-append |     6679.78 |    5405.91 | -1273.87 |     ms |   -19.07% |
|                                                   error rate |                           index-append |           0 |          0 |        0 |      % |     0.00% |
|                                      50th percentile latency |    knn-search-10-50-before-force-merge |     1.77614 |     1.6588 | -0.11734 |     ms |    -6.61% |
|                                      90th percentile latency |    knn-search-10-50-before-force-merge |     2.45086 |    1.78781 | -0.66305 |     ms |   -27.05% |
|                                      99th percentile latency |    knn-search-10-50-before-force-merge |     3.75217 |    1.87561 | -1.87656 |     ms |   -50.01% |
|                                     100th percentile latency |    knn-search-10-50-before-force-merge |     9.49562 |    1.96945 | -7.52617 |     ms |   -79.26% |
|                                 50th percentile service time |    knn-search-10-50-before-force-merge |     1.77614 |     1.6588 | -0.11734 |     ms |    -6.61% |
|                                 90th percentile service time |    knn-search-10-50-before-force-merge |     2.45086 |    1.78781 | -0.66305 |     ms |   -27.05% |
|                                 99th percentile service time |    knn-search-10-50-before-force-merge |     3.75217 |    1.87561 | -1.87656 |     ms |   -50.01% |
|                                100th percentile service time |    knn-search-10-50-before-force-merge |     9.49562 |    1.96945 | -7.52617 |     ms |   -79.26% |
|                                                   error rate |    knn-search-10-50-before-force-merge |         100 |        100 |        0 |      % |     0.00% |
|                                      50th percentile latency |   knn-search-10-100-before-force-merge |     1.49209 |    1.47257 | -0.01952 |     ms |    -1.31% |
|                                      90th percentile latency |   knn-search-10-100-before-force-merge |     1.78047 |    1.54723 | -0.23325 |     ms |   -13.10% |
|                                      99th percentile latency |   knn-search-10-100-before-force-merge |     2.16932 |    1.79104 | -0.37828 |     ms |   -17.44% |
|                                     100th percentile latency |   knn-search-10-100-before-force-merge |     2.50839 |    4.44578 |  1.93739 |     ms |   +77.24% |
|                                 50th percentile service time |   knn-search-10-100-before-force-merge |     1.49209 |    1.47257 | -0.01952 |     ms |    -1.31% |
|                                 90th percentile service time |   knn-search-10-100-before-force-merge |     1.78047 |    1.54723 | -0.23325 |     ms |   -13.10% |
|                                 99th percentile service time |   knn-search-10-100-before-force-merge |     2.16932 |    1.79104 | -0.37828 |     ms |   -17.44% |
|                                100th percentile service time |   knn-search-10-100-before-force-merge |     2.50839 |    4.44578 |  1.93739 |     ms |   +77.24% |
|                                                   error rate |   knn-search-10-100-before-force-merge |         100 |        100 |        0 |      % |     0.00% |
|                                      50th percentile latency | knn-search-100-1000-before-force-merge |     1.33248 |    1.33678 |  0.00429 |     ms |    +0.32% |
|                                      90th percentile latency | knn-search-100-1000-before-force-merge |     1.45882 |     1.4697 |  0.01088 |     ms |    +0.75% |
|                                      99th percentile latency | knn-search-100-1000-before-force-merge |     1.96115 |    1.71503 | -0.24611 |     ms |   -12.55% |
|                                     100th percentile latency | knn-search-100-1000-before-force-merge |     4.22338 |    1.82581 | -2.39757 |     ms |   -56.77% |
|                                 50th percentile service time | knn-search-100-1000-before-force-merge |     1.33248 |    1.33678 |  0.00429 |     ms |    +0.32% |
|                                 90th percentile service time | knn-search-100-1000-before-force-merge |     1.45882 |     1.4697 |  0.01088 |     ms |    +0.75% |
|                                 99th percentile service time | knn-search-100-1000-before-force-merge |     1.96115 |    1.71503 | -0.24611 |     ms |   -12.55% |
|                                100th percentile service time | knn-search-100-1000-before-force-merge |     4.22338 |    1.82581 | -2.39757 |     ms |   -56.77% |
|                                                   error rate | knn-search-100-1000-before-force-merge |         100 |        100 |        0 |      % |     0.00% |
|                                      50th percentile latency |  script-score-query-before-force-merge |     1.91248 |    1.74515 | -0.16733 |     ms |    -8.75% |
|                                      90th percentile latency |  script-score-query-before-force-merge |     2.05583 |    1.96158 | -0.09426 |     ms |    -4.58% |
|                                      99th percentile latency |  script-score-query-before-force-merge |     2.77322 |    2.56367 | -0.20955 |     ms |    -7.56% |
|                                     100th percentile latency |  script-score-query-before-force-merge |     2.95668 |    3.17972 |  0.22303 |     ms |    +7.54% |
|                                 50th percentile service time |  script-score-query-before-force-merge |     1.91248 |    1.74515 | -0.16733 |     ms |    -8.75% |
|                                 90th percentile service time |  script-score-query-before-force-merge |     2.05583 |    1.96158 | -0.09426 |     ms |    -4.58% |
|                                 99th percentile service time |  script-score-query-before-force-merge |     2.77322 |    2.56367 | -0.20955 |     ms |    -7.56% |
|                                100th percentile service time |  script-score-query-before-force-merge |     2.95668 |    3.17972 |  0.22303 |     ms |    +7.54% |
|                                                   error rate |  script-score-query-before-force-merge |         100 |        100 |        0 |      % |     0.00% |
|                                               Min Throughput |                            force-merge |  0.00350147 | 0.00434967 |  0.00085 |  ops/s |   +24.22% |
|                                              Mean Throughput |                            force-merge |  0.00350147 | 0.00434967 |  0.00085 |  ops/s |   +24.22% |
|                                            Median Throughput |                            force-merge |  0.00350147 | 0.00434967 |  0.00085 |  ops/s |   +24.22% |
|                                               Max Throughput |                            force-merge |  0.00350147 | 0.00434967 |  0.00085 |  ops/s |   +24.22% |
|                                     100th percentile latency |                            force-merge |      285594 |     229902 | -55691.9 |     ms |   -19.50% |
|                                100th percentile service time |                            force-merge |      285594 |     229902 | -55691.9 |     ms |   -19.50% |
|                                                   error rate |                            force-merge |           0 |          0 |        0 |      % |     0.00% |
|                                      50th percentile latency |                       knn-search-10-50 |     1.25738 |    1.28913 |  0.03174 |     ms |    +2.52% |
|                                      90th percentile latency |                       knn-search-10-50 |     1.38892 |    1.81576 |  0.42684 |     ms |   +30.73% |
|                                      99th percentile latency |                       knn-search-10-50 |     1.46816 |    1.98894 |  0.52078 |     ms |   +35.47% |
|                                     100th percentile latency |                       knn-search-10-50 |     4.18863 |    3.91482 | -0.27381 |     ms |    -6.54% |
|                                 50th percentile service time |                       knn-search-10-50 |     1.25738 |    1.28913 |  0.03174 |     ms |    +2.52% |
|                                 90th percentile service time |                       knn-search-10-50 |     1.38892 |    1.81576 |  0.42684 |     ms |   +30.73% |
|                                 99th percentile service time |                       knn-search-10-50 |     1.46816 |    1.98894 |  0.52078 |     ms |   +35.47% |
|                                100th percentile service time |                       knn-search-10-50 |     4.18863 |    3.91482 | -0.27381 |     ms |    -6.54% |
|                                                   error rate |                       knn-search-10-50 |         100 |        100 |        0 |      % |     0.00% |
|                                      50th percentile latency |                      knn-search-10-100 |     1.24565 |    1.24857 |  0.00292 |     ms |    +0.23% |
|                                      90th percentile latency |                      knn-search-10-100 |     1.39826 |     1.3437 | -0.05456 |     ms |    -3.90% |
|                                      99th percentile latency |                      knn-search-10-100 |     1.40926 |    1.42647 |  0.01721 |     ms |    +1.22% |
|                                     100th percentile latency |                      knn-search-10-100 |     1.41858 |    1.42799 |   0.0094 |     ms |    +0.66% |
|                                 50th percentile service time |                      knn-search-10-100 |     1.24565 |    1.24857 |  0.00292 |     ms |    +0.23% |
|                                 90th percentile service time |                      knn-search-10-100 |     1.39826 |     1.3437 | -0.05456 |     ms |    -3.90% |
|                                 99th percentile service time |                      knn-search-10-100 |     1.40926 |    1.42647 |  0.01721 |     ms |    +1.22% |
|                                100th percentile service time |                      knn-search-10-100 |     1.41858 |    1.42799 |   0.0094 |     ms |    +0.66% |
|                                                   error rate |                      knn-search-10-100 |         100 |        100 |        0 |      % |     0.00% |
|                                      50th percentile latency |                    knn-search-100-1000 |     1.26518 |     1.2602 | -0.00498 |     ms |    -0.39% |
|                                      90th percentile latency |                    knn-search-100-1000 |     1.41703 |    1.37706 | -0.03997 |     ms |    -2.82% |
|                                      99th percentile latency |                    knn-search-100-1000 |     1.44304 |    1.50542 |  0.06238 |     ms |    +4.32% |
|                                     100th percentile latency |                    knn-search-100-1000 |     1.54223 |    4.26046 |  2.71823 |     ms |  +176.25% |
|                                 50th percentile service time |                    knn-search-100-1000 |     1.26518 |     1.2602 | -0.00498 |     ms |    -0.39% |
|                                 90th percentile service time |                    knn-search-100-1000 |     1.41703 |    1.37706 | -0.03997 |     ms |    -2.82% |
|                                 99th percentile service time |                    knn-search-100-1000 |     1.44304 |    1.50542 |  0.06238 |     ms |    +4.32% |
|                                100th percentile service time |                    knn-search-100-1000 |     1.54223 |    4.26046 |  2.71823 |     ms |  +176.25% |
|                                                   error rate |                    knn-search-100-1000 |         100 |        100 |        0 |      % |     0.00% |
|                                      50th percentile latency |                     script-score-query |     1.75507 |    1.61249 | -0.14258 |     ms |    -8.12% |
|                                      90th percentile latency |                     script-score-query |     2.02456 |    1.77411 | -0.25045 |     ms |   -12.37% |
|                                      99th percentile latency |                     script-score-query |     3.59567 |    2.51176 | -1.08391 |     ms |   -30.14% |
|                                     100th percentile latency |                     script-score-query |     4.57164 |    4.62311 |  0.05146 |     ms |    +1.13% |
|                                 50th percentile service time |                     script-score-query |     1.75507 |    1.61249 | -0.14258 |     ms |    -8.12% |
|                                 90th percentile service time |                     script-score-query |     2.02456 |    1.77411 | -0.25045 |     ms |   -12.37% |
|                                 99th percentile service time |                     script-score-query |     3.59567 |    2.51176 | -1.08391 |     ms |   -30.14% |
|                                100th percentile service time |                     script-score-query |     4.57164 |    4.62311 |  0.05146 |     ms |    +1.13% |
|                                                   error rate |                     script-score-query |         100 |        100 |        0 |      % |     0.00% |



# geopointshape

## 场景介绍

数据量：2.6 GB

场景描述：Point coordinates from PlanetOSM indexed as geoshapes 



## 性能对比

baseline：SSD，raceid：a3bfc1cc-f0b7-4b7f-afde-8bf2ca5934d0

contender：PMEM，raceid：f663fe19-a516-4391-9740-1d021609ed6e

|                                                       Metric |         Task |    Baseline |  Contender |     Diff |   Unit |    Diff % |
| -----------------------------------------------------------: | -----------: | ----------: | ---------: | -------: | -----: | --------: |
|                   Cumulative indexing time of primary shards |              |     358.307 |    455.476 |  97.1689 |    min |   +27.12% |
|            Min cumulative indexing time across primary shard |              |           0 |      4.513 |    4.513 |    min |     0.00% |
|         Median cumulative indexing time across primary shard |              |      24.185 |    24.6147 |  0.42976 |    min |    +1.78% |
|            Max cumulative indexing time across primary shard |              |     165.091 |    194.912 |  29.8216 |    min |   +18.06% |
|          Cumulative indexing throttle time of primary shards |              | 0.000766667 |          0 | -0.00077 |    min |  -100.00% |
|   Min cumulative indexing throttle time across primary shard |              |           0 |          0 |        0 |    min |     0.00% |
| Median cumulative indexing throttle time across primary shard |              |           0 |          0 |        0 |    min |     0.00% |
|   Max cumulative indexing throttle time across primary shard |              | 0.000766667 |          0 | -0.00077 |    min |  -100.00% |
|                      Cumulative merge time of primary shards |              |     237.831 |    248.054 |  10.2227 |    min |    +4.30% |
|                     Cumulative merge count of primary shards |              |        1073 |       1442 |      369 |        |   +34.39% |
|               Min cumulative merge time across primary shard |              |           0 |    1.53747 |  1.53747 |    min |     0.00% |
|            Median cumulative merge time across primary shard |              |     22.4441 |    16.5981 | -5.84596 |    min |   -26.05% |
|               Max cumulative merge time across primary shard |              |     68.6997 |    72.2745 |  3.57472 |    min |    +5.20% |
|             Cumulative merge throttle time of primary shards |              |     84.5919 |    70.8858 |  -13.706 |    min |   -16.20% |
|      Min cumulative merge throttle time across primary shard |              |           0 |   0.426317 |  0.42632 |    min |     0.00% |
|   Median cumulative merge throttle time across primary shard |              |     4.33663 |    1.30721 | -3.02943 |    min |   -69.86% |
|      Max cumulative merge throttle time across primary shard |              |     27.2988 |    23.8589 |  -3.4399 |    min |   -12.60% |
|                    Cumulative refresh time of primary shards |              |     17.6024 |    17.6625 |   0.0601 |    min |    +0.34% |
|                   Cumulative refresh count of primary shards |              |        1833 |       2159 |      326 |        |   +17.79% |
|             Min cumulative refresh time across primary shard |              |           0 |  0.0606667 |  0.06067 |    min |     0.00% |
|          Median cumulative refresh time across primary shard |              |    0.894467 |   0.489125 | -0.40534 |    min |   -45.32% |
|             Max cumulative refresh time across primary shard |              |     3.18668 |    2.99333 | -0.19335 |    min |    -6.07% |
|                      Cumulative flush time of primary shards |              |     17.5428 |    4.15283 | -13.3899 |    min |   -76.33% |
|                     Cumulative flush count of primary shards |              |         159 |        173 |       14 |        |    +8.81% |
|               Min cumulative flush time across primary shard |              |           0 | 0.00943333 |  0.00943 |    min |     0.00% |
|            Median cumulative flush time across primary shard |              |     2.05822 |   0.124183 | -1.93403 |    min |   -93.97% |
|               Max cumulative flush time across primary shard |              |     3.68175 |    2.90753 | -0.77422 |    min |   -21.03% |
|                                      Total Young Gen GC time |              |      15.171 |      15.19 |    0.019 |      s |    +0.13% |
|                                     Total Young Gen GC count |              |        2623 |       2618 |       -5 |        |    -0.19% |
|                                        Total Old Gen GC time |              |       7.252 |      7.828 |    0.576 |      s |    +7.94% |
|                                       Total Old Gen GC count |              |         201 |        215 |       14 |        |    +6.97% |
|                                                   Store size |              |     87.6711 |    88.4446 |  0.77355 |     GB |    +0.88% |
|                                                Translog size |              |     4.23924 |   0.534622 | -3.70461 |     GB |   -87.39% |
|                                       Heap used for segments |              |     133.078 |    131.087 | -1.99082 |     MB |    -1.50% |
|                                     Heap used for doc values |              |   0.0857277 |     1.5183 |  1.43258 |     MB | +1671.08% |
|                                          Heap used for terms |              |     101.775 |    98.1724 | -3.60291 |     MB |    -3.54% |
|                                          Heap used for norms |              |   0.0158691 |  0.0164795 |  0.00061 |     MB |    +3.85% |
|                                         Heap used for points |              |     15.7729 |    15.8789 |  0.10604 |     MB |    +0.67% |
|                                  Heap used for stored fields |              |     15.4282 |    15.5011 |  0.07286 |     MB |    +0.47% |
|                                                Segment count |              |         249 |        298 |       49 |        |   +19.68% |
|                                               Min Throughput | index-append |      247112 |     267919 |    20807 | docs/s |    +8.42% |
|                                              Mean Throughput | index-append |      255993 |     274353 |  18359.5 | docs/s |    +7.17% |
|                                            Median Throughput | index-append |      255705 |     274460 |  18754.9 | docs/s |    +7.33% |
|                                               Max Throughput | index-append |      260966 |     278357 |  17390.5 | docs/s |    +6.66% |
|                                      50th percentile latency | index-append |     132.692 |    131.345 | -1.34778 |     ms |    -1.02% |
|                                      90th percentile latency | index-append |     183.185 |    166.522 | -16.6626 |     ms |    -9.10% |
|                                      99th percentile latency | index-append |     829.374 |     899.85 |  70.4759 |     ms |    +8.50% |
|                                    99.9th percentile latency | index-append |        1117 |    1178.81 |  61.8014 |     ms |    +5.53% |
|                                     100th percentile latency | index-append |     1464.96 |    1741.13 |  276.172 |     ms |   +18.85% |
|                                 50th percentile service time | index-append |     132.692 |    131.345 | -1.34778 |     ms |    -1.02% |
|                                 90th percentile service time | index-append |     183.185 |    166.522 | -16.6626 |     ms |    -9.10% |
|                                 99th percentile service time | index-append |     829.374 |     899.85 |  70.4759 |     ms |    +8.50% |
|                               99.9th percentile service time | index-append |        1117 |    1178.81 |  61.8014 |     ms |    +5.53% |
|                                100th percentile service time | index-append |     1464.96 |    1741.13 |  276.172 |     ms |   +18.85% |
|                                                   error rate | index-append |           0 |          0 |        0 |      % |     0.00% |
|                                               Min Throughput |      polygon |     2.00236 |    2.00234 |   -2e-05 |  ops/s |    -0.00% |
|                                              Mean Throughput |      polygon |     2.00286 |    2.00285 |   -1e-05 |  ops/s |    -0.00% |
|                                            Median Throughput |      polygon |     2.00282 |    2.00281 |   -1e-05 |  ops/s |    -0.00% |
|                                               Max Throughput |      polygon |      2.0035 |     2.0035 |       -0 |  ops/s |    -0.00% |
|                                      50th percentile latency |      polygon |     2.80226 |    2.71863 | -0.08363 |     ms |    -2.98% |
|                                      90th percentile latency |      polygon |     3.20036 |     3.1772 | -0.02316 |     ms |    -0.72% |
|                                      99th percentile latency |      polygon |     3.72818 |       3.32 | -0.40818 |     ms |   -10.95% |
|                                     100th percentile latency |      polygon |     6.29345 |      3.421 | -2.87244 |     ms |   -45.64% |
|                                 50th percentile service time |      polygon |     1.44773 |    1.40477 | -0.04297 |     ms |    -2.97% |
|                                 90th percentile service time |      polygon |     1.61263 |    1.53162 | -0.08101 |     ms |    -5.02% |
|                                 99th percentile service time |      polygon |     2.09091 |    1.64174 | -0.44917 |     ms |   -21.48% |
|                                100th percentile service time |      polygon |     5.33494 |    1.66541 | -3.66953 |     ms |   -68.78% |
|                                                   error rate |      polygon |           0 |          0 |        0 |      % |     0.00% |
|                                               Min Throughput |         bbox |     2.00317 |    2.00266 | -0.00051 |  ops/s |    -0.03% |
|                                              Mean Throughput |         bbox |     2.00384 |    2.00323 | -0.00061 |  ops/s |    -0.03% |
|                                            Median Throughput |         bbox |     2.00379 |    2.00319 | -0.00059 |  ops/s |    -0.03% |
|                                               Max Throughput |         bbox |     2.00471 |    2.00395 | -0.00076 |  ops/s |    -0.04% |
|                                      50th percentile latency |         bbox |     251.597 |    290.117 |  38.5201 |     ms |   +15.31% |
|                                      90th percentile latency |         bbox |     257.059 |    296.768 |  39.7094 |     ms |   +15.45% |
|                                      99th percentile latency |         bbox |     261.814 |    300.701 |  38.8876 |     ms |   +14.85% |
|                                     100th percentile latency |         bbox |     265.411 |    301.303 |  35.8919 |     ms |   +13.52% |
|                                 50th percentile service time |         bbox |     250.521 |    288.776 |  38.2546 |     ms |   +15.27% |
|                                 90th percentile service time |         bbox |     256.254 |      295.7 |  39.4455 |     ms |   +15.39% |
|                                 99th percentile service time |         bbox |     260.837 |    299.764 |  38.9264 |     ms |   +14.92% |
|                                100th percentile service time |         bbox |     264.542 |     300.39 |  35.8483 |     ms |   +13.55% |
|                                                   error rate |         bbox |           0 |          0 |        0 |      % |     0.00% |





# noaa

## 场景介绍

数据量：9.0 GB

场景描述：Global daily weather measurements from NOAA



## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：



# geoshape

## 场景介绍

数据量：58.7 GB

场景描述：Shapes from PlanetOSM



## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：





# http_logs

## 场景介绍

数据量：31.1 GB

场景描述：HTTP server log data



## 性能对比

baseline：SSD，raceid：

contender：PMEM，raceid：bcbdac0a-3042-4baa-b197-ea40dbc3b9fe





# pmc

## 场景介绍

数据量：21.7 GB

场景描述：Full text benchmark with academic papers from PMC



## 性能对比

baseline：SSD，raceid：f40dd7f5-36c0-4aad-af43-d43e9d02125b

contender：PMEM，raceid：03f1191b-b1e1-4b8f-8f6a-3b3e2975f4c9

|                                                       Metric |                          Task |   Baseline |  Contender |     Diff |    Unit |   Diff % |
| -----------------------------------------------------------: | ----------------------------: | ---------: | ---------: | -------: | ------: | -------: |
|                   Cumulative indexing time of primary shards |                               |    435.891 |     561.43 |  125.538 |     min |  +28.80% |
|            Min cumulative indexing time across primary shard |                               |          0 |      4.513 |    4.513 |     min |    0.00% |
|         Median cumulative indexing time across primary shard |                               |    15.6254 |    21.2302 |  5.60476 |     min |  +35.87% |
|            Max cumulative indexing time across primary shard |                               |    165.091 |    194.912 |  29.8216 |     min |  +18.06% |
|          Cumulative indexing throttle time of primary shards |                               |    0.00595 |          0 | -0.00595 |     min | -100.00% |
|   Min cumulative indexing throttle time across primary shard |                               |          0 |          0 |        0 |     min |    0.00% |
| Median cumulative indexing throttle time across primary shard |                               |          0 |          0 |        0 |     min |    0.00% |
|   Max cumulative indexing throttle time across primary shard |                               | 0.00248333 |          0 | -0.00248 |     min | -100.00% |
|                      Cumulative merge time of primary shards |                               |    278.231 |    299.084 |  20.8523 |     min |   +7.49% |
|                     Cumulative merge count of primary shards |                               |       1388 |       1811 |      423 |         |  +30.48% |
|               Min cumulative merge time across primary shard |                               |          0 |    1.53747 |  1.53747 |     min |    0.00% |
|            Median cumulative merge time across primary shard |                               |     8.6569 |    10.5288 |   1.8719 |     min |  +21.62% |
|               Max cumulative merge time across primary shard |                               |    68.6997 |    72.2745 |  3.57472 |     min |   +5.20% |
|             Cumulative merge throttle time of primary shards |                               |    101.022 |    85.3707 | -15.6511 |     min |  -15.49% |
|      Min cumulative merge throttle time across primary shard |                               |          0 |   0.426317 |  0.42632 |     min |    0.00% |
|   Median cumulative merge throttle time across primary shard |                               |    3.44958 |      2.717 | -0.73258 |     min |  -21.24% |
|      Max cumulative merge throttle time across primary shard |                               |    27.2988 |    23.8589 |  -3.4399 |     min |  -12.60% |
|                    Cumulative refresh time of primary shards |                               |    25.8202 |    27.1105 |   1.2903 |     min |   +5.00% |
|                   Cumulative refresh count of primary shards |                               |       2609 |       2947 |      338 |         |  +12.96% |
|             Min cumulative refresh time across primary shard |                               |          0 |  0.0606667 |  0.06067 |     min |    0.00% |
|          Median cumulative refresh time across primary shard |                               |    1.60165 |     1.8445 |  0.24285 |     min |  +15.16% |
|             Max cumulative refresh time across primary shard |                               |    3.18668 |    2.99333 | -0.19335 |     min |   -6.07% |
|                      Cumulative flush time of primary shards |                               |    23.3472 |    4.72145 | -18.6258 |     min |  -79.78% |
|                     Cumulative flush count of primary shards |                               |        205 |        218 |       13 |         |   +6.34% |
|               Min cumulative flush time across primary shard |                               |          0 | 0.00943333 |  0.00943 |     min |    0.00% |
|            Median cumulative flush time across primary shard |                               |    1.22172 |   0.121183 | -1.10053 |     min |  -90.08% |
|               Max cumulative flush time across primary shard |                               |    3.68175 |    2.90753 | -0.77422 |     min |  -21.03% |
|                                      Total Young Gen GC time |                               |      9.357 |      9.685 |    0.328 |       s |   +3.51% |
|                                     Total Young Gen GC count |                               |       2089 |       2175 |       86 |         |   +4.12% |
|                                        Total Old Gen GC time |                               |     58.529 |     103.97 |   45.441 |       s |  +77.64% |
|                                       Total Old Gen GC count |                               |        936 |       1163 |      227 |         |  +24.25% |
|                                                   Store size |                               |    107.724 |    107.914 |  0.18976 |      GB |   +0.18% |
|                                                Translog size |                               |     2.6928 |    3.28258 |  0.58978 |      GB |  +21.90% |
|                                       Heap used for segments |                               |    135.402 |    133.428 | -1.97491 |      MB |   -1.46% |
|                                     Heap used for doc values |                               |   0.165531 |    1.64696 |  1.48143 |      MB | +894.96% |
|                                          Heap used for terms |                               |    102.147 |    98.5572 | -3.58937 |      MB |   -3.51% |
|                                          Heap used for norms |                               |   0.055542 |  0.0564575 |  0.00092 |      MB |   +1.65% |
|                                         Heap used for points |                               |    15.7821 |    15.8879 |  0.10577 |      MB |   +0.67% |
|                                  Heap used for stored fields |                               |    17.2528 |    17.2791 |  0.02634 |      MB |   +0.15% |
|                                                Segment count |                               |        379 |        429 |       50 |         |  +13.19% |
|                                               Min Throughput |                  index-append |     1300.6 |     1342.3 |  41.7035 |  docs/s |   +3.21% |
|                                              Mean Throughput |                  index-append |    1344.17 |    1361.02 |  16.8523 |  docs/s |   +1.25% |
|                                            Median Throughput |                  index-append |    1345.27 |    1359.31 |  14.0387 |  docs/s |   +1.04% |
|                                               Max Throughput |                  index-append |    1372.54 |    1381.83 |  9.28962 |  docs/s |   +0.68% |
|                                      50th percentile latency |                  index-append |    1624.68 |    2681.88 |   1057.2 |      ms |  +65.07% |
|                                      90th percentile latency |                  index-append |    2659.58 |    3627.19 |   967.61 |      ms |  +36.38% |
|                                      99th percentile latency |                  index-append |    3475.51 |    4607.86 |  1132.35 |      ms |  +32.58% |
|                                     100th percentile latency |                  index-append |    4051.05 |    5094.47 |  1043.42 |      ms |  +25.76% |
|                                 50th percentile service time |                  index-append |    1624.68 |    2681.88 |   1057.2 |      ms |  +65.07% |
|                                 90th percentile service time |                  index-append |    2659.58 |    3627.19 |   967.61 |      ms |  +36.38% |
|                                 99th percentile service time |                  index-append |    3475.51 |    4607.86 |  1132.35 |      ms |  +32.58% |
|                                100th percentile service time |                  index-append |    4051.05 |    5094.47 |  1043.42 |      ms |  +25.76% |
|                                                   error rate |                  index-append |     1.0142 |    3.88769 |  2.87349 |       % | +283.33% |
|                                               Min Throughput |                       default |    20.0208 |     20.025 |  0.00415 |   ops/s |   +0.02% |
|                                              Mean Throughput |                       default |    20.0243 |    20.0291 |  0.00472 |   ops/s |   +0.02% |
|                                            Median Throughput |                       default |    20.0243 |    20.0289 |  0.00456 |   ops/s |   +0.02% |
|                                               Max Throughput |                       default |    20.0288 |    20.0341 |  0.00538 |   ops/s |   +0.03% |
|                                      50th percentile latency |                       default |    2.53675 |    3.86445 |  1.32769 |      ms |  +52.34% |
|                                      90th percentile latency |                       default |    2.93778 |    4.28574 |  1.34796 |      ms |  +45.88% |
|                                      99th percentile latency |                       default |    3.13624 |     4.5845 |  1.44826 |      ms |  +46.18% |
|                                     100th percentile latency |                       default |    3.34107 |     4.7164 |  1.37533 |      ms |  +41.16% |
|                                 50th percentile service time |                       default |     1.8188 |    3.09792 |  1.27912 |      ms |  +70.33% |
|                                 90th percentile service time |                       default |    1.92104 |    3.41376 |  1.49272 |      ms |  +77.70% |
|                                 99th percentile service time |                       default |     2.1287 |    3.68064 |  1.55194 |      ms |  +72.91% |
|                                100th percentile service time |                       default |    2.22685 |    4.21977 |  1.99293 |      ms |  +89.50% |
|                                                   error rate |                       default |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                          term |    20.0057 |    20.0015 |  -0.0042 |   ops/s |   -0.02% |
|                                              Mean Throughput |                          term |    20.0063 |    20.0017 | -0.00459 |   ops/s |   -0.02% |
|                                            Median Throughput |                          term |    20.0063 |    20.0017 | -0.00462 |   ops/s |   -0.02% |
|                                               Max Throughput |                          term |    20.0073 |    20.0021 | -0.00519 |   ops/s |   -0.03% |
|                                      50th percentile latency |                          term |    3.42734 |    3.60078 |  0.17344 |      ms |   +5.06% |
|                                      90th percentile latency |                          term |    3.77325 |    4.04357 |  0.27032 |      ms |   +7.16% |
|                                      99th percentile latency |                          term |    6.27626 |    6.44955 |  0.17329 |      ms |   +2.76% |
|                                     100th percentile latency |                          term |    6.47563 |    6.94505 |  0.46942 |      ms |   +7.25% |
|                                 50th percentile service time |                          term |    2.52572 |     2.8176 |  0.29188 |      ms |  +11.56% |
|                                 90th percentile service time |                          term |    2.85199 |    3.20144 |  0.34944 |      ms |  +12.25% |
|                                 99th percentile service time |                          term |    5.50985 |    5.76856 |  0.25871 |      ms |   +4.70% |
|                                100th percentile service time |                          term |    5.69394 |    6.19361 |  0.49968 |      ms |   +8.78% |
|                                                   error rate |                          term |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                        phrase |     20.006 |    19.9581 | -0.04793 |   ops/s |   -0.24% |
|                                              Mean Throughput |                        phrase |     20.007 |     19.964 | -0.04299 |   ops/s |   -0.21% |
|                                            Median Throughput |                        phrase |     20.007 |    19.9644 | -0.04261 |   ops/s |   -0.21% |
|                                               Max Throughput |                        phrase |    20.0079 |    19.9688 | -0.03915 |   ops/s |   -0.20% |
|                                      50th percentile latency |                        phrase |    2.90238 |    2.77708 |  -0.1253 |      ms |   -4.32% |
|                                      90th percentile latency |                        phrase |    3.29733 |      3.181 | -0.11633 |      ms |   -3.53% |
|                                      99th percentile latency |                        phrase |    3.75944 |     3.7213 | -0.03814 |      ms |   -1.01% |
|                                     100th percentile latency |                        phrase |    6.11596 |    6.04164 | -0.07431 |      ms |   -1.22% |
|                                 50th percentile service time |                        phrase |    2.09619 |    1.98507 | -0.11113 |      ms |   -5.30% |
|                                 90th percentile service time |                        phrase |    2.28987 |    2.30409 |  0.01422 |      ms |   +0.62% |
|                                 99th percentile service time |                        phrase |    2.61515 |    2.73541 |  0.12026 |      ms |   +4.60% |
|                                100th percentile service time |                        phrase |    5.36659 |    5.13933 | -0.22726 |      ms |   -4.23% |
|                                                   error rate |                        phrase |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput | articles_monthly_agg_uncached |    20.0073 |    19.9954 | -0.01186 |   ops/s |   -0.06% |
|                                              Mean Throughput | articles_monthly_agg_uncached |    20.0083 |    19.9961 | -0.01213 |   ops/s |   -0.06% |
|                                            Median Throughput | articles_monthly_agg_uncached |    20.0081 |    19.9961 | -0.01197 |   ops/s |   -0.06% |
|                                               Max Throughput | articles_monthly_agg_uncached |    20.0097 |    19.9967 | -0.01301 |   ops/s |   -0.07% |
|                                      50th percentile latency | articles_monthly_agg_uncached |    8.09888 |     8.5684 |  0.46952 |      ms |   +5.80% |
|                                      90th percentile latency | articles_monthly_agg_uncached |    8.46619 |    15.0353 |  6.56914 |      ms |  +77.59% |
|                                      99th percentile latency | articles_monthly_agg_uncached |    8.78318 |    15.9566 |  7.17344 |      ms |  +81.67% |
|                                     100th percentile latency | articles_monthly_agg_uncached |    8.97941 |     16.239 |  7.25957 |      ms |  +80.85% |
|                                 50th percentile service time | articles_monthly_agg_uncached |     7.3448 |     7.7745 |   0.4297 |      ms |   +5.85% |
|                                 90th percentile service time | articles_monthly_agg_uncached |    7.46327 |    14.8023 |  7.33906 |      ms |  +98.34% |
|                                 99th percentile service time | articles_monthly_agg_uncached |    8.21821 |    15.2106 |  6.99238 |      ms |  +85.08% |
|                                100th percentile service time | articles_monthly_agg_uncached |     8.3798 |     15.275 |  6.89518 |      ms |  +82.28% |
|                                                   error rate | articles_monthly_agg_uncached |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |   articles_monthly_agg_cached |    20.0184 |    19.9985 | -0.01994 |   ops/s |   -0.10% |
|                                              Mean Throughput |   articles_monthly_agg_cached |    20.0213 |    19.9989 | -0.02241 |   ops/s |   -0.11% |
|                                            Median Throughput |   articles_monthly_agg_cached |    20.0212 |    19.9988 | -0.02238 |   ops/s |   -0.11% |
|                                               Max Throughput |   articles_monthly_agg_cached |    20.0248 |    19.9992 | -0.02555 |   ops/s |   -0.13% |
|                                      50th percentile latency |   articles_monthly_agg_cached |    1.59634 |    1.53354 |  -0.0628 |      ms |   -3.93% |
|                                      90th percentile latency |   articles_monthly_agg_cached |     1.9499 |    1.93966 | -0.01023 |      ms |   -0.52% |
|                                      99th percentile latency |   articles_monthly_agg_cached |    2.25058 |    2.36976 |  0.11918 |      ms |   +5.30% |
|                                     100th percentile latency |   articles_monthly_agg_cached |    8.11938 |    7.47577 | -0.64361 |      ms |   -7.93% |
|                                 50th percentile service time |   articles_monthly_agg_cached |   0.765857 |    0.77488 |  0.00902 |      ms |   +1.18% |
|                                 90th percentile service time |   articles_monthly_agg_cached |   0.948461 |   0.995661 |   0.0472 |      ms |   +4.98% |
|                                 99th percentile service time |   articles_monthly_agg_cached |    1.29651 |    1.46544 |  0.16892 |      ms |  +13.03% |
|                                100th percentile service time |   articles_monthly_agg_cached |    7.65867 |    7.01183 | -0.64684 |      ms |   -8.45% |
|                                                   error rate |   articles_monthly_agg_cached |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                        scroll |    12.5698 |    12.5686 | -0.00118 | pages/s |   -0.01% |
|                                              Mean Throughput |                        scroll |    12.6149 |     12.613 | -0.00193 | pages/s |   -0.02% |
|                                            Median Throughput |                        scroll |    12.6045 |    12.6027 | -0.00173 | pages/s |   -0.01% |
|                                               Max Throughput |                        scroll |    12.7076 |    12.7041 | -0.00353 | pages/s |   -0.03% |
|                                      50th percentile latency |                        scroll |    220.996 |    211.127 | -9.86955 |      ms |   -4.47% |
|                                      90th percentile latency |                        scroll |    227.845 |    216.002 | -11.8432 |      ms |   -5.20% |
|                                      99th percentile latency |                        scroll |     230.85 |    222.455 |   -8.395 |      ms |   -3.64% |
|                                     100th percentile latency |                        scroll |    231.953 |    226.678 | -5.27523 |      ms |   -2.27% |
|                                 50th percentile service time |                        scroll |    217.814 |    208.015 | -9.79924 |      ms |   -4.50% |
|                                 90th percentile service time |                        scroll |    223.836 |    213.069 | -10.7668 |      ms |   -4.81% |
|                                 99th percentile service time |                        scroll |    228.307 |     218.37 | -9.93711 |      ms |   -4.35% |
|                                100th percentile service time |                        scroll |    228.598 |    222.727 | -5.87136 |      ms |   -2.57% |
|                                                   error rate |                        scroll |          0 |          0 |        0 |       % |    0.00% |



# geonames

## 场景介绍

数据量：3.3 GB

场景描述：POIs from Geonames



## 性能对比

baseline：SSD，raceid：af360426-b334-4fc9-8fbf-548c1719fbe4

contender：PMEM，raceid：dd034827-ce45-4ffe-befe-bc1a523ff83a

|                                                       Metric |                           Task |   Baseline |  Contender |     Diff |    Unit |   Diff % |
| -----------------------------------------------------------: | -----------------------------: | ---------: | ---------: | -------: | ------: | -------: |
|                   Cumulative indexing time of primary shards |                                |    464.135 |     594.75 |  130.615 |     min |  +28.14% |
|            Min cumulative indexing time across primary shard |                                |          0 |      4.513 |    4.513 |     min |    0.00% |
|         Median cumulative indexing time across primary shard |                                |    15.4511 |    21.1383 |  5.68721 |     min |  +36.81% |
|            Max cumulative indexing time across primary shard |                                |    165.091 |    194.912 |  29.8216 |     min |  +18.06% |
|          Cumulative indexing throttle time of primary shards |                                |    0.00595 |          0 | -0.00595 |     min | -100.00% |
|   Min cumulative indexing throttle time across primary shard |                                |          0 |          0 |        0 |     min |    0.00% |
| Median cumulative indexing throttle time across primary shard |                                |          0 |          0 |        0 |     min |    0.00% |
|   Max cumulative indexing throttle time across primary shard |                                | 0.00248333 |          0 | -0.00248 |     min | -100.00% |
|                      Cumulative merge time of primary shards |                                |    288.347 |    310.204 |  21.8569 |     min |   +7.58% |
|                     Cumulative merge count of primary shards |                                |       1523 |       1975 |      452 |         |  +29.68% |
|               Min cumulative merge time across primary shard |                                |          0 |    1.53747 |  1.53747 |     min |    0.00% |
|            Median cumulative merge time across primary shard |                                |     7.6101 |    9.74249 |  2.13239 |     min |  +28.02% |
|               Max cumulative merge time across primary shard |                                |    68.6997 |    72.2745 |  3.57472 |     min |   +5.20% |
|             Cumulative merge throttle time of primary shards |                                |    101.991 |     86.194 | -15.7966 |     min |  -15.49% |
|      Min cumulative merge throttle time across primary shard |                                |          0 |   0.150433 |  0.15043 |     min |    0.00% |
|   Median cumulative merge throttle time across primary shard |                                |    2.66477 |    1.30721 | -1.35756 |     min |  -50.94% |
|      Max cumulative merge throttle time across primary shard |                                |    27.2988 |    23.8589 |  -3.4399 |     min |  -12.60% |
|                    Cumulative refresh time of primary shards |                                |    28.0719 |    29.5672 |  1.49537 |     min |   +5.33% |
|                   Cumulative refresh count of primary shards |                                |       2963 |       3318 |      355 |         |  +11.98% |
|             Min cumulative refresh time across primary shard |                                |          0 |  0.0606667 |  0.06067 |     min |    0.00% |
|          Median cumulative refresh time across primary shard |                                |   0.894467 |   0.645258 | -0.24921 |     min |  -27.86% |
|             Max cumulative refresh time across primary shard |                                |    3.18668 |    2.99333 | -0.19335 |     min |   -6.07% |
|                      Cumulative flush time of primary shards |                                |    23.7128 |    4.77152 | -18.9413 |     min |  -79.88% |
|                     Cumulative flush count of primary shards |                                |        215 |        228 |       13 |         |   +6.05% |
|               Min cumulative flush time across primary shard |                                |          0 | 0.00676667 |  0.00677 |     min |    0.00% |
|            Median cumulative flush time across primary shard |                                |   0.931783 |   0.100008 | -0.83178 |     min |  -89.27% |
|               Max cumulative flush time across primary shard |                                |    3.68175 |    2.90753 | -0.77422 |     min |  -21.03% |
|                                      Total Young Gen GC time |                                |     19.038 |     20.077 |    1.039 |       s |   +5.46% |
|                                     Total Young Gen GC count |                                |       5929 |       6035 |      106 |         |   +1.79% |
|                                        Total Old Gen GC time |                                |      9.121 |      9.595 |    0.474 |       s |   +5.20% |
|                                       Total Old Gen GC count |                                |        261 |        276 |       15 |         |   +5.75% |
|                                                   Store size |                                |    110.925 |    111.133 |  0.20756 |      GB |   +0.19% |
|                                                Translog size |                                |    5.48505 |    6.07461 |  0.58955 |      GB |  +10.75% |
|                                       Heap used for segments |                                |    141.236 |    139.006 |  -2.2303 |      MB |   -1.58% |
|                                     Heap used for doc values |                                |   0.207363 |    1.68506 |   1.4777 |      MB | +712.61% |
|                                          Heap used for terms |                                |    106.817 |    102.983 | -3.83459 |      MB |   -3.59% |
|                                          Heap used for norms |                                |   0.132324 |   0.127502 | -0.00482 |      MB |   -3.64% |
|                                         Heap used for points |                                |    16.0425 |    16.1551 |  0.11264 |      MB |   +0.70% |
|                                  Heap used for stored fields |                                |    18.0369 |    18.0557 |  0.01878 |      MB |   +0.10% |
|                                                Segment count |                                |        479 |        520 |       41 |         |   +8.56% |
|                                               Min Throughput |                   index-append |    84882.7 |    86744.7 |  1862.07 |  docs/s |   +2.19% |
|                                              Mean Throughput |                   index-append |    87489.7 |    87059.8 | -429.926 |  docs/s |   -0.49% |
|                                            Median Throughput |                   index-append |    88192.4 |    87004.6 | -1187.82 |  docs/s |   -1.35% |
|                                               Max Throughput |                   index-append |      88915 |    87664.6 | -1250.46 |  docs/s |   -1.41% |
|                                      50th percentile latency |                   index-append |    410.634 |    404.557 | -6.07616 |      ms |   -1.48% |
|                                      90th percentile latency |                   index-append |    837.184 |    782.597 | -54.5872 |      ms |   -6.52% |
|                                      99th percentile latency |                   index-append |    1787.15 |    1026.63 | -760.521 |      ms |  -42.55% |
|                                     100th percentile latency |                   index-append |    2052.02 |    1089.27 | -962.745 |      ms |  -46.92% |
|                                 50th percentile service time |                   index-append |    410.634 |    404.557 | -6.07616 |      ms |   -1.48% |
|                                 90th percentile service time |                   index-append |    837.184 |    782.597 | -54.5872 |      ms |   -6.52% |
|                                 99th percentile service time |                   index-append |    1787.15 |    1026.63 | -760.521 |      ms |  -42.55% |
|                                100th percentile service time |                   index-append |    2052.02 |    1089.27 | -962.745 |      ms |  -46.92% |
|                                                   error rate |                   index-append |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                    index-stats |    90.0078 |    90.0038 | -0.00407 |   ops/s |   -0.00% |
|                                              Mean Throughput |                    index-stats |    90.0135 |    90.0096 | -0.00387 |   ops/s |   -0.00% |
|                                            Median Throughput |                    index-stats |    90.0129 |    90.0091 | -0.00375 |   ops/s |   -0.00% |
|                                               Max Throughput |                    index-stats |    90.0251 |    90.0176 | -0.00754 |   ops/s |   -0.01% |
|                                      50th percentile latency |                    index-stats |    3.39531 |    4.08475 |  0.68943 |      ms |  +20.31% |
|                                      90th percentile latency |                    index-stats |    3.79742 |    4.51158 |  0.71416 |      ms |  +18.81% |
|                                      99th percentile latency |                    index-stats |    3.98059 |    5.05355 |  1.07296 |      ms |  +26.95% |
|                                    99.9th percentile latency |                    index-stats |    7.21446 |    11.9776 |  4.76309 |      ms |  +66.02% |
|                                     100th percentile latency |                    index-stats |    10.9481 |     18.341 |  7.39298 |      ms |  +67.53% |
|                                 50th percentile service time |                    index-stats |    2.67073 |    3.37727 |  0.70655 |      ms |  +26.46% |
|                                 90th percentile service time |                    index-stats |    2.79589 |    3.51846 |  0.72257 |      ms |  +25.84% |
|                                 99th percentile service time |                    index-stats |    3.01776 |    4.06014 |  1.04237 |      ms |  +34.54% |
|                               99.9th percentile service time |                    index-stats |    6.03443 |    6.82901 |  0.79459 |      ms |  +13.17% |
|                                100th percentile service time |                    index-stats |    10.2192 |    17.4955 |  7.27633 |      ms |  +71.20% |
|                                                   error rate |                    index-stats |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                     node-stats |    89.9986 |    89.9908 | -0.00785 |   ops/s |   -0.01% |
|                                              Mean Throughput |                     node-stats |    90.0221 |    89.9979 | -0.02418 |   ops/s |   -0.03% |
|                                            Median Throughput |                     node-stats |    90.0178 |    89.9985 | -0.01934 |   ops/s |   -0.02% |
|                                               Max Throughput |                     node-stats |     90.064 |    90.0034 | -0.06053 |   ops/s |   -0.07% |
|                                      50th percentile latency |                     node-stats |    3.39002 |    3.99078 |  0.60077 |      ms |  +17.72% |
|                                      90th percentile latency |                     node-stats |    3.96837 |    4.40429 |  0.43592 |      ms |  +10.98% |
|                                      99th percentile latency |                     node-stats |    4.96472 |    5.43521 |  0.47048 |      ms |   +9.48% |
|                                    99.9th percentile latency |                     node-stats |    6.62292 |    10.7279 |  4.10495 |      ms |  +61.98% |
|                                     100th percentile latency |                     node-stats |    9.80779 |    15.5592 |  5.75141 |      ms |  +58.64% |
|                                 50th percentile service time |                     node-stats |    2.61169 |    3.26491 |  0.65322 |      ms |  +25.01% |
|                                 90th percentile service time |                     node-stats |    2.79657 |    3.43135 |  0.63479 |      ms |  +22.70% |
|                                 99th percentile service time |                     node-stats |    3.92038 |    4.63376 |  0.71338 |      ms |  +18.20% |
|                               99.9th percentile service time |                     node-stats |    5.70945 |    6.44278 |  0.73333 |      ms |  +12.84% |
|                                100th percentile service time |                     node-stats |    8.88433 |    14.9031 |  6.01874 |      ms |  +67.75% |
|                                                   error rate |                     node-stats |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                        default |    50.0255 |    50.0266 |  0.00109 |   ops/s |    0.00% |
|                                              Mean Throughput |                        default |    50.0433 |    50.0438 |  0.00048 |   ops/s |    0.00% |
|                                            Median Throughput |                        default |    50.0403 |    50.0393 | -0.00096 |   ops/s |   -0.00% |
|                                               Max Throughput |                        default |    50.0783 |    50.0763 | -0.00199 |   ops/s |   -0.00% |
|                                      50th percentile latency |                        default |    1.56718 |    1.49502 | -0.07216 |      ms |   -4.60% |
|                                      90th percentile latency |                        default |    2.09285 |    1.89796 | -0.19489 |      ms |   -9.31% |
|                                      99th percentile latency |                        default |    2.79775 |     2.4574 | -0.34035 |      ms |  -12.17% |
|                                    99.9th percentile latency |                        default |    2.99643 |    2.72359 | -0.27284 |      ms |   -9.11% |
|                                     100th percentile latency |                        default |    8.27205 |    10.0516 |  1.77956 |      ms |  +21.51% |
|                                 50th percentile service time |                        default |   0.684974 |   0.676338 | -0.00864 |      ms |   -1.26% |
|                                 90th percentile service time |                        default |   0.753556 |   0.735665 | -0.01789 |      ms |   -2.37% |
|                                 99th percentile service time |                        default |   0.880597 |   0.811747 | -0.06885 |      ms |   -7.82% |
|                               99.9th percentile service time |                        default |    1.54007 |    2.11844 |  0.57838 |      ms |  +37.56% |
|                                100th percentile service time |                        default |    7.27577 |    8.90087 |   1.6251 |      ms |  +22.34% |
|                                                   error rate |                        default |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                           term |     100.03 |    100.026 | -0.00361 |   ops/s |   -0.00% |
|                                              Mean Throughput |                           term |    100.046 |    100.044 | -0.00271 |   ops/s |   -0.00% |
|                                            Median Throughput |                           term |    100.044 |    100.034 | -0.01003 |   ops/s |   -0.01% |
|                                               Max Throughput |                           term |    100.064 |    100.074 |  0.01002 |   ops/s |   +0.01% |
|                                      50th percentile latency |                           term |    2.00248 |    2.01842 |  0.01593 |      ms |   +0.80% |
|                                      90th percentile latency |                           term |    2.87164 |    2.87411 |  0.00247 |      ms |   +0.09% |
|                                      99th percentile latency |                           term |    3.11928 |    3.11612 | -0.00316 |      ms |   -0.10% |
|                                    99.9th percentile latency |                           term |    6.13315 |    6.17263 |  0.03947 |      ms |   +0.64% |
|                                     100th percentile latency |                           term |    6.32045 |     6.1828 | -0.13765 |      ms |   -2.18% |
|                                 50th percentile service time |                           term |   0.882172 |   0.883649 |  0.00148 |      ms |   +0.17% |
|                                 90th percentile service time |                           term |   0.956405 |    0.96367 |  0.00726 |      ms |   +0.76% |
|                                 99th percentile service time |                           term |    1.30342 |    1.23537 | -0.06806 |      ms |   -5.22% |
|                               99.9th percentile service time |                           term |    4.48027 |    4.41738 |  -0.0629 |      ms |   -1.40% |
|                                100th percentile service time |                           term |    5.81042 |    4.51031 | -1.30011 |      ms |  -22.38% |
|                                                   error rate |                           term |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                         phrase |    110.039 |     110.03 | -0.00856 |   ops/s |   -0.01% |
|                                              Mean Throughput |                         phrase |     110.06 |    110.051 | -0.00935 |   ops/s |   -0.01% |
|                                            Median Throughput |                         phrase |    110.053 |    110.042 | -0.01048 |   ops/s |   -0.01% |
|                                               Max Throughput |                         phrase |    110.098 |    110.093 | -0.00531 |   ops/s |   -0.00% |
|                                      50th percentile latency |                         phrase |    1.64266 |    1.66845 |  0.02579 |      ms |   +1.57% |
|                                      90th percentile latency |                         phrase |    2.04388 |    2.07642 |  0.03254 |      ms |   +1.59% |
|                                      99th percentile latency |                         phrase |    2.22038 |     2.3208 |  0.10042 |      ms |   +4.52% |
|                                    99.9th percentile latency |                         phrase |    5.30021 |    4.98887 | -0.31134 |      ms |   -5.87% |
|                                     100th percentile latency |                         phrase |    8.69175 |     5.3706 | -3.32115 |      ms |  -38.21% |
|                                 50th percentile service time |                         phrase |   0.933463 |   0.972055 |  0.03859 |      ms |   +4.13% |
|                                 90th percentile service time |                         phrase |   0.998397 |    1.04536 |  0.04697 |      ms |   +4.70% |
|                                 99th percentile service time |                         phrase |    1.23862 |    1.29991 |  0.06129 |      ms |   +4.95% |
|                               99.9th percentile service time |                         phrase |    4.26532 |    4.25102 | -0.01431 |      ms |   -0.34% |
|                                100th percentile service time |                         phrase |    7.82432 |    4.29525 | -3.52907 |      ms |  -45.10% |
|                                                   error rate |                         phrase |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |           country_agg_uncached |     2.9914 |     2.9912 | -0.00021 |   ops/s |   -0.01% |
|                                              Mean Throughput |           country_agg_uncached |    2.99302 |    2.99283 | -0.00019 |   ops/s |   -0.01% |
|                                            Median Throughput |           country_agg_uncached |     2.9931 |    2.99294 | -0.00016 |   ops/s |   -0.01% |
|                                               Max Throughput |           country_agg_uncached |    2.99427 |    2.99406 |  -0.0002 |   ops/s |   -0.01% |
|                                      50th percentile latency |           country_agg_uncached |    186.582 |     188.36 |  1.77765 |      ms |   +0.95% |
|                                      90th percentile latency |           country_agg_uncached |    190.951 |    191.942 |  0.99176 |      ms |   +0.52% |
|                                      99th percentile latency |           country_agg_uncached |    240.133 |    198.247 |  -41.886 |      ms |  -17.44% |
|                                     100th percentile latency |           country_agg_uncached |    242.109 |    210.361 | -31.7475 |      ms |  -13.11% |
|                                 50th percentile service time |           country_agg_uncached |     185.41 |    187.305 |   1.8943 |      ms |   +1.02% |
|                                 90th percentile service time |           country_agg_uncached |    190.008 |    190.152 |  0.14455 |      ms |   +0.08% |
|                                 99th percentile service time |           country_agg_uncached |    238.882 |     196.98 | -41.9017 |      ms |  -17.54% |
|                                100th percentile service time |           country_agg_uncached |    240.043 |    209.925 | -30.1183 |      ms |  -12.55% |
|                                                   error rate |           country_agg_uncached |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |             country_agg_cached |    98.3248 |    98.2338 | -0.09103 |   ops/s |   -0.09% |
|                                              Mean Throughput |             country_agg_cached |    98.7701 |    98.7416 | -0.02848 |   ops/s |   -0.03% |
|                                            Median Throughput |             country_agg_cached |    98.8137 |    98.7977 | -0.01609 |   ops/s |   -0.02% |
|                                               Max Throughput |             country_agg_cached |    99.0847 |    99.0975 |  0.01281 |   ops/s |   +0.01% |
|                                      50th percentile latency |             country_agg_cached |    1.84708 |    1.85105 |  0.00397 |      ms |   +0.22% |
|                                      90th percentile latency |             country_agg_cached |    2.63676 |     2.6695 |  0.03274 |      ms |   +1.24% |
|                                      99th percentile latency |             country_agg_cached |    2.85419 |    2.84484 | -0.00935 |      ms |   -0.33% |
|                                    99.9th percentile latency |             country_agg_cached |    3.07796 |    3.01011 | -0.06786 |      ms |   -2.20% |
|                                     100th percentile latency |             country_agg_cached |     9.8443 |    8.83407 | -1.01023 |      ms |  -10.26% |
|                                 50th percentile service time |             country_agg_cached |   0.643087 |   0.647596 |  0.00451 |      ms |   +0.70% |
|                                 90th percentile service time |             country_agg_cached |   0.696483 |   0.682781 |  -0.0137 |      ms |   -1.97% |
|                                 99th percentile service time |             country_agg_cached |    0.80015 |   0.763376 | -0.03677 |      ms |   -4.60% |
|                               99.9th percentile service time |             country_agg_cached |    1.38593 |    1.85853 |   0.4726 |      ms |  +34.10% |
|                                100th percentile service time |             country_agg_cached |    8.97959 |    7.80155 | -1.17804 |      ms |  -13.12% |
|                                                   error rate |             country_agg_cached |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                         scroll |    20.0523 |    20.0525 |  0.00019 | pages/s |    0.00% |
|                                              Mean Throughput |                         scroll |    20.0636 |    20.0638 |  0.00027 | pages/s |    0.00% |
|                                            Median Throughput |                         scroll |    20.0627 |     20.063 |  0.00028 | pages/s |    0.00% |
|                                               Max Throughput |                         scroll |    20.0782 |    20.0785 |  0.00033 | pages/s |    0.00% |
|                                      50th percentile latency |                         scroll |    276.985 |    254.796 |  -22.189 |      ms |   -8.01% |
|                                      90th percentile latency |                         scroll |     286.01 |    261.511 | -24.4997 |      ms |   -8.57% |
|                                      99th percentile latency |                         scroll |    291.108 |    263.937 | -27.1714 |      ms |   -9.33% |
|                                     100th percentile latency |                         scroll |    296.175 |    264.568 | -31.6067 |      ms |  -10.67% |
|                                 50th percentile service time |                         scroll |    274.902 |    252.636 | -22.2659 |      ms |   -8.10% |
|                                 90th percentile service time |                         scroll |    283.639 |    259.399 | -24.2403 |      ms |   -8.55% |
|                                 99th percentile service time |                         scroll |    289.225 |     262.12 | -27.1057 |      ms |   -9.37% |
|                                100th percentile service time |                         scroll |    294.125 |    262.518 |  -31.607 |      ms |  -10.75% |
|                                                   error rate |                         scroll |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                     expression |    1.50089 |    1.50089 |       -0 |   ops/s |   -0.00% |
|                                              Mean Throughput |                     expression |    1.50108 |    1.50108 |       -0 |   ops/s |   -0.00% |
|                                            Median Throughput |                     expression |    1.50107 |    1.50107 |       -0 |   ops/s |   -0.00% |
|                                               Max Throughput |                     expression |    1.50133 |    1.50132 |       -0 |   ops/s |   -0.00% |
|                                      50th percentile latency |                     expression |     352.75 |    352.708 | -0.04194 |      ms |   -0.01% |
|                                      90th percentile latency |                     expression |    356.834 |    359.491 |  2.65695 |      ms |   +0.74% |
|                                      99th percentile latency |                     expression |    361.466 |    374.874 |  13.4075 |      ms |   +3.71% |
|                                     100th percentile latency |                     expression |    361.565 |    374.905 |  13.3391 |      ms |   +3.69% |
|                                 50th percentile service time |                     expression |    351.544 |    351.624 |  0.07995 |      ms |   +0.02% |
|                                 90th percentile service time |                     expression |    356.067 |    358.155 |  2.08766 |      ms |   +0.59% |
|                                 99th percentile service time |                     expression |    359.778 |    373.811 |  14.0332 |      ms |   +3.90% |
|                                100th percentile service time |                     expression |     360.01 |    373.813 |  13.8034 |      ms |   +3.83% |
|                                                   error rate |                     expression |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                painless_static |    1.25219 |    1.17396 | -0.07823 |   ops/s |   -6.25% |
|                                              Mean Throughput |                painless_static |    1.25443 |    1.17688 | -0.07755 |   ops/s |   -6.18% |
|                                            Median Throughput |                painless_static |    1.25455 |    1.17704 | -0.07751 |   ops/s |   -6.18% |
|                                               Max Throughput |                painless_static |    1.25691 |    1.17946 | -0.07745 |   ops/s |   -6.16% |
|                                      50th percentile latency |                painless_static |    21217.9 |    34649.4 |  13431.5 |      ms |  +63.30% |
|                                      90th percentile latency |                painless_static |    25021.9 |    40548.1 |  15526.2 |      ms |  +62.05% |
|                                      99th percentile latency |                painless_static |    25734.6 |    41727.5 |  15992.9 |      ms |  +62.15% |
|                                     100th percentile latency |                painless_static |    25843.9 |    41855.6 |  16011.7 |      ms |  +61.96% |
|                                 50th percentile service time |                painless_static |    801.458 |    853.387 |  51.9288 |      ms |   +6.48% |
|                                 90th percentile service time |                painless_static |    853.636 |    909.843 |  56.2076 |      ms |   +6.58% |
|                                 99th percentile service time |                painless_static |     909.25 |    954.882 |  45.6321 |      ms |   +5.02% |
|                                100th percentile service time |                painless_static |    909.998 |    960.054 |  50.0558 |      ms |   +5.50% |
|                                                   error rate |                painless_static |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |               painless_dynamic |    1.40018 |    1.39996 | -0.00021 |   ops/s |   -0.02% |
|                                              Mean Throughput |               painless_dynamic |    1.40061 |    1.40051 |  -0.0001 |   ops/s |   -0.01% |
|                                            Median Throughput |               painless_dynamic |    1.40061 |    1.40053 |   -9e-05 |   ops/s |   -0.01% |
|                                               Max Throughput |               painless_dynamic |    1.40077 |    1.40068 |   -9e-05 |   ops/s |   -0.01% |
|                                      50th percentile latency |               painless_dynamic |    623.385 |     641.68 |  18.2949 |      ms |   +2.93% |
|                                      90th percentile latency |               painless_dynamic |    695.442 |    724.759 |  29.3168 |      ms |   +4.22% |
|                                      99th percentile latency |               painless_dynamic |    755.879 |    777.087 |  21.2077 |      ms |   +2.81% |
|                                     100th percentile latency |               painless_dynamic |    770.827 |     788.52 |  17.6924 |      ms |   +2.30% |
|                                 50th percentile service time |               painless_dynamic |    620.218 |    633.025 |  12.8076 |      ms |   +2.07% |
|                                 90th percentile service time |               painless_dynamic |    694.167 |    723.424 |  29.2565 |      ms |   +4.21% |
|                                 99th percentile service time |               painless_dynamic |    755.398 |    776.061 |  20.6629 |      ms |   +2.74% |
|                                100th percentile service time |               painless_dynamic |    770.305 |    787.777 |  17.4727 |      ms |   +2.27% |
|                                                   error rate |               painless_dynamic |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput | decay_geo_gauss_function_score |    1.00092 |     1.0016 |  0.00068 |   ops/s |   +0.07% |
|                                              Mean Throughput | decay_geo_gauss_function_score |    1.00112 |    1.00194 |  0.00082 |   ops/s |   +0.08% |
|                                            Median Throughput | decay_geo_gauss_function_score |     1.0011 |    1.00191 |  0.00081 |   ops/s |   +0.08% |
|                                               Max Throughput | decay_geo_gauss_function_score |    1.00138 |    1.00239 |  0.00101 |   ops/s |   +0.10% |
|                                      50th percentile latency | decay_geo_gauss_function_score |    496.074 |     497.24 |  1.16649 |      ms |   +0.24% |
|                                      90th percentile latency | decay_geo_gauss_function_score |    500.003 |    501.777 |  1.77393 |      ms |   +0.35% |
|                                      99th percentile latency | decay_geo_gauss_function_score |    514.792 |     512.64 | -2.15176 |      ms |   -0.42% |
|                                     100th percentile latency | decay_geo_gauss_function_score |     516.66 |     516.48 | -0.17994 |      ms |   -0.03% |
|                                 50th percentile service time | decay_geo_gauss_function_score |    494.684 |    495.928 |  1.24445 |      ms |   +0.25% |
|                                 90th percentile service time | decay_geo_gauss_function_score |    498.651 |    500.434 |  1.78359 |      ms |   +0.36% |
|                                 99th percentile service time | decay_geo_gauss_function_score |    513.848 |    511.506 |  -2.3419 |      ms |   -0.46% |
|                                100th percentile service time | decay_geo_gauss_function_score |    515.753 |    515.144 | -0.60857 |      ms |   -0.12% |
|                                                   error rate | decay_geo_gauss_function_score |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |   decay_geo_gauss_script_score |    1.00126 |     1.0012 |   -5e-05 |   ops/s |   -0.01% |
|                                              Mean Throughput |   decay_geo_gauss_script_score |    1.00153 |    1.00147 |   -6e-05 |   ops/s |   -0.01% |
|                                            Median Throughput |   decay_geo_gauss_script_score |    1.00151 |    1.00144 |   -6e-05 |   ops/s |   -0.01% |
|                                               Max Throughput |   decay_geo_gauss_script_score |    1.00188 |    1.00181 |   -8e-05 |   ops/s |   -0.01% |
|                                      50th percentile latency |   decay_geo_gauss_script_score |    583.329 |    599.803 |  16.4748 |      ms |   +2.82% |
|                                      90th percentile latency |   decay_geo_gauss_script_score |    613.771 |    630.201 |  16.4305 |      ms |   +2.68% |
|                                      99th percentile latency |   decay_geo_gauss_script_score |    636.643 |    657.694 |  21.0511 |      ms |   +3.31% |
|                                     100th percentile latency |   decay_geo_gauss_script_score |    665.836 |    664.569 | -1.26661 |      ms |   -0.19% |
|                                 50th percentile service time |   decay_geo_gauss_script_score |    582.195 |    598.282 |  16.0868 |      ms |   +2.76% |
|                                 90th percentile service time |   decay_geo_gauss_script_score |      612.8 |    628.513 |  15.7123 |      ms |   +2.56% |
|                                 99th percentile service time |   decay_geo_gauss_script_score |    635.594 |    656.681 |  21.0868 |      ms |   +3.32% |
|                                100th percentile service time |   decay_geo_gauss_script_score |    664.988 |    662.499 | -2.48903 |      ms |   -0.37% |
|                                                   error rate |   decay_geo_gauss_script_score |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |     field_value_function_score |     1.5038 |    1.50378 |   -2e-05 |   ops/s |   -0.00% |
|                                              Mean Throughput |     field_value_function_score |    1.50462 |     1.5046 |   -2e-05 |   ops/s |   -0.00% |
|                                            Median Throughput |     field_value_function_score |    1.50456 |    1.50453 |   -3e-05 |   ops/s |   -0.00% |
|                                               Max Throughput |     field_value_function_score |    1.50568 |    1.50565 |   -3e-05 |   ops/s |   -0.00% |
|                                      50th percentile latency |     field_value_function_score |    150.673 |    152.826 |  2.15236 |      ms |   +1.43% |
|                                      90th percentile latency |     field_value_function_score |    154.447 |    156.122 |  1.67531 |      ms |   +1.08% |
|                                      99th percentile latency |     field_value_function_score |    156.616 |    161.801 |  5.18484 |      ms |   +3.31% |
|                                     100th percentile latency |     field_value_function_score |    180.107 |    170.059 | -10.0481 |      ms |   -5.58% |
|                                 50th percentile service time |     field_value_function_score |    149.289 |    151.564 |  2.27506 |      ms |   +1.52% |
|                                 90th percentile service time |     field_value_function_score |    153.044 |    154.742 |  1.69806 |      ms |   +1.11% |
|                                 99th percentile service time |     field_value_function_score |    155.405 |    160.675 |  5.27073 |      ms |   +3.39% |
|                                100th percentile service time |     field_value_function_score |    178.769 |    168.609 | -10.1605 |      ms |   -5.68% |
|                                                   error rate |     field_value_function_score |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |       field_value_script_score |    1.50288 |    1.50237 | -0.00051 |   ops/s |   -0.03% |
|                                              Mean Throughput |       field_value_script_score |    1.50351 |    1.50287 | -0.00063 |   ops/s |   -0.04% |
|                                            Median Throughput |       field_value_script_score |    1.50346 |    1.50283 | -0.00063 |   ops/s |   -0.04% |
|                                               Max Throughput |       field_value_script_score |    1.50431 |    1.50352 | -0.00079 |   ops/s |   -0.05% |
|                                      50th percentile latency |       field_value_script_score |    234.346 |    310.019 |  75.6735 |      ms |  +32.29% |
|                                      90th percentile latency |       field_value_script_score |     238.74 |    316.901 |  78.1609 |      ms |  +32.74% |
|                                      99th percentile latency |       field_value_script_score |    272.463 |    323.179 |  50.7162 |      ms |  +18.61% |
|                                     100th percentile latency |       field_value_script_score |     303.27 |    342.303 |   39.033 |      ms |  +12.87% |
|                                 50th percentile service time |       field_value_script_score |    232.907 |     308.89 |  75.9829 |      ms |  +32.62% |
|                                 90th percentile service time |       field_value_script_score |    237.494 |    315.641 |  78.1468 |      ms |  +32.90% |
|                                 99th percentile service time |       field_value_script_score |    270.649 |    321.726 |  51.0767 |      ms |  +18.87% |
|                                100th percentile service time |       field_value_script_score |     302.45 |     341.27 |  38.8199 |      ms |  +12.84% |
|                                                   error rate |       field_value_script_score |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |                    large_terms |    1.09933 |     1.0988 | -0.00053 |   ops/s |   -0.05% |
|                                              Mean Throughput |                    large_terms |    1.09945 |    1.09901 | -0.00044 |   ops/s |   -0.04% |
|                                            Median Throughput |                    large_terms |    1.09946 |    1.09903 | -0.00043 |   ops/s |   -0.04% |
|                                               Max Throughput |                    large_terms |    1.09955 |    1.09918 | -0.00037 |   ops/s |   -0.03% |
|                                      50th percentile latency |                    large_terms |    734.414 |      765.4 |  30.9859 |      ms |   +4.22% |
|                                      90th percentile latency |                    large_terms |    737.941 |    769.276 |  31.3357 |      ms |   +4.25% |
|                                      99th percentile latency |                    large_terms |    751.786 |    782.808 |  31.0217 |      ms |   +4.13% |
|                                     100th percentile latency |                    large_terms |    752.938 |    787.569 |  34.6315 |      ms |   +4.60% |
|                                 50th percentile service time |                    large_terms |    727.121 |    758.273 |  31.1518 |      ms |   +4.28% |
|                                 90th percentile service time |                    large_terms |    730.544 |    762.021 |  31.4768 |      ms |   +4.31% |
|                                 99th percentile service time |                    large_terms |    745.464 |     775.21 |  29.7458 |      ms |   +3.99% |
|                                100th percentile service time |                    large_terms |    746.258 |    780.058 |  33.7997 |      ms |   +4.53% |
|                                                   error rate |                    large_terms |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |           large_filtered_terms |     1.1006 |    1.10016 | -0.00044 |   ops/s |   -0.04% |
|                                              Mean Throughput |           large_filtered_terms |    1.10073 |     1.1002 | -0.00053 |   ops/s |   -0.05% |
|                                            Median Throughput |           large_filtered_terms |    1.10072 |     1.1002 | -0.00052 |   ops/s |   -0.05% |
|                                               Max Throughput |           large_filtered_terms |    1.10089 |    1.10024 | -0.00065 |   ops/s |   -0.06% |
|                                      50th percentile latency |           large_filtered_terms |    739.586 |    774.617 |  35.0311 |      ms |   +4.74% |
|                                      90th percentile latency |           large_filtered_terms |    744.086 |    779.194 |  35.1084 |      ms |   +4.72% |
|                                      99th percentile latency |           large_filtered_terms |    757.094 |    798.078 |  40.9837 |      ms |   +5.41% |
|                                     100th percentile latency |           large_filtered_terms |    783.035 |    813.893 |  30.8584 |      ms |   +3.94% |
|                                 50th percentile service time |           large_filtered_terms |    733.217 |    767.755 |  34.5374 |      ms |   +4.71% |
|                                 90th percentile service time |           large_filtered_terms |     737.45 |    772.049 |  34.5992 |      ms |   +4.69% |
|                                 99th percentile service time |           large_filtered_terms |    750.355 |    792.001 |  41.6461 |      ms |   +5.55% |
|                                100th percentile service time |           large_filtered_terms |    776.205 |    806.663 |  30.4578 |      ms |   +3.92% |
|                                                   error rate |           large_filtered_terms |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |         large_prohibited_terms |    1.10068 |    1.10055 | -0.00013 |   ops/s |   -0.01% |
|                                              Mean Throughput |         large_prohibited_terms |    1.10082 |    1.10067 | -0.00015 |   ops/s |   -0.01% |
|                                            Median Throughput |         large_prohibited_terms |    1.10081 |    1.10066 | -0.00015 |   ops/s |   -0.01% |
|                                               Max Throughput |         large_prohibited_terms |    1.10101 |    1.10082 | -0.00019 |   ops/s |   -0.02% |
|                                      50th percentile latency |         large_prohibited_terms |    734.567 |    756.275 |  21.7076 |      ms |   +2.96% |
|                                      90th percentile latency |         large_prohibited_terms |    738.658 |     760.84 |  22.1813 |      ms |   +3.00% |
|                                      99th percentile latency |         large_prohibited_terms |    754.927 |    781.346 |  26.4187 |      ms |   +3.50% |
|                                     100th percentile latency |         large_prohibited_terms |    760.085 |    793.403 |  33.3181 |      ms |   +4.38% |
|                                 50th percentile service time |         large_prohibited_terms |     727.58 |     749.57 |  21.9902 |      ms |   +3.02% |
|                                 90th percentile service time |         large_prohibited_terms |    731.214 |    754.429 |  23.2156 |      ms |   +3.17% |
|                                 99th percentile service time |         large_prohibited_terms |    747.017 |    775.279 |  28.2623 |      ms |   +3.78% |
|                                100th percentile service time |         large_prohibited_terms |    751.939 |    787.138 |  35.1997 |      ms |   +4.68% |
|                                                   error rate |         large_prohibited_terms |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |           desc_sort_population |    1.50439 |     1.5026 | -0.00178 |   ops/s |   -0.12% |
|                                              Mean Throughput |           desc_sort_population |    1.50533 |    1.50317 | -0.00216 |   ops/s |   -0.14% |
|                                            Median Throughput |           desc_sort_population |    1.50527 |    1.50313 | -0.00214 |   ops/s |   -0.14% |
|                                               Max Throughput |           desc_sort_population |    1.50656 |     1.5039 | -0.00266 |   ops/s |   -0.18% |
|                                      50th percentile latency |           desc_sort_population |    42.2008 |     41.866 | -0.33485 |      ms |   -0.79% |
|                                      90th percentile latency |           desc_sort_population |    44.8212 |    43.6643 | -1.15689 |      ms |   -2.58% |
|                                      99th percentile latency |           desc_sort_population |    47.3565 |    64.9469 |  17.5905 |      ms |  +37.14% |
|                                     100th percentile latency |           desc_sort_population |    47.9054 |    65.1781 |  17.2728 |      ms |  +36.06% |
|                                 50th percentile service time |           desc_sort_population |     40.778 |    40.4238 | -0.35427 |      ms |   -0.87% |
|                                 90th percentile service time |           desc_sort_population |     43.156 |    42.0948 | -1.06122 |      ms |   -2.46% |
|                                 99th percentile service time |           desc_sort_population |    45.8899 |    63.0343 |  17.1444 |      ms |  +37.36% |
|                                100th percentile service time |           desc_sort_population |    46.8068 |    63.7051 |  16.8983 |      ms |  +36.10% |
|                                                   error rate |           desc_sort_population |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |            asc_sort_population |    1.50468 |    1.50466 |   -1e-05 |   ops/s |   -0.00% |
|                                              Mean Throughput |            asc_sort_population |    1.50569 |    1.50568 |   -1e-05 |   ops/s |   -0.00% |
|                                            Median Throughput |            asc_sort_population |    1.50562 |     1.5056 |   -2e-05 |   ops/s |   -0.00% |
|                                               Max Throughput |            asc_sort_population |    1.50699 |    1.50697 |   -2e-05 |   ops/s |   -0.00% |
|                                      50th percentile latency |            asc_sort_population |    43.8056 |    42.7532 | -1.05249 |      ms |   -2.40% |
|                                      90th percentile latency |            asc_sort_population |    46.1782 |    44.3065 | -1.87166 |      ms |   -4.05% |
|                                      99th percentile latency |            asc_sort_population |    52.6435 |    47.0833 | -5.56024 |      ms |  -10.56% |
|                                     100th percentile latency |            asc_sort_population |    58.3438 |    47.8503 | -10.4935 |      ms |  -17.99% |
|                                 50th percentile service time |            asc_sort_population |    42.3025 |    41.2659 | -1.03663 |      ms |   -2.45% |
|                                 90th percentile service time |            asc_sort_population |     44.683 |     42.877 | -1.80596 |      ms |   -4.04% |
|                                 99th percentile service time |            asc_sort_population |    51.6042 |     45.332 | -6.27212 |      ms |  -12.15% |
|                                100th percentile service time |            asc_sort_population |    56.9335 |    46.8128 | -10.1207 |      ms |  -17.78% |
|                                                   error rate |            asc_sort_population |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput | asc_sort_with_after_population |    1.50363 |    1.50355 |   -8e-05 |   ops/s |   -0.01% |
|                                              Mean Throughput | asc_sort_with_after_population |    1.50441 |    1.50432 |   -9e-05 |   ops/s |   -0.01% |
|                                            Median Throughput | asc_sort_with_after_population |    1.50435 |    1.50426 |   -9e-05 |   ops/s |   -0.01% |
|                                               Max Throughput | asc_sort_with_after_population |    1.50543 |    1.50531 | -0.00012 |   ops/s |   -0.01% |
|                                      50th percentile latency | asc_sort_with_after_population |     56.509 |    65.5177 |  9.00866 |      ms |  +15.94% |
|                                      90th percentile latency | asc_sort_with_after_population |    58.5452 |      68.44 |  9.89472 |      ms |  +16.90% |
|                                      99th percentile latency | asc_sort_with_after_population |    60.1424 |    71.5509 |  11.4085 |      ms |  +18.97% |
|                                     100th percentile latency | asc_sort_with_after_population |    60.2061 |    74.7287 |  14.5227 |      ms |  +24.12% |
|                                 50th percentile service time | asc_sort_with_after_population |    55.0002 |     64.026 |  9.02576 |      ms |  +16.41% |
|                                 90th percentile service time | asc_sort_with_after_population |    57.2007 |    67.0489 |  9.84819 |      ms |  +17.22% |
|                                 99th percentile service time | asc_sort_with_after_population |     58.203 |    70.1639 |  11.9609 |      ms |  +20.55% |
|                                100th percentile service time | asc_sort_with_after_population |     58.674 |    73.7291 |  15.0551 |      ms |  +25.66% |
|                                                   error rate | asc_sort_with_after_population |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |            desc_sort_geonameid |    6.01524 |    6.01492 | -0.00032 |   ops/s |   -0.01% |
|                                              Mean Throughput |            desc_sort_geonameid |    6.01821 |    6.01787 | -0.00034 |   ops/s |   -0.01% |
|                                            Median Throughput |            desc_sort_geonameid |      6.018 |    6.01765 | -0.00035 |   ops/s |   -0.01% |
|                                               Max Throughput |            desc_sort_geonameid |    6.02194 |    6.02154 |  -0.0004 |   ops/s |   -0.01% |
|                                      50th percentile latency |            desc_sort_geonameid |    39.4811 |    41.8618 |  2.38071 |      ms |   +6.03% |
|                                      90th percentile latency |            desc_sort_geonameid |    42.0933 |    43.1879 |  1.09457 |      ms |   +2.60% |
|                                      99th percentile latency |            desc_sort_geonameid |    48.2163 |    44.7758 | -3.44058 |      ms |   -7.14% |
|                                     100th percentile latency |            desc_sort_geonameid |    58.9307 |    68.9611 |  10.0304 |      ms |  +17.02% |
|                                 50th percentile service time |            desc_sort_geonameid |    38.5908 |    40.9669 |  2.37611 |      ms |   +6.16% |
|                                 90th percentile service time |            desc_sort_geonameid |    41.1406 |    42.3643 |  1.22373 |      ms |   +2.97% |
|                                 99th percentile service time |            desc_sort_geonameid |    47.5553 |    43.7471 | -3.80823 |      ms |   -8.01% |
|                                100th percentile service time |            desc_sort_geonameid |    58.0114 |    68.0175 |  10.0061 |      ms |  +17.25% |
|                                                   error rate |            desc_sort_geonameid |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput | desc_sort_with_after_geonameid |    6.01194 |    6.01217 |  0.00023 |   ops/s |    0.00% |
|                                              Mean Throughput | desc_sort_with_after_geonameid |    6.01422 |    6.01452 |   0.0003 |   ops/s |    0.00% |
|                                            Median Throughput | desc_sort_with_after_geonameid |    6.01404 |    6.01433 |  0.00028 |   ops/s |    0.00% |
|                                               Max Throughput | desc_sort_with_after_geonameid |    6.01714 |     6.0175 |  0.00036 |   ops/s |    0.01% |
|                                      50th percentile latency | desc_sort_with_after_geonameid |    66.3288 |    64.2012 | -2.12761 |      ms |   -3.21% |
|                                      90th percentile latency | desc_sort_with_after_geonameid |    70.0207 |    66.2011 | -3.81959 |      ms |   -5.45% |
|                                      99th percentile latency | desc_sort_with_after_geonameid |    77.2519 |    73.0869 | -4.16496 |      ms |   -5.39% |
|                                     100th percentile latency | desc_sort_with_after_geonameid |    86.9023 |    73.1383 | -13.7641 |      ms |  -15.84% |
|                                 50th percentile service time | desc_sort_with_after_geonameid |    65.6924 |    62.6014 | -3.09091 |      ms |   -4.71% |
|                                 90th percentile service time | desc_sort_with_after_geonameid |    69.1085 |    64.3718 | -4.73669 |      ms |   -6.85% |
|                                 99th percentile service time | desc_sort_with_after_geonameid |    76.8884 |    70.9504 | -5.93798 |      ms |   -7.72% |
|                                100th percentile service time | desc_sort_with_after_geonameid |    86.1575 |    71.1413 | -15.0162 |      ms |  -17.43% |
|                                                   error rate | desc_sort_with_after_geonameid |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |             asc_sort_geonameid |    6.01488 |     6.0149 |    2e-05 |   ops/s |    0.00% |
|                                              Mean Throughput |             asc_sort_geonameid |    6.01784 |    6.01782 |   -2e-05 |   ops/s |   -0.00% |
|                                            Median Throughput |             asc_sort_geonameid |     6.0176 |     6.0176 |       -0 |   ops/s |   -0.00% |
|                                               Max Throughput |             asc_sort_geonameid |    6.02155 |    6.02149 |   -5e-05 |   ops/s |   -0.00% |
|                                      50th percentile latency |             asc_sort_geonameid |     39.085 |    41.6561 |   2.5711 |      ms |   +6.58% |
|                                      90th percentile latency |             asc_sort_geonameid |    40.8731 |    43.3234 |  2.45028 |      ms |   +5.99% |
|                                      99th percentile latency |             asc_sort_geonameid |    43.6998 |    45.6732 |  1.97336 |      ms |   +4.52% |
|                                     100th percentile latency |             asc_sort_geonameid |    52.4637 |    71.7746 |  19.3109 |      ms |  +36.81% |
|                                 50th percentile service time |             asc_sort_geonameid |     38.311 |    40.8036 |  2.49261 |      ms |   +6.51% |
|                                 90th percentile service time |             asc_sort_geonameid |    40.2508 |    42.5683 |  2.31749 |      ms |   +5.76% |
|                                 99th percentile service time |             asc_sort_geonameid |    42.5806 |    44.7381 |  2.15751 |      ms |   +5.07% |
|                                100th percentile service time |             asc_sort_geonameid |    51.7065 |    70.8488 |  19.1423 |      ms |  +37.02% |
|                                                   error rate |             asc_sort_geonameid |          0 |          0 |        0 |       % |    0.00% |
|                                               Min Throughput |  asc_sort_with_after_geonameid |    6.01264 |    6.01295 |  0.00031 |   ops/s |    0.01% |
|                                              Mean Throughput |  asc_sort_with_after_geonameid |     6.0151 |    6.01555 |  0.00045 |   ops/s |    0.01% |
|                                            Median Throughput |  asc_sort_with_after_geonameid |    6.01474 |    6.01537 |  0.00063 |   ops/s |   +0.01% |
|                                               Max Throughput |  asc_sort_with_after_geonameid |    6.01825 |    6.01875 |   0.0005 |   ops/s |    0.01% |
|                                      50th percentile latency |  asc_sort_with_after_geonameid |    61.7013 |    58.5808 | -3.12044 |      ms |   -5.06% |
|                                      90th percentile latency |  asc_sort_with_after_geonameid |    65.5766 |    60.6772 | -4.89936 |      ms |   -7.47% |
|                                      99th percentile latency |  asc_sort_with_after_geonameid |    85.0325 |    64.6664 | -20.3661 |      ms |  -23.95% |
|                                     100th percentile latency |  asc_sort_with_after_geonameid |    91.5658 |    65.7508 |  -25.815 |      ms |  -28.19% |
|                                 50th percentile service time |  asc_sort_with_after_geonameid |    60.8904 |    57.6006 | -3.28973 |      ms |   -5.40% |
|                                 90th percentile service time |  asc_sort_with_after_geonameid |    64.4161 |    59.5893 | -4.82683 |      ms |   -7.49% |
|                                 99th percentile service time |  asc_sort_with_after_geonameid |    84.3455 |    63.6792 | -20.6663 |      ms |  -24.50% |
|                                100th percentile service time |  asc_sort_with_after_geonameid |    89.4492 |    65.2108 | -24.2384 |      ms |  -27.10% |
|                                                   error rate |  asc_sort_with_after_geonameid |          0 |          0 |        0 |       % |    0.00% |



# nested

## 场景介绍

数据量：3.4 GB

场景描述：StackOverflow Q&A stored as nested docs



## 性能对比

baseline：SSD，raceid：4c695f02-cdc0-4bf9-9001-32c607653de5

contender：PMEM，raceid：e94ceafb-01bd-48a4-b8ee-21f14dbf9253

|                                                       Metric |                                                       Task |   Baseline |  Contender |     Diff |   Unit |   Diff % |
| -----------------------------------------------------------: | ---------------------------------------------------------: | ---------: | ---------: | -------: | -----: | -------: |
|                   Cumulative indexing time of primary shards |                                                            |    474.654 |    605.229 |  130.576 |    min |  +27.51% |
|            Min cumulative indexing time across primary shard |                                                            |          0 |      4.513 |    4.513 |    min |    0.00% |
|         Median cumulative indexing time across primary shard |                                                            |    15.3826 |    21.1105 |  5.72788 |    min |  +37.24% |
|            Max cumulative indexing time across primary shard |                                                            |    165.091 |    194.912 |  29.8216 |    min |  +18.06% |
|          Cumulative indexing throttle time of primary shards |                                                            |    0.00595 |          0 | -0.00595 |    min | -100.00% |
|   Min cumulative indexing throttle time across primary shard |                                                            |          0 |          0 |        0 |    min |    0.00% |
| Median cumulative indexing throttle time across primary shard |                                                            |          0 |          0 |        0 |    min |    0.00% |
|   Max cumulative indexing throttle time across primary shard |                                                            | 0.00248333 |          0 | -0.00248 |    min | -100.00% |
|                      Cumulative merge time of primary shards |                                                            |    291.839 |    313.945 |  22.1062 |    min |   +7.57% |
|                     Cumulative merge count of primary shards |                                                            |       1542 |       1994 |      452 |        |  +29.31% |
|               Min cumulative merge time across primary shard |                                                            |          0 |    1.53747 |  1.53747 |    min |    0.00% |
|            Median cumulative merge time across primary shard |                                                            |    7.60246 |    9.47738 |  1.87493 |    min |  +24.66% |
|               Max cumulative merge time across primary shard |                                                            |    68.6997 |    72.2745 |  3.57472 |    min |   +5.20% |
|             Cumulative merge throttle time of primary shards |                                                            |    103.373 |    87.7685 | -15.6043 |    min |  -15.10% |
|      Min cumulative merge throttle time across primary shard |                                                            |          0 |   0.150433 |  0.15043 |    min |    0.00% |
|   Median cumulative merge throttle time across primary shard |                                                            |     2.0235 |    1.57455 | -0.44895 |    min |  -22.19% |
|      Max cumulative merge throttle time across primary shard |                                                            |    27.2988 |    23.8589 |  -3.4399 |    min |  -12.60% |
|                    Cumulative refresh time of primary shards |                                                            |    28.2086 |    29.7152 |  1.50657 |    min |   +5.34% |
|                   Cumulative refresh count of primary shards |                                                            |       3038 |       3395 |      357 |        |  +11.75% |
|             Min cumulative refresh time across primary shard |                                                            |          0 |  0.0606667 |  0.06067 |    min |    0.00% |
|          Median cumulative refresh time across primary shard |                                                            |   0.677008 |     0.5084 | -0.16861 |    min |  -24.90% |
|             Max cumulative refresh time across primary shard |                                                            |    3.18668 |    2.99333 | -0.19335 |    min |   -6.07% |
|                      Cumulative flush time of primary shards |                                                            |    24.0738 |    4.95738 | -19.1165 |    min |  -79.41% |
|                     Cumulative flush count of primary shards |                                                            |        225 |        238 |       13 |        |   +5.78% |
|               Min cumulative flush time across primary shard |                                                            |          0 | 0.00676667 |  0.00677 |    min |    0.00% |
|            Median cumulative flush time across primary shard |                                                            |   0.756033 |   0.108017 | -0.64802 |    min |  -85.71% |
|               Max cumulative flush time across primary shard |                                                            |    3.68175 |    2.90753 | -0.77422 |    min |  -21.03% |
|                                      Total Young Gen GC time |                                                            |      7.504 |      7.897 |    0.393 |      s |   +5.24% |
|                                     Total Young Gen GC count |                                                            |       1884 |       1904 |       20 |        |   +1.06% |
|                                        Total Old Gen GC time |                                                            |      5.928 |      6.303 |    0.375 |      s |   +6.33% |
|                                       Total Old Gen GC count |                                                            |        158 |        165 |        7 |        |   +4.43% |
|                                                   Store size |                                                            |    114.422 |    114.631 |  0.20896 |     GB |   +0.18% |
|                                                Translog size |                                                            |    5.99818 |     6.5941 |  0.59592 |     GB |   +9.93% |
|                                       Heap used for segments |                                                            |    146.429 |    144.069 | -2.35988 |     MB |   -1.61% |
|                                     Heap used for doc values |                                                            |   0.218819 |    1.69596 |  1.47715 |     MB | +675.05% |
|                                          Heap used for terms |                                                            |    110.901 |    106.944 | -3.95728 |     MB |   -3.57% |
|                                          Heap used for norms |                                                            |   0.133972 |   0.129272 |  -0.0047 |     MB |   -3.51% |
|                                         Heap used for points |                                                            |    16.3681 |    16.4805 |   0.1124 |     MB |   +0.69% |
|                                  Heap used for stored fields |                                                            |    18.8072 |    18.8197 |  0.01256 |     MB |   +0.07% |
|                                                Segment count |                                                            |        506 |        549 |       43 |        |   +8.50% |
|                                               Min Throughput |                                               index-append |    54110.4 |    60551.5 |  6441.02 | docs/s |  +11.90% |
|                                              Mean Throughput |                                               index-append |    58044.6 |    63655.1 |  5610.42 | docs/s |   +9.67% |
|                                            Median Throughput |                                               index-append |    58531.9 |    64237.9 |  5705.95 | docs/s |   +9.75% |
|                                               Max Throughput |                                               index-append |    59287.5 |    64475.7 |  5188.19 | docs/s |   +8.75% |
|                                      50th percentile latency |                                               index-append |    259.102 |    242.967 | -16.1346 |     ms |   -6.23% |
|                                      90th percentile latency |                                               index-append |    355.965 |     292.35 |  -63.615 |     ms |  -17.87% |
|                                      99th percentile latency |                                               index-append |    1473.74 |    1548.28 |  74.5384 |     ms |   +5.06% |
|                                     100th percentile latency |                                               index-append |    2597.23 |    1779.96 | -817.267 |     ms |  -31.47% |
|                                 50th percentile service time |                                               index-append |    259.102 |    242.967 | -16.1346 |     ms |   -6.23% |
|                                 90th percentile service time |                                               index-append |    355.965 |     292.35 |  -63.615 |     ms |  -17.87% |
|                                 99th percentile service time |                                               index-append |    1473.74 |    1548.28 |  74.5384 |     ms |   +5.06% |
|                                100th percentile service time |                                               index-append |    2597.23 |    1779.96 | -817.267 |     ms |  -31.47% |
|                                                   error rate |                                               index-append |          0 |          0 |        0 |      % |    0.00% |
|                                               Min Throughput |                                  randomized-nested-queries |    19.9714 |    19.9396 | -0.03176 |  ops/s |   -0.16% |
|                                              Mean Throughput |                                  randomized-nested-queries |    19.9842 |    19.9675 | -0.01675 |  ops/s |   -0.08% |
|                                            Median Throughput |                                  randomized-nested-queries |    19.9855 |      19.97 | -0.01548 |  ops/s |   -0.08% |
|                                               Max Throughput |                                  randomized-nested-queries |    19.9904 |    19.9804 | -0.01005 |  ops/s |   -0.05% |
|                                      50th percentile latency |                                  randomized-nested-queries |    39.0869 |    61.8964 |  22.8095 |     ms |  +58.36% |
|                                      90th percentile latency |                                  randomized-nested-queries |    93.3039 |    103.995 |  10.6915 |     ms |  +11.46% |
|                                      99th percentile latency |                                  randomized-nested-queries |    120.259 |    131.306 |  11.0467 |     ms |   +9.19% |
|                                    99.9th percentile latency |                                  randomized-nested-queries |     136.52 |    151.655 |  15.1352 |     ms |  +11.09% |
|                                     100th percentile latency |                                  randomized-nested-queries |    139.357 |    187.035 |  47.6778 |     ms |  +34.21% |
|                                 50th percentile service time |                                  randomized-nested-queries |    37.3166 |    58.7186 |   21.402 |     ms |  +57.35% |
|                                 90th percentile service time |                                  randomized-nested-queries |    91.2471 |    100.586 |   9.3387 |     ms |  +10.23% |
|                                 99th percentile service time |                                  randomized-nested-queries |    113.689 |    119.884 |  6.19508 |     ms |   +5.45% |
|                               99.9th percentile service time |                                  randomized-nested-queries |    135.704 |    139.126 |  3.42214 |     ms |   +2.52% |
|                                100th percentile service time |                                  randomized-nested-queries |    138.622 |    146.916 |  8.29422 |     ms |   +5.98% |
|                                                   error rate |                                  randomized-nested-queries |          0 |          0 |        0 |      % |    0.00% |
|                                               Min Throughput |                                    randomized-term-queries |    25.0157 |    25.0157 |   -7e-05 |  ops/s |   -0.00% |
|                                              Mean Throughput |                                    randomized-term-queries |    25.0182 |    25.0184 |  0.00014 |  ops/s |    0.00% |
|                                            Median Throughput |                                    randomized-term-queries |    25.0179 |    25.0184 |  0.00046 |  ops/s |    0.00% |
|                                               Max Throughput |                                    randomized-term-queries |    25.0217 |    25.0217 |    5e-05 |  ops/s |    0.00% |
|                                      50th percentile latency |                                    randomized-term-queries |    2.23418 |    2.33244 |  0.09826 |     ms |   +4.40% |
|                                      90th percentile latency |                                    randomized-term-queries |    2.69193 |    2.77842 |  0.08649 |     ms |   +3.21% |
|                                      99th percentile latency |                                    randomized-term-queries |    3.32288 |     3.7031 |  0.38023 |     ms |  +11.44% |
|                                     100th percentile latency |                                    randomized-term-queries |    13.2096 |    13.0285 | -0.18109 |     ms |   -1.37% |
|                                 50th percentile service time |                                    randomized-term-queries |    1.45572 |    1.51846 |  0.06274 |     ms |   +4.31% |
|                                 90th percentile service time |                                    randomized-term-queries |    1.64094 |    1.74669 |  0.10575 |     ms |   +6.44% |
|                                 99th percentile service time |                                    randomized-term-queries |    2.06141 |    3.05676 |  0.99535 |     ms |  +48.28% |
|                                100th percentile service time |                                    randomized-term-queries |    12.0583 |    12.3819 |  0.32358 |     ms |   +2.68% |
|                                                   error rate |                                    randomized-term-queries |          0 |          0 |        0 |      % |    0.00% |
|                                               Min Throughput |                             randomized-sorted-term-queries |    15.6228 |    13.6811 | -1.94174 |  ops/s |  -12.43% |
|                                              Mean Throughput |                             randomized-sorted-term-queries |    15.7141 |    13.7238 | -1.99033 |  ops/s |  -12.67% |
|                                            Median Throughput |                             randomized-sorted-term-queries |    15.7005 |    13.7187 | -1.98183 |  ops/s |  -12.62% |
|                                               Max Throughput |                             randomized-sorted-term-queries |    15.8575 |    13.7682 | -2.08931 |  ops/s |  -13.18% |
|                                      50th percentile latency |                             randomized-sorted-term-queries |    1482.11 |      12403 |  10920.9 |     ms | +736.85% |
|                                      90th percentile latency |                             randomized-sorted-term-queries |    2033.75 |    14239.8 |    12206 |     ms | +600.17% |
|                                      99th percentile latency |                             randomized-sorted-term-queries |    2199.98 |    14696.8 |  12496.9 |     ms | +568.04% |
|                                     100th percentile latency |                             randomized-sorted-term-queries |    2238.01 |    14757.5 |  12519.5 |     ms | +559.40% |
|                                 50th percentile service time |                             randomized-sorted-term-queries |     121.73 |    141.403 |   19.673 |     ms |  +16.16% |
|                                 90th percentile service time |                             randomized-sorted-term-queries |    202.421 |    206.375 |  3.95429 |     ms |   +1.95% |
|                                 99th percentile service time |                             randomized-sorted-term-queries |    216.878 |    234.532 |  17.6545 |     ms |   +8.14% |
|                                100th percentile service time |                             randomized-sorted-term-queries |    225.587 |    240.319 |  14.7312 |     ms |   +6.53% |
|                                                   error rate |                             randomized-sorted-term-queries |          0 |          0 |        0 |      % |    0.00% |
|                                               Min Throughput |                                                  match-all |    5.00348 |    5.00347 |   -2e-05 |  ops/s |   -0.00% |
|                                              Mean Throughput |                                                  match-all |    5.00409 |    5.00409 |       -0 |  ops/s |   -0.00% |
|                                            Median Throughput |                                                  match-all |    5.00405 |    5.00406 |    1e-05 |  ops/s |    0.00% |
|                                               Max Throughput |                                                  match-all |    5.00486 |    5.00484 |   -2e-05 |  ops/s |   -0.00% |
|                                      50th percentile latency |                                                  match-all |    2.40959 |    2.44746 |  0.03787 |     ms |   +1.57% |
|                                      90th percentile latency |                                                  match-all |    2.81949 |    2.82801 |  0.00852 |     ms |   +0.30% |
|                                      99th percentile latency |                                                  match-all |     3.4947 |    3.08019 |  -0.4145 |     ms |  -11.86% |
|                                     100th percentile latency |                                                  match-all |    6.65915 |    3.24691 | -3.41224 |     ms |  -51.24% |
|                                 50th percentile service time |                                                  match-all |    1.18015 |    1.19211 |  0.01196 |     ms |   +1.01% |
|                                 90th percentile service time |                                                  match-all |    1.42429 |    1.40719 |  -0.0171 |     ms |   -1.20% |
|                                 99th percentile service time |                                                  match-all |     2.2292 |    1.52667 | -0.70253 |     ms |  -31.51% |
|                                100th percentile service time |                                                  match-all |    5.45903 |    1.89093 |  -3.5681 |     ms |  -65.36% |
|                                                   error rate |                                                  match-all |          0 |          0 |        0 |      % |    0.00% |
|                                               Min Throughput |                                          nested-date-histo |   0.996271 |   0.995727 | -0.00054 |  ops/s |   -0.05% |
|                                              Mean Throughput |                                          nested-date-histo |    0.99794 |   0.997638 |  -0.0003 |  ops/s |   -0.03% |
|                                            Median Throughput |                                          nested-date-histo |   0.998123 |   0.997849 | -0.00027 |  ops/s |   -0.03% |
|                                               Max Throughput |                                          nested-date-histo |   0.998747 |   0.998563 | -0.00018 |  ops/s |   -0.02% |
|                                      50th percentile latency |                                          nested-date-histo |    1715.37 |    1668.64 | -46.7251 |     ms |   -2.72% |
|                                      90th percentile latency |                                          nested-date-histo |    1736.74 |    1697.08 | -39.6549 |     ms |   -2.28% |
|                                      99th percentile latency |                                          nested-date-histo |    1758.66 |    1717.82 | -40.8393 |     ms |   -2.32% |
|                                     100th percentile latency |                                          nested-date-histo |    1783.62 |    1749.26 | -34.3582 |     ms |   -1.93% |
|                                 50th percentile service time |                                          nested-date-histo |    1714.09 |    1667.64 | -46.4413 |     ms |   -2.71% |
|                                 90th percentile service time |                                          nested-date-histo |    1735.39 |    1695.85 | -39.5374 |     ms |   -2.28% |
|                                 99th percentile service time |                                          nested-date-histo |    1756.97 |    1716.83 | -40.1443 |     ms |   -2.28% |
|                                100th percentile service time |                                          nested-date-histo |    1783.05 |    1748.57 |  -34.476 |     ms |   -1.93% |
|                                                   error rate |                                          nested-date-histo |          0 |          0 |        0 |      % |    0.00% |
|                                               Min Throughput |          randomized-nested-queries-with-inner-hits_default |    17.9971 |    17.9875 | -0.00956 |  ops/s |   -0.05% |
|                                              Mean Throughput |          randomized-nested-queries-with-inner-hits_default |    17.9994 |    17.9929 | -0.00645 |  ops/s |   -0.04% |
|                                            Median Throughput |          randomized-nested-queries-with-inner-hits_default |    17.9995 |    17.9934 | -0.00604 |  ops/s |   -0.03% |
|                                               Max Throughput |          randomized-nested-queries-with-inner-hits_default |    17.9997 |    17.9958 | -0.00388 |  ops/s |   -0.02% |
|                                      50th percentile latency |          randomized-nested-queries-with-inner-hits_default |    41.7091 |      63.41 |  21.7009 |     ms |  +52.03% |
|                                      90th percentile latency |          randomized-nested-queries-with-inner-hits_default |    98.7107 |    105.317 |  6.60588 |     ms |   +6.69% |
|                                      99th percentile latency |          randomized-nested-queries-with-inner-hits_default |    123.834 |    128.741 |  4.90688 |     ms |   +3.96% |
|                                    99.9th percentile latency |          randomized-nested-queries-with-inner-hits_default |    138.365 |     163.94 |   25.575 |     ms |  +18.48% |
|                                     100th percentile latency |          randomized-nested-queries-with-inner-hits_default |    140.366 |    186.466 |  46.1002 |     ms |  +32.84% |
|                                 50th percentile service time |          randomized-nested-queries-with-inner-hits_default |    40.4523 |    61.2054 |  20.7531 |     ms |  +51.30% |
|                                 90th percentile service time |          randomized-nested-queries-with-inner-hits_default |    97.1639 |    101.614 |  4.45002 |     ms |   +4.58% |
|                                 99th percentile service time |          randomized-nested-queries-with-inner-hits_default |    120.841 |    124.022 |  3.18114 |     ms |   +2.63% |
|                               99.9th percentile service time |          randomized-nested-queries-with-inner-hits_default |    137.646 |    142.866 |  5.22084 |     ms |   +3.79% |
|                                100th percentile service time |          randomized-nested-queries-with-inner-hits_default |    139.027 |    153.404 |  14.3771 |     ms |  +10.34% |
|                                                   error rate |          randomized-nested-queries-with-inner-hits_default |          0 |          0 |        0 |      % |    0.00% |
|                                               Min Throughput | randomized-nested-queries-with-inner-hits_default_big_size |    15.9942 |    15.9866 | -0.00753 |  ops/s |   -0.05% |
|                                              Mean Throughput | randomized-nested-queries-with-inner-hits_default_big_size |    16.0001 |    15.9962 | -0.00388 |  ops/s |   -0.02% |
|                                            Median Throughput | randomized-nested-queries-with-inner-hits_default_big_size |    16.0002 |    15.9965 |  -0.0037 |  ops/s |   -0.02% |
|                                               Max Throughput | randomized-nested-queries-with-inner-hits_default_big_size |    16.0006 |    15.9978 | -0.00273 |  ops/s |   -0.02% |
|                                      50th percentile latency | randomized-nested-queries-with-inner-hits_default_big_size |    64.3149 |    85.1834 |  20.8684 |     ms |  +32.45% |
|                                      90th percentile latency | randomized-nested-queries-with-inner-hits_default_big_size |     122.55 |    128.006 |  5.45656 |     ms |   +4.45% |
|                                      99th percentile latency | randomized-nested-queries-with-inner-hits_default_big_size |    154.577 |    157.993 |    3.416 |     ms |   +2.21% |
|                                    99.9th percentile latency | randomized-nested-queries-with-inner-hits_default_big_size |    174.047 |    193.748 |  19.7008 |     ms |  +11.32% |
|                                     100th percentile latency | randomized-nested-queries-with-inner-hits_default_big_size |    200.972 |    197.385 | -3.58659 |     ms |   -1.78% |
|                                 50th percentile service time | randomized-nested-queries-with-inner-hits_default_big_size |    61.0352 |    82.7252 |    21.69 |     ms |  +35.54% |
|                                 90th percentile service time | randomized-nested-queries-with-inner-hits_default_big_size |    117.736 |    121.195 |  3.45954 |     ms |   +2.94% |
|                                 99th percentile service time | randomized-nested-queries-with-inner-hits_default_big_size |    144.888 |    150.898 |  6.00988 |     ms |   +4.15% |
|                               99.9th percentile service time | randomized-nested-queries-with-inner-hits_default_big_size |    161.813 |    165.955 |  4.14258 |     ms |   +2.56% |
|                                100th percentile service time | randomized-nested-queries-with-inner-hits_default_big_size |    199.749 |    167.804 | -31.9449 |     ms |  -15.99% |
|                                                   error rate | randomized-nested-queries-with-inner-hits_default_big_size |          0 |          0 |        0 |      % |    0.00% |



# metricbeat

## 场景介绍

数据量：1.2 GB

场景描述：Metricbeat data



## 性能对比

baseline：SSD，raceid：528c206d-abd2-4bbb-b55a-8e65af5a4a4d

contender：PMEM，raceid：9bbb9e73-7880-4c50-a79e-3189b3ba932b

|                                                       Metric |                        Task |   Baseline |  Contender |     Diff |   Unit |     Diff % |
| -----------------------------------------------------------: | --------------------------: | ---------: | ---------: | -------: | -----: | ---------: |
|                   Cumulative indexing time of primary shards |                             |    29.2634 |    612.841 |  583.578 |    min |  +1994.23% |
|            Min cumulative indexing time across primary shard |                             |      4.513 |      4.513 |        0 |    min |      0.00% |
|         Median cumulative indexing time across primary shard |                             |    4.92942 |    21.1105 |  16.1811 |    min |   +328.26% |
|            Max cumulative indexing time across primary shard |                             |    5.14115 |    194.912 |  189.771 |    min |  +3691.22% |
|          Cumulative indexing throttle time of primary shards |                             |          0 |          0 |        0 |    min |      0.00% |
|   Min cumulative indexing throttle time across primary shard |                             |          0 |          0 |        0 |    min |      0.00% |
| Median cumulative indexing throttle time across primary shard |                             |          0 |          0 |        0 |    min |      0.00% |
|   Max cumulative indexing throttle time across primary shard |                             |          0 |          0 |        0 |    min |      0.00% |
|                      Cumulative merge time of primary shards |                             |    11.0114 |    316.519 |  305.508 |    min |  +2774.46% |
|                     Cumulative merge count of primary shards |                             |        207 |       1992 |     1785 |        |   +862.32% |
|               Min cumulative merge time across primary shard |                             |    1.53747 |    1.53747 |        0 |    min |      0.00% |
|            Median cumulative merge time across primary shard |                             |    1.80297 |    9.47738 |  7.67442 |    min |   +425.65% |
|               Max cumulative merge time across primary shard |                             |    2.07468 |    72.2745 |  70.1998 |    min |  +3383.64% |
|             Cumulative merge throttle time of primary shards |                             |     3.8773 |    87.8971 |  84.0198 |    min |  +2166.97% |
|      Min cumulative merge throttle time across primary shard |                             |   0.426317 |   0.150433 | -0.27588 |    min |    -64.71% |
|   Median cumulative merge throttle time across primary shard |                             |   0.643225 |    1.57455 |  0.93132 |    min |   +144.79% |
|      Max cumulative merge throttle time across primary shard |                             |     0.9319 |    23.8589 |   22.927 |    min |  +2460.24% |
|                    Cumulative refresh time of primary shards |                             |   0.978633 |    29.7186 |  28.7399 |    min |  +2936.74% |
|                   Cumulative refresh count of primary shards |                             |        261 |       3477 |     3216 |        |  +1232.18% |
|             Min cumulative refresh time across primary shard |                             |  0.0606667 |    0.06405 |  0.00338 |    min |     +5.58% |
|          Median cumulative refresh time across primary shard |                             |   0.181708 |     0.5084 |  0.32669 |    min |   +179.79% |
|             Max cumulative refresh time across primary shard |                             |   0.196117 |    2.99333 |  2.79722 |    min |  +1426.30% |
|                      Cumulative flush time of primary shards |                             |  0.0787333 |    4.96607 |  4.88733 |    min |  +6207.45% |
|                     Cumulative flush count of primary shards |                             |         18 |        238 |      220 |        |  +1222.22% |
|               Min cumulative flush time across primary shard |                             | 0.00943333 | 0.00676667 | -0.00267 |    min |    -28.27% |
|            Median cumulative flush time across primary shard |                             |   0.012625 |   0.108017 |  0.09539 |    min |   +755.58% |
|               Max cumulative flush time across primary shard |                             |  0.0189333 |    2.90753 |   2.8886 |    min | +15256.69% |
|                                      Total Young Gen GC time |                             |      4.957 |      3.171 |   -1.786 |      s |    -36.03% |
|                                     Total Young Gen GC count |                             |        698 |        679 |      -19 |        |     -2.72% |
|                                        Total Old Gen GC time |                             |     10.417 |     71.036 |   60.619 |      s |   +581.92% |
|                                       Total Old Gen GC count |                             |        102 |        262 |      160 |        |   +156.86% |
|                                                   Store size |                             |    4.15927 |    114.605 |  110.446 |     GB |  +2655.42% |
|                                                Translog size |                             |   0.525305 |   0.534494 |  0.00919 |     GB |     +1.75% |
|                                       Heap used for segments |                             |    27.0111 |     143.81 |  116.799 |     MB |   +432.41% |
|                                     Heap used for doc values |                             |    1.43922 |    1.48225 |  0.04303 |     MB |     +2.99% |
|                                          Heap used for terms |                             |    23.0506 |    106.912 |  83.8612 |     MB |   +363.81% |
|                                          Heap used for norms |                             |          0 |   0.129272 |  0.12927 |     MB |      0.00% |
|                                         Heap used for points |                             |    0.94655 |    16.4781 |  15.5315 |     MB |  +1640.86% |
|                                  Heap used for stored fields |                             |    1.57471 |    18.8086 |  17.2339 |     MB |  +1094.41% |
|                                                Segment count |                             |        129 |        548 |      419 |        |   +324.81% |
|                                               Min Throughput |                index-append |     2294.3 |    1276.88 | -1017.42 | docs/s |    -44.35% |
|                                              Mean Throughput |                index-append |    20277.7 |     9040.3 | -11237.4 | docs/s |    -55.42% |
|                                            Median Throughput |                index-append |    21504.2 |    9348.19 |   -12156 | docs/s |    -56.53% |
|                                               Max Throughput |                index-append |    23904.2 |    10207.4 | -13696.7 | docs/s |    -57.30% |
|                                      50th percentile latency |                index-append |    2957.44 |    7912.55 |  4955.11 |     ms |   +167.55% |
|                                      90th percentile latency |                index-append |    3611.54 |    10034.6 |  6423.05 |     ms |   +177.85% |
|                                      99th percentile latency |                index-append |    4848.61 |    11860.2 |  7011.58 |     ms |   +144.61% |
|                                     100th percentile latency |                index-append |    4875.96 |    12583.4 |  7707.44 |     ms |   +158.07% |
|                                 50th percentile service time |                index-append |    2957.44 |    7912.55 |  4955.11 |     ms |   +167.55% |
|                                 90th percentile service time |                index-append |    3611.54 |    10034.6 |  6423.05 |     ms |   +177.85% |
|                                 99th percentile service time |                index-append |    4848.61 |    11860.2 |  7011.58 |     ms |   +144.61% |
|                                100th percentile service time |                index-append |    4875.96 |    12583.4 |  7707.44 |     ms |   +158.07% |
|                                                   error rate |                index-append |          0 |    4.46429 |  4.46429 |      % |      0.00% |
|                                               Min Throughput |         auto-date-histogram |    2.01281 |     2.0134 |  0.00058 |  ops/s |     +0.03% |
|                                              Mean Throughput |         auto-date-histogram |    2.02106 |    2.02203 |  0.00097 |  ops/s |     +0.05% |
|                                            Median Throughput |         auto-date-histogram |    2.01914 |    2.02001 |  0.00087 |  ops/s |     +0.04% |
|                                               Max Throughput |         auto-date-histogram |    2.03789 |    2.03963 |  0.00174 |  ops/s |     +0.09% |
|                                      50th percentile latency |         auto-date-histogram |    3.29228 |    2.60439 | -0.68789 |     ms |    -20.89% |
|                                      90th percentile latency |         auto-date-histogram |    3.90944 |    3.33443 | -0.57501 |     ms |    -14.71% |
|                                      99th percentile latency |         auto-date-histogram |    5.67746 |    4.99162 | -0.68585 |     ms |    -12.08% |
|                                     100th percentile latency |         auto-date-histogram |    6.47521 |    12.7985 |  6.32329 |     ms |    +97.65% |
|                                 50th percentile service time |         auto-date-histogram |    1.97115 |    1.32164 |  -0.6495 |     ms |    -32.95% |
|                                 90th percentile service time |         auto-date-histogram |    2.21508 |    1.63449 |  -0.5806 |     ms |    -26.21% |
|                                 99th percentile service time |         auto-date-histogram |    4.03851 |     4.0741 |  0.03559 |     ms |     +0.88% |
|                                100th percentile service time |         auto-date-histogram |    4.81174 |    11.4608 |  6.64907 |     ms |   +138.18% |
|                                                   error rate |         auto-date-histogram |          0 |          0 |        0 |      % |      0.00% |
|                                               Min Throughput | auto-date-histogram-with-tz |    2.01334 |    2.01337 |    4e-05 |  ops/s |      0.00% |
|                                              Mean Throughput | auto-date-histogram-with-tz |    2.02196 |    2.02201 |    4e-05 |  ops/s |      0.00% |
|                                            Median Throughput | auto-date-histogram-with-tz |    2.01995 |    2.01999 |    4e-05 |  ops/s |      0.00% |
|                                               Max Throughput | auto-date-histogram-with-tz |     2.0395 |    2.03961 |   0.0001 |  ops/s |      0.01% |
|                                      50th percentile latency | auto-date-histogram-with-tz |    3.05472 |    2.68888 | -0.36584 |     ms |    -11.98% |
|                                      90th percentile latency | auto-date-histogram-with-tz |     3.6366 |    3.28988 | -0.34671 |     ms |     -9.53% |
|                                      99th percentile latency | auto-date-histogram-with-tz |    4.92875 |    4.85605 |  -0.0727 |     ms |     -1.48% |
|                                     100th percentile latency | auto-date-histogram-with-tz |    4.97265 |    5.31419 |  0.34154 |     ms |     +6.87% |
|                                 50th percentile service time | auto-date-histogram-with-tz |    1.74951 |    1.34982 | -0.39968 |     ms |    -22.85% |
|                                 90th percentile service time | auto-date-histogram-with-tz |    1.95282 |     1.5029 | -0.44992 |     ms |    -23.04% |
|                                 99th percentile service time | auto-date-histogram-with-tz |    3.22487 |    3.10264 | -0.12223 |     ms |     -3.79% |
|                                100th percentile service time | auto-date-histogram-with-tz |    3.29794 |    3.61931 |  0.32138 |     ms |     +9.74% |
|                                                   error rate | auto-date-histogram-with-tz |          0 |          0 |        0 |      % |      0.00% |
|                                               Min Throughput |              date-histogram |    2.01324 |    2.01337 |  0.00013 |  ops/s |      0.01% |
|                                              Mean Throughput |              date-histogram |    2.02179 |    2.02199 |  0.00021 |  ops/s |     +0.01% |
|                                            Median Throughput |              date-histogram |     2.0198 |    2.01999 |  0.00019 |  ops/s |      0.01% |
|                                               Max Throughput |              date-histogram |    2.03913 |    2.03953 |  0.00039 |  ops/s |     +0.02% |
|                                      50th percentile latency |              date-histogram |    2.96973 |    2.65724 | -0.31249 |     ms |    -10.52% |
|                                      90th percentile latency |              date-histogram |    3.49314 |    3.26312 | -0.23002 |     ms |     -6.58% |
|                                      99th percentile latency |              date-histogram |    4.74458 |    4.37318 |  -0.3714 |     ms |     -7.83% |
|                                     100th percentile latency |              date-histogram |    4.97385 |    4.70543 | -0.26842 |     ms |     -5.40% |
|                                 50th percentile service time |              date-histogram |    1.67807 |    1.35182 | -0.32625 |     ms |    -19.44% |
|                                 90th percentile service time |              date-histogram |    1.86353 |    1.48633 |  -0.3772 |     ms |    -20.24% |
|                                 99th percentile service time |              date-histogram |    3.24195 |    2.84216 |  -0.3998 |     ms |    -12.33% |
|                                100th percentile service time |              date-histogram |     3.3502 |    3.39283 |  0.04264 |     ms |     +1.27% |
|                                                   error rate |              date-histogram |          0 |          0 |        0 |      % |      0.00% |
|                                               Min Throughput |      date-histogram-with-tz |    2.01336 |    2.01335 |   -1e-05 |  ops/s |     -0.00% |
|                                              Mean Throughput |      date-histogram-with-tz |    2.02198 |    2.02198 |       -0 |  ops/s |     -0.00% |
|                                            Median Throughput |      date-histogram-with-tz |    2.01996 |    2.01998 |    2e-05 |  ops/s |      0.00% |
|                                               Max Throughput |      date-histogram-with-tz |    2.03953 |    2.03954 |        0 |  ops/s |      0.00% |
|                                      50th percentile latency |      date-histogram-with-tz |    3.10689 |    2.72942 | -0.37746 |     ms |    -12.15% |
|                                      90th percentile latency |      date-histogram-with-tz |    3.95704 |    3.30519 | -0.65185 |     ms |    -16.47% |
|                                      99th percentile latency |      date-histogram-with-tz |    4.84461 |    4.78807 | -0.05654 |     ms |     -1.17% |
|                                     100th percentile latency |      date-histogram-with-tz |    4.84535 |    7.29531 |  2.44996 |     ms |    +50.56% |
|                                 50th percentile service time |      date-histogram-with-tz |    1.70377 |    1.41997 |  -0.2838 |     ms |    -16.66% |
|                                 90th percentile service time |      date-histogram-with-tz |    2.42135 |    1.59197 | -0.82938 |     ms |    -34.25% |
|                                 99th percentile service time |      date-histogram-with-tz |    3.34523 |    3.22214 | -0.12308 |     ms |     -3.68% |
|                                100th percentile service time |      date-histogram-with-tz |    3.39852 |    5.65547 |  2.25695 |     ms |    +66.41% |
|                                                   error rate |      date-histogram-with-tz |          0 |          0 |        0 |      % |      0.00% |



# percolator

## 场景介绍

数据量：104.9 MB

场景描述：Percolator benchmark based on AOL queries



## 性能对比

baseline：SSD，raceid：6abdde38-6b0f-4c33-aebe-ea237753a1b6

contender：PMEM，raceid：836619c5-3c39-4fb4-a287-728b56176bf6

|                                                       Metric |                                       Task |   Baseline |  Contender |     Diff |  Unit |   Diff % |
| -----------------------------------------------------------: | -----------------------------------------: | ---------: | ---------: | -------: | ----: | -------: |
|                   Cumulative indexing time of primary shards |                                            |    476.043 |    614.421 |  138.378 |   min |  +29.07% |
|            Min cumulative indexing time across primary shard |                                            |          0 |    0.30325 |  0.30325 |   min |    0.00% |
|         Median cumulative indexing time across primary shard |                                            |     5.7402 |    8.62013 |  2.87993 |   min |  +50.17% |
|            Max cumulative indexing time across primary shard |                                            |    165.091 |    194.912 |  29.8216 |   min |  +18.06% |
|          Cumulative indexing throttle time of primary shards |                                            |    0.00595 |          0 | -0.00595 |   min | -100.00% |
|   Min cumulative indexing throttle time across primary shard |                                            |          0 |          0 |        0 |   min |    0.00% |
| Median cumulative indexing throttle time across primary shard |                                            |          0 |          0 |        0 |   min |    0.00% |
|   Max cumulative indexing throttle time across primary shard |                                            | 0.00248333 |          0 | -0.00248 |   min | -100.00% |
|                      Cumulative merge time of primary shards |                                            |    291.913 |    316.586 |  24.6732 |   min |   +8.45% |
|                     Cumulative merge count of primary shards |                                            |       1551 |       2002 |      451 |       |  +29.08% |
|               Min cumulative merge time across primary shard |                                            |          0 |  0.0102667 |  0.01027 |   min |    0.00% |
|            Median cumulative merge time across primary shard |                                            |    2.10818 |    2.99808 |  0.88989 |   min |  +42.21% |
|               Max cumulative merge time across primary shard |                                            |    68.6997 |    72.2745 |  3.57472 |   min |   +5.20% |
|             Cumulative merge throttle time of primary shards |                                            |    103.373 |    87.8971 | -15.4758 |   min |  -14.97% |
|      Min cumulative merge throttle time across primary shard |                                            |          0 |          0 |        0 |   min |    0.00% |
|   Median cumulative merge throttle time across primary shard |                                            |   0.226217 |   0.804183 |  0.57797 |   min | +255.49% |
|      Max cumulative merge throttle time across primary shard |                                            |    27.2988 |    23.8589 |  -3.4399 |   min |  -12.60% |
|                    Cumulative refresh time of primary shards |                                            |    28.2449 |    29.7564 |  1.51147 |   min |   +5.35% |
|                   Cumulative refresh count of primary shards |                                            |       3154 |       3596 |      442 |       |  +14.01% |
|             Min cumulative refresh time across primary shard |                                            |          0 | 0.00696667 |  0.00697 |   min |    0.00% |
|          Median cumulative refresh time across primary shard |                                            |    0.45025 |   0.487925 |  0.03768 |   min |   +8.37% |
|             Max cumulative refresh time across primary shard |                                            |    3.18668 |    2.99333 | -0.19335 |   min |   -6.07% |
|                      Cumulative flush time of primary shards |                                            |    24.0738 |    4.96607 | -19.1078 |   min |  -79.37% |
|                     Cumulative flush count of primary shards |                                            |        230 |        243 |       13 |       |   +5.65% |
|               Min cumulative flush time across primary shard |                                            |          0 |          0 |        0 |   min |    0.00% |
|            Median cumulative flush time across primary shard |                                            |  0.0800333 |    0.02145 | -0.05858 |   min |  -73.20% |
|               Max cumulative flush time across primary shard |                                            |    3.68175 |    2.90753 | -0.77422 |   min |  -21.03% |
|                                      Total Young Gen GC time |                                            |     18.258 |     18.349 |    0.091 |     s |   +0.50% |
|                                     Total Young Gen GC count |                                            |       8833 |       8852 |       19 |       |   +0.22% |
|                                        Total Old Gen GC time |                                            |      0.229 |      0.271 |    0.042 |     s |  +18.34% |
|                                       Total Old Gen GC count |                                            |          6 |          7 |        1 |       |  +16.67% |
|                                                   Store size |                                            |    114.555 |    114.739 |  0.18432 |    GB |   +0.16% |
|                                                Translog size |                                            |    6.22919 |     0.7655 | -5.46369 |    GB |  -87.71% |
|                                       Heap used for segments |                                            |    147.042 |    144.382 | -2.65927 |    MB |   -1.81% |
|                                     Heap used for doc values |                                            |   0.225746 |    1.48878 |  1.26304 |    MB | +559.50% |
|                                          Heap used for terms |                                            |    111.449 |     107.42 | -4.02876 |    MB |   -3.61% |
|                                          Heap used for norms |                                            |   0.133972 |   0.129272 |  -0.0047 |    MB |   -3.51% |
|                                         Heap used for points |                                            |    16.3778 |    16.4878 |  0.11001 |    MB |   +0.67% |
|                                  Heap used for stored fields |                                            |    18.8553 |    18.8564 |  0.00115 |    MB |    0.01% |
|                                                Segment count |                                            |        540 |        580 |       40 |       |   +7.41% |
|                                                   error rate |                                      index |          0 |          0 |        0 |     % |    0.00% |
|                                               Min Throughput |     percolator_with_content_president_bush |    48.4661 |    48.8902 |  0.42413 | ops/s |   +0.88% |
|                                              Mean Throughput |     percolator_with_content_president_bush |    48.6481 |    49.0233 |  0.37525 | ops/s |   +0.77% |
|                                            Median Throughput |     percolator_with_content_president_bush |    48.6481 |    49.0233 |  0.37525 | ops/s |   +0.77% |
|                                               Max Throughput |     percolator_with_content_president_bush |    48.8301 |    49.1565 |  0.32638 | ops/s |   +0.67% |
|                                      50th percentile latency |     percolator_with_content_president_bush |    5.10115 |    5.38404 |   0.2829 |    ms |   +5.55% |
|                                      90th percentile latency |     percolator_with_content_president_bush |    6.43865 |     6.8639 |  0.42525 |    ms |   +6.60% |
|                                      99th percentile latency |     percolator_with_content_president_bush |    8.26214 |     8.0592 | -0.20294 |    ms |   -2.46% |
|                                     100th percentile latency |     percolator_with_content_president_bush |    8.69044 |    8.46926 | -0.22118 |    ms |   -2.55% |
|                                 50th percentile service time |     percolator_with_content_president_bush |    4.19427 |    4.39733 |  0.20306 |    ms |   +4.84% |
|                                 90th percentile service time |     percolator_with_content_president_bush |    5.54724 |     5.7582 |  0.21096 |    ms |   +3.80% |
|                                 99th percentile service time |     percolator_with_content_president_bush |    7.63296 |    7.55121 | -0.08175 |    ms |   -1.07% |
|                                100th percentile service time |     percolator_with_content_president_bush |     8.2989 |    7.67432 | -0.62458 |    ms |   -7.53% |
|                                                   error rate |     percolator_with_content_president_bush |          0 |          0 |        0 |     % |    0.00% |
|                                               Min Throughput |     percolator_with_content_saddam_hussein |    50.2384 |    50.2465 |   0.0081 | ops/s |   +0.02% |
|                                              Mean Throughput |     percolator_with_content_saddam_hussein |    50.2874 |    50.3075 |  0.02008 | ops/s |   +0.04% |
|                                            Median Throughput |     percolator_with_content_saddam_hussein |    50.2874 |    50.3075 |  0.02008 | ops/s |   +0.04% |
|                                               Max Throughput |     percolator_with_content_saddam_hussein |    50.3364 |    50.3685 |  0.03206 | ops/s |   +0.06% |
|                                      50th percentile latency |     percolator_with_content_saddam_hussein |    2.38533 |    2.39962 |  0.01429 |    ms |   +0.60% |
|                                      90th percentile latency |     percolator_with_content_saddam_hussein |    3.11938 |    3.15874 |  0.03935 |    ms |   +1.26% |
|                                      99th percentile latency |     percolator_with_content_saddam_hussein |    3.50533 |    3.52515 |  0.01982 |    ms |   +0.57% |
|                                     100th percentile latency |     percolator_with_content_saddam_hussein |    6.37304 |    6.15348 | -0.21956 |    ms |   -3.45% |
|                                 50th percentile service time |     percolator_with_content_saddam_hussein |    1.19534 |    1.17926 | -0.01607 |    ms |   -1.34% |
|                                 90th percentile service time |     percolator_with_content_saddam_hussein |    1.27646 |    1.26993 | -0.00652 |    ms |   -0.51% |
|                                 99th percentile service time |     percolator_with_content_saddam_hussein |    1.41735 |    2.02615 |  0.60879 |    ms |  +42.95% |
|                                100th percentile service time |     percolator_with_content_saddam_hussein |    6.15096 |    4.34668 | -1.80429 |    ms |  -29.33% |
|                                                   error rate |     percolator_with_content_saddam_hussein |          0 |          0 |        0 |     % |    0.00% |
|                                               Min Throughput |  percolator_with_content_hurricane_katrina |     50.206 |    50.2094 |  0.00339 | ops/s |    0.01% |
|                                              Mean Throughput |  percolator_with_content_hurricane_katrina |    50.2596 |    50.2656 |  0.00601 | ops/s |   +0.01% |
|                                            Median Throughput |  percolator_with_content_hurricane_katrina |    50.2596 |    50.2656 |  0.00601 | ops/s |   +0.01% |
|                                               Max Throughput |  percolator_with_content_hurricane_katrina |    50.3132 |    50.3218 |  0.00864 | ops/s |   +0.02% |
|                                      50th percentile latency |  percolator_with_content_hurricane_katrina |       4.47 |    4.34526 | -0.12474 |    ms |   -2.79% |
|                                      90th percentile latency |  percolator_with_content_hurricane_katrina |    5.50357 |    5.12897 |  -0.3746 |    ms |   -6.81% |
|                                      99th percentile latency |  percolator_with_content_hurricane_katrina |    7.33885 |    6.86356 | -0.47529 |    ms |   -6.48% |
|                                     100th percentile latency |  percolator_with_content_hurricane_katrina |    8.86587 |    6.95653 | -1.90934 |    ms |  -21.54% |
|                                 50th percentile service time |  percolator_with_content_hurricane_katrina |    3.50868 |    3.46166 | -0.04702 |    ms |   -1.34% |
|                                 90th percentile service time |  percolator_with_content_hurricane_katrina |    4.49575 |    4.40422 | -0.09153 |    ms |   -2.04% |
|                                 99th percentile service time |  percolator_with_content_hurricane_katrina |    6.55451 |    6.48506 | -0.06945 |    ms |   -1.06% |
|                                100th percentile service time |  percolator_with_content_hurricane_katrina |    7.82794 |    6.70148 | -1.12647 |    ms |  -14.39% |
|                                                   error rate |  percolator_with_content_hurricane_katrina |          0 |          0 |        0 |     % |    0.00% |
|                                               Min Throughput |             percolator_with_content_google |    27.0411 |    27.0095 | -0.03161 | ops/s |   -0.12% |
|                                              Mean Throughput |             percolator_with_content_google |    27.0543 |    27.0105 | -0.04378 | ops/s |   -0.16% |
|                                            Median Throughput |             percolator_with_content_google |    27.0525 |    27.0101 | -0.04243 | ops/s |   -0.16% |
|                                               Max Throughput |             percolator_with_content_google |     27.071 |    27.0124 | -0.05865 | ops/s |   -0.22% |
|                                      50th percentile latency |             percolator_with_content_google |    22.6636 |    23.0186 |  0.35502 |    ms |   +1.57% |
|                                      90th percentile latency |             percolator_with_content_google |    25.7649 |    26.3138 |  0.54892 |    ms |   +2.13% |
|                                      99th percentile latency |             percolator_with_content_google |    31.6968 |    29.9802 | -1.71659 |    ms |   -5.42% |
|                                     100th percentile latency |             percolator_with_content_google |    33.4922 |    32.3046 | -1.18757 |    ms |   -3.55% |
|                                 50th percentile service time |             percolator_with_content_google |    21.3492 |     22.079 |  0.72974 |    ms |   +3.42% |
|                                 90th percentile service time |             percolator_with_content_google |      24.71 |    25.3582 |  0.64812 |    ms |   +2.62% |
|                                 99th percentile service time |             percolator_with_content_google |    30.8494 |    29.4239 | -1.42542 |    ms |   -4.62% |
|                                100th percentile service time |             percolator_with_content_google |    33.0871 |    31.9865 | -1.10067 |    ms |   -3.33% |
|                                                   error rate |             percolator_with_content_google |          0 |          0 |        0 |     % |    0.00% |
|                                               Min Throughput |    percolator_no_score_with_content_google |    99.9217 |    99.9801 |  0.05838 | ops/s |   +0.06% |
|                                              Mean Throughput |    percolator_no_score_with_content_google |    99.9217 |    99.9801 |  0.05838 | ops/s |   +0.06% |
|                                            Median Throughput |    percolator_no_score_with_content_google |    99.9217 |    99.9801 |  0.05838 | ops/s |   +0.06% |
|                                               Max Throughput |    percolator_no_score_with_content_google |    99.9217 |    99.9801 |  0.05838 | ops/s |   +0.06% |
|                                      50th percentile latency |    percolator_no_score_with_content_google |    3.09961 |    2.97074 | -0.12887 |    ms |   -4.16% |
|                                      90th percentile latency |    percolator_no_score_with_content_google |    4.02637 |    3.37268 | -0.65369 |    ms |  -16.24% |
|                                      99th percentile latency |    percolator_no_score_with_content_google |    4.58881 |    3.51952 | -1.06929 |    ms |  -23.30% |
|                                     100th percentile latency |    percolator_no_score_with_content_google |    5.87833 |    3.70577 | -2.17256 |    ms |  -36.96% |
|                                 50th percentile service time |    percolator_no_score_with_content_google |    2.28462 |    2.25869 | -0.02593 |    ms |   -1.13% |
|                                 90th percentile service time |    percolator_no_score_with_content_google |    3.31493 |    2.34528 | -0.96965 |    ms |  -29.25% |
|                                 99th percentile service time |    percolator_no_score_with_content_google |    3.46801 |    2.61732 | -0.85069 |    ms |  -24.53% |
|                                100th percentile service time |    percolator_no_score_with_content_google |    5.47706 |    3.20452 | -2.27253 |    ms |  -41.49% |
|                                                   error rate |    percolator_no_score_with_content_google |          0 |          0 |        0 |     % |    0.00% |
|                                               Min Throughput |               percolator_with_highlighting |    49.3905 |    48.4063 | -0.98414 | ops/s |   -1.99% |
|                                              Mean Throughput |               percolator_with_highlighting |    49.4676 |    48.6037 | -0.86383 | ops/s |   -1.75% |
|                                            Median Throughput |               percolator_with_highlighting |    49.4676 |    48.6037 | -0.86383 | ops/s |   -1.75% |
|                                               Max Throughput |               percolator_with_highlighting |    49.5447 |    48.8012 | -0.74351 | ops/s |   -1.50% |
|                                      50th percentile latency |               percolator_with_highlighting |    3.55896 |    3.27772 | -0.28124 |    ms |   -7.90% |
|                                      90th percentile latency |               percolator_with_highlighting |     4.2771 |    4.55909 |    0.282 |    ms |   +6.59% |
|                                      99th percentile latency |               percolator_with_highlighting |    7.24255 |     6.1896 | -1.05295 |    ms |  -14.54% |
|                                     100th percentile latency |               percolator_with_highlighting |    7.71404 |    7.14709 | -0.56695 |    ms |   -7.35% |
|                                 50th percentile service time |               percolator_with_highlighting |    2.66007 |    2.46399 | -0.19608 |    ms |   -7.37% |
|                                 90th percentile service time |               percolator_with_highlighting |    3.22582 |     2.9683 | -0.25751 |    ms |   -7.98% |
|                                 99th percentile service time |               percolator_with_highlighting |    6.14617 |    5.62867 |  -0.5175 |    ms |   -8.42% |
|                                100th percentile service time |               percolator_with_highlighting |    6.21757 |    6.93895 |  0.72138 |    ms |  +11.60% |
|                                                   error rate |               percolator_with_highlighting |          0 |          0 |        0 |     % |    0.00% |
|                                               Min Throughput |          percolator_with_content_ignore_me |  0.0838694 |  0.0838565 |   -1e-05 | ops/s |   -0.02% |
|                                              Mean Throughput |          percolator_with_content_ignore_me |  0.0847497 |  0.0847142 |   -4e-05 | ops/s |   -0.04% |
|                                            Median Throughput |          percolator_with_content_ignore_me |  0.0843139 |  0.0842896 |   -2e-05 | ops/s |   -0.03% |
|                                               Max Throughput |          percolator_with_content_ignore_me |  0.0890269 |   0.088878 | -0.00015 | ops/s |   -0.17% |
|                                      50th percentile latency |          percolator_with_content_ignore_me |    3664.83 |    3705.36 |  40.5271 |    ms |   +1.11% |
|                                      90th percentile latency |          percolator_with_content_ignore_me |    3700.43 |     3758.2 |  57.7685 |    ms |   +1.56% |
|                                      99th percentile latency |          percolator_with_content_ignore_me |    3747.48 |    3821.48 |   74.001 |    ms |   +1.97% |
|                                     100th percentile latency |          percolator_with_content_ignore_me |    3778.37 |    3845.18 |  66.8107 |    ms |   +1.77% |
|                                 50th percentile service time |          percolator_with_content_ignore_me |    3659.17 |    3700.25 |   41.073 |    ms |   +1.12% |
|                                 90th percentile service time |          percolator_with_content_ignore_me |    3692.06 |    3752.64 |  60.5759 |    ms |   +1.64% |
|                                 99th percentile service time |          percolator_with_content_ignore_me |    3741.43 |    3820.19 |  78.7617 |    ms |   +2.11% |
|                                100th percentile service time |          percolator_with_content_ignore_me |    3770.01 |     3843.8 |  73.7917 |    ms |   +1.96% |
|                                                   error rate |          percolator_with_content_ignore_me |          0 |          0 |        0 |     % |    0.00% |
|                                               Min Throughput | percolator_no_score_with_content_ignore_me |    15.0701 |    15.0701 |   -4e-05 | ops/s |   -0.00% |
|                                              Mean Throughput | percolator_no_score_with_content_ignore_me |    15.0949 |    15.0948 | -0.00013 | ops/s |   -0.00% |
|                                            Median Throughput | percolator_no_score_with_content_ignore_me |    15.0908 |    15.0903 | -0.00047 | ops/s |   -0.00% |
|                                               Max Throughput | percolator_no_score_with_content_ignore_me |      15.13 |    15.1309 |  0.00093 | ops/s |    0.01% |
|                                      50th percentile latency | percolator_no_score_with_content_ignore_me |    3.01262 |    2.80222 |  -0.2104 |    ms |   -6.98% |
|                                      90th percentile latency | percolator_no_score_with_content_ignore_me |    3.77459 |    3.42798 | -0.34661 |    ms |   -9.18% |
|                                      99th percentile latency | percolator_no_score_with_content_ignore_me |    4.13534 |    3.83877 | -0.29656 |    ms |   -7.17% |
|                                     100th percentile latency | percolator_no_score_with_content_ignore_me |    5.07484 |    5.76588 |  0.69104 |    ms |  +13.62% |
|                                 50th percentile service time | percolator_no_score_with_content_ignore_me |    2.02746 |    2.02939 |  0.00194 |    ms |   +0.10% |
|                                 90th percentile service time | percolator_no_score_with_content_ignore_me |     2.8822 |    2.32702 | -0.55518 |    ms |  -19.26% |
|                                 99th percentile service time | percolator_no_score_with_content_ignore_me |    3.10174 |    2.66425 |  -0.4375 |    ms |  -14.10% |
|                                100th percentile service time | percolator_no_score_with_content_ignore_me |    4.67231 |    4.77867 |  0.10635 |    ms |   +2.28% |
|                                                   error rate | percolator_no_score_with_content_ignore_me |          0 |          0 |        0 |     % |    0.00% |









































