Corona Virus Cases and Death Rates 
================

## GitHub Documents

This is an R Markdown format used for publishing markdown documents to
GitHub. When you click the **Knit** button all R code chunks are run and
a markdown file (.md) suitable for publishing to GitHub is generated.

## 

``` r
url <- "https://tinyurl.com/COVID-2019"

virus <- read.csv(url)

tail(virus)
```

    ##      Province.State Country.Region      Lat     Long       date cases      type
    ## 2881         Shanxi Mainland China  37.5777 112.2922 2020-03-05     2 recovered
    ## 2882        Sichuan Mainland China  30.6171 102.7103 2020-03-05    19 recovered
    ## 2883        Tianjin Mainland China  39.3054 117.3230 2020-03-05     4 recovered
    ## 2884       Victoria      Australia -37.8136 144.9631 2020-03-05     3 recovered
    ## 2885       Xinjiang Mainland China  41.1129  85.2401 2020-03-05     1 recovered
    ## 2886       Zhejiang Mainland China  29.1832 120.0934 2020-03-05    10 recovered

``` r
table(virus$cases)
```

    ## 
    ##   -20   -11    -8    -5    -4    -3    -2    -1     1     2     3     4     5 
    ##     1     1     1     1     1     1     3     8   670   346   209   152   133 
    ##     6     7     8     9    10    11    12    13    14    15    16    17    18 
    ##   110    97    68    53    58    63    42    49    40    35    31    30    28 
    ##    19    20    21    22    23    24    25    26    27    28    29    30    31 
    ##    33    27    22    22    24    20    12    13    11    19    21    15    12 
    ##    32    33    34    35    36    37    38    39    40    41    42    43    44 
    ##    11     6    17    14    12    12     8     9    10     9     9     7     6 
    ##    45    46    47    48    49    50    51    52    53    55    56    57    58 
    ##     7     4     3     7     4     5     8     8     2     2     3     4     5 
    ##    59    60    61    62    63    64    65    66    67    68    69    70    71 
    ##     5     1    10     2     3     3     3     4     2     4     3     4     3 
    ##    72    73    74    75    77    78    79    81    82    85    87    88    89 
    ##     4     3     4     2     1     2     1     4     2     1     1     2     1 
    ##    91    92    93    94    97    99   100   101   103   105   106   108   109 
    ##     2     1     5     2     1     3     2     1     1     2     1     1     1 
    ##   110   111   114   115   116   123   127   131   132   134   136   138   139 
    ##     1     1     1     2     2     1     1     1     2     1     1     1     1 
    ##   143   144   147   149   169   184   187   196   202   203   205   212   220 
    ##     1     1     1     1     1     1     1     1     2     2     1     1     2 
    ##   229   231   233   240   242   261   284   297   298   318   324   342   349 
    ##     1     1     1     1     1     1     1     1     1     1     1     1     1 
    ##   356   365   385   401   409   411   417   423   427   435   444   466   467 
    ##     1     1     1     1     1     1     1     1     1     1     1     1     1 
    ##   499   505   523   566   570   571   586   587   591   599   769   773   813 
    ##     1     1     1     1     1     1     2     1     1     1     1     1     1 
    ##   835   849   851   903  1016  1209  1223  1266  1315  1347  1349  1405  1422 
    ##     1     1     1     1     1     1     1     1     1     1     1     1     1 
    ##  1451  1638  1693  1807  1843  1933  1998  2035  2097  2131  2147  2223  2274 
    ##     1     1     1     1     1     1     1     1     1     1     1     1     1 
    ##  2345  2349  2398  2414  2447  2531  2543  2590  2841  2987  3020  3156  3418 
    ##     1     1     1     1     1     1     1     1     1     1     1     1     1 
    ##  4024  6200 14840 
    ##     1     1     1

## Q1. How many total infected cases are there around the world?

\#check in cases and sum it up

``` r
sum(virus$cases)
```

    ## [1] 155031

## Q2. How many deaths linked to infected cases have there been?

``` r
virus$type
```

    ##    [1] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##    [8] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [15] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [22] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [29] confirmed death     recovered confirmed confirmed confirmed confirmed
    ##   [36] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [43] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [50] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [57] confirmed confirmed confirmed death     recovered confirmed confirmed
    ##   [64] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [71] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [78] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [85] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##   [92] confirmed confirmed death     death     recovered recovered recovered
    ##   [99] recovered confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [106] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [113] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [120] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [127] confirmed confirmed confirmed confirmed confirmed confirmed death    
    ##  [134] recovered recovered recovered confirmed confirmed confirmed confirmed
    ##  [141] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [148] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [155] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [162] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [169] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [176] confirmed confirmed death     death     death     recovered recovered
    ##  [183] recovered confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [190] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [197] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [204] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [211] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [218] confirmed confirmed confirmed confirmed death     death     death    
    ##  [225] recovered recovered recovered recovered confirmed confirmed confirmed
    ##  [232] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [239] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [246] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [253] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [260] confirmed confirmed confirmed confirmed confirmed confirmed death    
    ##  [267] recovered recovered recovered recovered recovered recovered recovered
    ##  [274] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [281] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [288] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [295] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [302] confirmed confirmed confirmed death     death     recovered recovered
    ##  [309] recovered recovered recovered recovered recovered recovered recovered
    ##  [316] recovered recovered confirmed confirmed confirmed confirmed confirmed
    ##  [323] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [330] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [337] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [344] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [351] confirmed confirmed confirmed confirmed confirmed confirmed death    
    ##  [358] death     recovered recovered recovered recovered recovered recovered
    ##  [365] recovered recovered recovered confirmed confirmed confirmed confirmed
    ##  [372] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [379] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [386] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [393] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [400] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [407] confirmed confirmed confirmed confirmed confirmed confirmed death    
    ##  [414] recovered recovered recovered recovered recovered recovered recovered
    ##  [421] recovered recovered recovered recovered recovered recovered confirmed
    ##  [428] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [435] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [442] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [449] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [456] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [463] confirmed confirmed confirmed confirmed confirmed death     death    
    ##  [470] recovered recovered recovered recovered recovered recovered recovered
    ##  [477] recovered recovered recovered recovered recovered recovered recovered
    ##  [484] recovered confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [491] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [498] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [505] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [512] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [519] confirmed confirmed confirmed confirmed confirmed confirmed death    
    ##  [526] death     death     recovered recovered recovered recovered recovered
    ##  [533] recovered recovered recovered recovered recovered recovered recovered
    ##  [540] recovered recovered recovered recovered recovered confirmed confirmed
    ##  [547] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [554] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [561] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [568] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [575] confirmed confirmed confirmed confirmed confirmed death     recovered
    ##  [582] recovered recovered recovered recovered recovered recovered recovered
    ##  [589] recovered recovered recovered recovered recovered recovered recovered
    ##  [596] recovered recovered confirmed confirmed confirmed confirmed confirmed
    ##  [603] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [610] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [617] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [624] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [631] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [638] death     death     recovered recovered recovered recovered recovered
    ##  [645] recovered recovered recovered recovered recovered recovered recovered
    ##  [652] recovered recovered recovered recovered recovered recovered recovered
    ##  [659] recovered recovered confirmed confirmed confirmed confirmed confirmed
    ##  [666] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [673] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [680] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [687] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [694] confirmed death     death     death     recovered recovered recovered
    ##  [701] recovered recovered recovered recovered recovered recovered recovered
    ##  [708] recovered recovered recovered recovered recovered recovered recovered
    ##  [715] recovered recovered recovered recovered recovered recovered recovered
    ##  [722] recovered confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [729] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [736] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [743] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [750] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [757] confirmed death     death     recovered recovered recovered recovered
    ##  [764] recovered recovered recovered recovered recovered recovered recovered
    ##  [771] recovered recovered recovered recovered recovered recovered recovered
    ##  [778] recovered recovered recovered recovered recovered recovered recovered
    ##  [785] recovered recovered confirmed confirmed confirmed confirmed confirmed
    ##  [792] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [799] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [806] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [813] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [820] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [827] death     death     death     death     death     recovered recovered
    ##  [834] recovered recovered recovered recovered recovered recovered recovered
    ##  [841] recovered recovered recovered recovered recovered recovered recovered
    ##  [848] recovered recovered recovered recovered recovered recovered recovered
    ##  [855] recovered recovered recovered recovered confirmed confirmed confirmed
    ##  [862] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [869] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [876] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [883] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [890] confirmed confirmed confirmed confirmed confirmed death     death    
    ##  [897] death     death     death     death     recovered recovered recovered
    ##  [904] recovered recovered recovered recovered recovered recovered recovered
    ##  [911] recovered recovered recovered recovered recovered recovered recovered
    ##  [918] recovered recovered recovered recovered recovered recovered recovered
    ##  [925] recovered recovered recovered recovered confirmed confirmed confirmed
    ##  [932] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [939] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [946] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [953] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ##  [960] confirmed confirmed confirmed confirmed confirmed death     death    
    ##  [967] death     death     death     death     death     death     death    
    ##  [974] recovered recovered recovered recovered recovered recovered recovered
    ##  [981] recovered recovered recovered recovered recovered recovered recovered
    ##  [988] recovered recovered recovered recovered recovered recovered recovered
    ##  [995] recovered recovered recovered recovered recovered recovered recovered
    ## [1002] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1009] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1016] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1023] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1030] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1037] death     death     death     death     recovered recovered recovered
    ## [1044] recovered recovered recovered recovered recovered recovered recovered
    ## [1051] recovered recovered recovered recovered recovered recovered recovered
    ## [1058] recovered recovered recovered recovered recovered recovered recovered
    ## [1065] recovered confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1072] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1079] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1086] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1093] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1100] confirmed death     death     death     death     death     death    
    ## [1107] death     recovered recovered recovered recovered recovered recovered
    ## [1114] recovered recovered recovered recovered recovered recovered recovered
    ## [1121] recovered recovered recovered recovered recovered recovered recovered
    ## [1128] recovered recovered recovered recovered recovered recovered recovered
    ## [1135] recovered recovered recovered recovered recovered recovered confirmed
    ## [1142] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1149] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1156] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1163] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1170] confirmed confirmed confirmed confirmed death     death     death    
    ## [1177] death     death     recovered recovered recovered recovered recovered
    ## [1184] recovered recovered recovered recovered recovered recovered recovered
    ## [1191] recovered recovered recovered recovered recovered recovered recovered
    ## [1198] recovered recovered recovered recovered recovered recovered recovered
    ## [1205] recovered recovered recovered recovered recovered recovered recovered
    ## [1212] recovered recovered recovered recovered recovered recovered recovered
    ## [1219] recovered recovered recovered confirmed confirmed confirmed confirmed
    ## [1226] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1233] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1240] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1247] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1254] death     death     death     death     death     death     death    
    ## [1261] death     death     death     death     recovered recovered recovered
    ## [1268] recovered recovered recovered recovered recovered recovered recovered
    ## [1275] recovered recovered recovered recovered recovered recovered recovered
    ## [1282] recovered recovered recovered recovered recovered recovered recovered
    ## [1289] recovered recovered recovered recovered recovered recovered recovered
    ## [1296] recovered recovered recovered confirmed confirmed confirmed confirmed
    ## [1303] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1310] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1317] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1324] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1331] confirmed death     death     death     death     death     recovered
    ## [1338] recovered recovered recovered recovered recovered recovered recovered
    ## [1345] recovered recovered recovered recovered recovered recovered recovered
    ## [1352] recovered recovered recovered recovered recovered recovered recovered
    ## [1359] recovered recovered recovered recovered recovered confirmed confirmed
    ## [1366] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1373] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1380] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1387] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1394] confirmed confirmed death     death     death     death     recovered
    ## [1401] recovered recovered recovered recovered recovered recovered recovered
    ## [1408] recovered recovered recovered recovered recovered recovered recovered
    ## [1415] recovered recovered recovered recovered recovered recovered recovered
    ## [1422] recovered recovered recovered recovered recovered recovered recovered
    ## [1429] recovered recovered recovered recovered recovered recovered recovered
    ## [1436] recovered confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1443] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1450] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1457] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1464] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1471] death     death     death     death     recovered recovered recovered
    ## [1478] recovered recovered recovered recovered recovered recovered recovered
    ## [1485] recovered recovered recovered recovered recovered recovered recovered
    ## [1492] recovered recovered recovered recovered recovered recovered recovered
    ## [1499] recovered recovered recovered recovered recovered recovered recovered
    ## [1506] recovered recovered confirmed confirmed confirmed confirmed confirmed
    ## [1513] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1520] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1527] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1534] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1541] death     death     death     recovered recovered recovered recovered
    ## [1548] recovered recovered recovered recovered recovered recovered recovered
    ## [1555] recovered recovered recovered recovered recovered recovered recovered
    ## [1562] recovered recovered recovered recovered recovered recovered recovered
    ## [1569] recovered recovered recovered recovered recovered recovered recovered
    ## [1576] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1583] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1590] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1597] confirmed confirmed confirmed confirmed confirmed death     death    
    ## [1604] death     death     death     death     recovered recovered recovered
    ## [1611] recovered recovered recovered recovered recovered recovered recovered
    ## [1618] recovered recovered recovered recovered recovered recovered recovered
    ## [1625] recovered recovered recovered recovered recovered recovered recovered
    ## [1632] recovered recovered recovered recovered recovered recovered recovered
    ## [1639] recovered recovered confirmed confirmed confirmed confirmed confirmed
    ## [1646] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1653] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1660] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1667] confirmed death     death     death     death     death     death    
    ## [1674] death     recovered recovered recovered recovered recovered recovered
    ## [1681] recovered recovered recovered recovered recovered recovered recovered
    ## [1688] recovered recovered recovered recovered recovered recovered recovered
    ## [1695] recovered recovered recovered recovered recovered recovered recovered
    ## [1702] recovered recovered recovered recovered recovered recovered recovered
    ## [1709] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1716] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1723] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1730] confirmed confirmed confirmed confirmed death     death     death    
    ## [1737] death     death     death     death     death     death     death    
    ## [1744] recovered recovered recovered recovered recovered recovered recovered
    ## [1751] recovered recovered recovered recovered recovered recovered recovered
    ## [1758] recovered recovered recovered recovered recovered recovered recovered
    ## [1765] recovered recovered recovered recovered recovered recovered recovered
    ## [1772] recovered recovered recovered recovered confirmed confirmed confirmed
    ## [1779] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1786] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1793] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1800] confirmed confirmed confirmed confirmed confirmed death     death    
    ## [1807] death     recovered recovered recovered recovered recovered recovered
    ## [1814] recovered recovered recovered recovered recovered recovered recovered
    ## [1821] recovered recovered recovered recovered recovered recovered recovered
    ## [1828] recovered recovered recovered recovered recovered recovered recovered
    ## [1835] recovered recovered recovered recovered recovered recovered recovered
    ## [1842] recovered recovered recovered recovered recovered recovered confirmed
    ## [1849] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1856] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1863] confirmed confirmed confirmed confirmed confirmed confirmed death    
    ## [1870] death     death     death     death     death     recovered recovered
    ## [1877] recovered recovered recovered recovered recovered recovered recovered
    ## [1884] recovered recovered recovered recovered recovered recovered recovered
    ## [1891] recovered recovered recovered recovered recovered recovered recovered
    ## [1898] recovered recovered recovered recovered recovered recovered confirmed
    ## [1905] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1912] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1919] death     death     death     death     death     death     recovered
    ## [1926] recovered recovered recovered recovered recovered recovered recovered
    ## [1933] recovered recovered recovered recovered recovered recovered recovered
    ## [1940] recovered recovered recovered recovered recovered recovered recovered
    ## [1947] recovered recovered recovered recovered recovered recovered recovered
    ## [1954] recovered recovered recovered recovered recovered recovered confirmed
    ## [1961] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1968] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1975] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [1982] confirmed confirmed confirmed death     death     death     death    
    ## [1989] death     recovered recovered recovered recovered recovered recovered
    ## [1996] recovered recovered recovered recovered recovered recovered recovered
    ## [2003] recovered recovered recovered recovered recovered recovered recovered
    ## [2010] recovered recovered recovered recovered recovered recovered recovered
    ## [2017] recovered recovered recovered recovered recovered confirmed confirmed
    ## [2024] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2031] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2038] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2045] confirmed confirmed confirmed death     death     death     death    
    ## [2052] death     death     recovered recovered recovered recovered recovered
    ## [2059] recovered recovered recovered recovered recovered recovered recovered
    ## [2066] recovered recovered recovered recovered recovered recovered recovered
    ## [2073] recovered recovered recovered recovered recovered recovered recovered
    ## [2080] recovered recovered recovered recovered recovered recovered recovered
    ## [2087] recovered confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2094] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2101] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2108] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2115] confirmed confirmed confirmed confirmed confirmed confirmed death    
    ## [2122] death     death     death     death     death     death     recovered
    ## [2129] recovered recovered recovered recovered recovered recovered recovered
    ## [2136] recovered recovered recovered recovered recovered recovered recovered
    ## [2143] recovered recovered recovered recovered recovered recovered recovered
    ## [2150] recovered recovered recovered recovered recovered recovered recovered
    ## [2157] recovered recovered recovered recovered recovered confirmed confirmed
    ## [2164] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2171] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2178] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2185] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2192] confirmed confirmed confirmed death     death     death     death    
    ## [2199] death     death     death     death     recovered recovered recovered
    ## [2206] recovered recovered recovered recovered recovered recovered recovered
    ## [2213] recovered recovered recovered recovered recovered recovered recovered
    ## [2220] recovered recovered recovered recovered recovered recovered recovered
    ## [2227] recovered recovered recovered recovered recovered recovered recovered
    ## [2234] recovered recovered confirmed confirmed confirmed confirmed confirmed
    ## [2241] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2248] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2255] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2262] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2269] death     death     death     death     death     death     recovered
    ## [2276] recovered recovered recovered recovered recovered recovered recovered
    ## [2283] recovered recovered recovered recovered recovered recovered recovered
    ## [2290] recovered recovered recovered recovered recovered recovered recovered
    ## [2297] recovered recovered recovered recovered recovered recovered recovered
    ## [2304] recovered recovered recovered recovered confirmed confirmed confirmed
    ## [2311] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2318] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2325] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2332] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2339] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2346] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2353] confirmed confirmed confirmed confirmed confirmed death     death    
    ## [2360] death     death     death     death     death     death     recovered
    ## [2367] recovered recovered recovered recovered recovered recovered recovered
    ## [2374] recovered recovered recovered recovered recovered recovered recovered
    ## [2381] recovered recovered recovered recovered recovered recovered recovered
    ## [2388] recovered recovered recovered recovered recovered recovered recovered
    ## [2395] recovered recovered recovered recovered recovered recovered confirmed
    ## [2402] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2409] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2416] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2423] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2430] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2437] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2444] confirmed confirmed confirmed death     death     death     death    
    ## [2451] death     death     death     death     recovered recovered recovered
    ## [2458] recovered recovered recovered recovered recovered recovered recovered
    ## [2465] recovered recovered recovered recovered recovered recovered recovered
    ## [2472] recovered recovered recovered recovered recovered recovered recovered
    ## [2479] recovered recovered recovered recovered recovered recovered recovered
    ## [2486] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2493] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2500] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2507] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2514] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2521] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2528] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2535] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2542] confirmed death     death     death     death     death     death    
    ## [2549] death     recovered recovered recovered recovered recovered recovered
    ## [2556] recovered recovered recovered recovered recovered recovered recovered
    ## [2563] recovered recovered recovered recovered recovered recovered recovered
    ## [2570] recovered recovered recovered recovered recovered recovered recovered
    ## [2577] recovered recovered recovered recovered confirmed confirmed confirmed
    ## [2584] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2591] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2598] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2605] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2612] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2619] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2626] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2633] confirmed confirmed confirmed confirmed confirmed confirmed death    
    ## [2640] death     death     death     death     death     death     death    
    ## [2647] recovered recovered recovered recovered recovered recovered recovered
    ## [2654] recovered recovered recovered recovered recovered recovered recovered
    ## [2661] recovered recovered recovered recovered recovered recovered recovered
    ## [2668] recovered recovered recovered recovered recovered recovered recovered
    ## [2675] recovered recovered recovered recovered recovered recovered confirmed
    ## [2682] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2689] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2696] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2703] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2710] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2717] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2724] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2731] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2738] confirmed confirmed death     death     death     death     death    
    ## [2745] death     death     death     death     recovered recovered recovered
    ## [2752] recovered recovered recovered recovered recovered recovered recovered
    ## [2759] recovered recovered recovered recovered recovered recovered recovered
    ## [2766] recovered recovered recovered recovered recovered recovered recovered
    ## [2773] recovered recovered recovered recovered recovered confirmed confirmed
    ## [2780] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2787] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2794] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2801] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2808] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2815] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2822] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2829] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2836] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2843] confirmed confirmed confirmed confirmed confirmed confirmed confirmed
    ## [2850] confirmed death     death     death     death     death     death    
    ## [2857] death     death     death     recovered recovered recovered recovered
    ## [2864] recovered recovered recovered recovered recovered recovered recovered
    ## [2871] recovered recovered recovered recovered recovered recovered recovered
    ## [2878] recovered recovered recovered recovered recovered recovered recovered
    ## [2885] recovered recovered
    ## Levels: confirmed death recovered

``` r
table(virus$type)
```

    ## 
    ## confirmed     death recovered 
    ##      1593       212      1081

``` r
inds <- virus$type == "death"

##use square brackets to print out all the ones that have high death

virus[inds,]
```

    ##                    Province.State Country.Region       Lat      Long       date
    ## 30                          Hubei Mainland China  30.97560  112.2707 2020-01-22
    ## 60                          Hebei Mainland China  38.04280  114.5149 2020-01-23
    ## 94                   Heilongjiang Mainland China  47.86200  127.7615 2020-01-24
    ## 95                          Hubei Mainland China  30.97560  112.2707 2020-01-24
    ## 133                         Hubei Mainland China  30.97560  112.2707 2020-01-25
    ## 178                         Henan Mainland China  33.88202  113.6140 2020-01-26
    ## 179                         Hubei Mainland China  30.97560  112.2707 2020-01-26
    ## 180                      Shanghai Mainland China  31.20200  121.4491 2020-01-26
    ## 222                       Beijing Mainland China  40.18240  116.4142 2020-01-27
    ## 223                        Hainan Mainland China  19.19590  109.7453 2020-01-27
    ## 224                         Hubei Mainland China  30.97560  112.2707 2020-01-27
    ## 266                         Hubei Mainland China  30.97560  112.2707 2020-01-28
    ## 305                         Henan Mainland China  33.88202  113.6140 2020-01-29
    ## 306                       Sichuan Mainland China  30.61710  102.7103 2020-01-29
    ## 357                  Heilongjiang Mainland China  47.86200  127.7615 2020-01-30
    ## 358                         Hubei Mainland China  30.97560  112.2707 2020-01-30
    ## 413                         Hubei Mainland China  30.97560  112.2707 2020-01-31
    ## 468                     Chongqing Mainland China  30.05720  107.8740 2020-02-01
    ## 469                         Hubei Mainland China  30.97560  112.2707 2020-02-01
    ## 525                                  Philippines  13.00000  122.0000 2020-02-02
    ## 526                     Chongqing Mainland China  30.05720  107.8740 2020-02-02
    ## 527                         Hubei Mainland China  30.97560  112.2707 2020-02-02
    ## 580                         Hubei Mainland China  30.97560  112.2707 2020-02-03
    ## 638                     Hong Kong      Hong Kong  22.30000  114.2000 2020-02-04
    ## 639                         Hubei Mainland China  30.97560  112.2707 2020-02-04
    ## 695                       Guizhou Mainland China  26.81540  106.8748 2020-02-05
    ## 696                         Hubei Mainland China  30.97560  112.2707 2020-02-05
    ## 697                       Tianjin Mainland China  39.30540  117.3230 2020-02-05
    ## 758                  Heilongjiang Mainland China  47.86200  127.7615 2020-02-06
    ## 759                         Hubei Mainland China  30.97560  112.2707 2020-02-06
    ## 827                     Guangdong Mainland China  23.34170  113.4244 2020-02-07
    ## 828                        Hainan Mainland China  19.19590  109.7453 2020-02-07
    ## 829                         Henan Mainland China  33.88202  113.6140 2020-02-07
    ## 830                         Hubei Mainland China  30.97560  112.2707 2020-02-07
    ## 831                         Jilin Mainland China  43.66610  126.1923 2020-02-07
    ## 895                       Beijing Mainland China  40.18240  116.4142 2020-02-08
    ## 896                         Gansu Mainland China  36.06110  103.8343 2020-02-08
    ## 897                  Heilongjiang Mainland China  47.86200  127.7615 2020-02-08
    ## 898                         Henan Mainland China  33.88202  113.6140 2020-02-08
    ## 899                         Hubei Mainland China  30.97560  112.2707 2020-02-08
    ## 900                         Hunan Mainland China  27.61040  111.7088 2020-02-08
    ## 965                         Anhui Mainland China  31.82570  117.2264 2020-02-09
    ## 966                         Gansu Mainland China  36.06110  103.8343 2020-02-09
    ## 967                       Guangxi Mainland China  23.82980  108.7881 2020-02-09
    ## 968                        Hainan Mainland China  19.19590  109.7453 2020-02-09
    ## 969                         Hebei Mainland China  38.04280  114.5149 2020-02-09
    ## 970                  Heilongjiang Mainland China  47.86200  127.7615 2020-02-09
    ## 971                         Henan Mainland China  33.88202  113.6140 2020-02-09
    ## 972                         Hubei Mainland China  30.97560  112.2707 2020-02-09
    ## 973                      Shandong Mainland China  36.34270  118.1498 2020-02-09
    ## 1037                        Anhui Mainland China  31.82570  117.2264 2020-02-10
    ## 1038                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-10
    ## 1039                        Hubei Mainland China  30.97560  112.2707 2020-02-10
    ## 1040                      Jiangxi Mainland China  27.61400  115.7221 2020-02-10
    ## 1101                        Anhui Mainland China  31.82570  117.2264 2020-02-11
    ## 1102                      Beijing Mainland China  40.18240  116.4142 2020-02-11
    ## 1103                    Chongqing Mainland China  30.05720  107.8740 2020-02-11
    ## 1104                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-11
    ## 1105                        Henan Mainland China  33.88202  113.6140 2020-02-11
    ## 1106                        Hubei Mainland China  30.97560  112.2707 2020-02-11
    ## 1107                      Tianjin Mainland China  39.30540  117.3230 2020-02-11
    ## 1174                       Hainan Mainland China  19.19590  109.7453 2020-02-12
    ## 1175                        Henan Mainland China  33.88202  113.6140 2020-02-12
    ## 1176                        Hunan Mainland China  27.61040  111.7088 2020-02-12
    ## 1177                     Liaoning Mainland China  41.29560  122.6085 2020-02-12
    ## 1178                     Shandong Mainland China  36.34270  118.1498 2020-02-12
    ## 1254                                       Japan  36.00000  138.0000 2020-02-13
    ## 1255                        Anhui Mainland China  31.82570  117.2264 2020-02-13
    ## 1256                    Chongqing Mainland China  30.05720  107.8740 2020-02-13
    ## 1257                    Guangdong Mainland China  23.34170  113.4244 2020-02-13
    ## 1258                      Guangxi Mainland China  23.82980  108.7881 2020-02-13
    ## 1259                        Hebei Mainland China  38.04280  114.5149 2020-02-13
    ## 1260                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-13
    ## 1261                        Henan Mainland China  33.88202  113.6140 2020-02-13
    ## 1262                        Hubei Mainland China  30.97560  112.2707 2020-02-13
    ## 1263                      Tianjin Mainland China  39.30540  117.3230 2020-02-13
    ## 1264                     Xinjiang Mainland China  41.11290   85.2401 2020-02-13
    ## 1332                        Anhui Mainland China  31.82570  117.2264 2020-02-14
    ## 1333                    Chongqing Mainland China  30.05720  107.8740 2020-02-14
    ## 1334                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-14
    ## 1335                        Henan Mainland China  33.88202  113.6140 2020-02-14
    ## 1336                        Hubei Mainland China  30.97560  112.2707 2020-02-14
    ## 1396                                      France  47.00000    2.0000 2020-02-15
    ## 1397                      Beijing Mainland China  40.18240  116.4142 2020-02-15
    ## 1398                        Henan Mainland China  33.88202  113.6140 2020-02-15
    ## 1399                        Hubei Mainland China  30.97560  112.2707 2020-02-15
    ## 1471                        Hubei Mainland China  30.97560  112.2707 2020-02-16
    ## 1472                        Hunan Mainland China  27.61040  111.7088 2020-02-16
    ## 1473                      Sichuan Mainland China  30.61710  102.7103 2020-02-16
    ## 1474                       Taiwan         Taiwan  23.70000  121.0000 2020-02-16
    ## 1541                    Guangdong Mainland China  23.34170  113.4244 2020-02-17
    ## 1542                        Henan Mainland China  33.88202  113.6140 2020-02-17
    ## 1543                        Hubei Mainland China  30.97560  112.2707 2020-02-17
    ## 1602                      Guizhou Mainland China  26.81540  106.8748 2020-02-18
    ## 1603                        Hebei Mainland China  38.04280  114.5149 2020-02-18
    ## 1604                        Henan Mainland China  33.88202  113.6140 2020-02-18
    ## 1605                        Hubei Mainland China  30.97560  112.2707 2020-02-18
    ## 1606                        Hunan Mainland China  27.61040  111.7088 2020-02-18
    ## 1607                     Shandong Mainland China  36.34270  118.1498 2020-02-18
    ## 1668                                        Iran  32.00000   53.0000 2020-02-19
    ## 1669                    Guangdong Mainland China  23.34170  113.4244 2020-02-19
    ## 1670                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-19
    ## 1671                    Hong Kong      Hong Kong  22.30000  114.2000 2020-02-19
    ## 1672                        Hubei Mainland China  30.97560  112.2707 2020-02-19
    ## 1673                     Shanghai Mainland China  31.20200  121.4491 2020-02-19
    ## 1674                       Yunnan Mainland China  24.97400  101.4870 2020-02-19
    ## 1734                                 South Korea  36.00000  128.0000 2020-02-20
    ## 1735                    Chongqing Mainland China  30.05720  107.8740 2020-02-20
    ## 1736 Diamond Princess cruise ship         Others  35.44370  139.6380 2020-02-20
    ## 1737                       Fujian Mainland China  26.07890  117.9874 2020-02-20
    ## 1738                        Hebei Mainland China  38.04280  114.5149 2020-02-20
    ## 1739                        Hubei Mainland China  30.97560  112.2707 2020-02-20
    ## 1740                      Shaanxi Mainland China  35.19170  108.8701 2020-02-20
    ## 1741                     Shandong Mainland China  36.34270  118.1498 2020-02-20
    ## 1742                       Yunnan Mainland China  24.97400  101.4870 2020-02-20
    ## 1743                     Zhejiang Mainland China  29.18320  120.0934 2020-02-20
    ## 1805                                        Iran  32.00000   53.0000 2020-02-21
    ## 1806                                       Italy  43.00000   12.0000 2020-02-21
    ## 1807                                 South Korea  36.00000  128.0000 2020-02-21
    ## 1869                                        Iran  32.00000   53.0000 2020-02-22
    ## 1870                                       Italy  43.00000   12.0000 2020-02-22
    ## 1871                        Hebei Mainland China  38.04280  114.5149 2020-02-22
    ## 1872                        Hubei Mainland China  30.97560  112.2707 2020-02-22
    ## 1873                     Shanghai Mainland China  31.20200  121.4491 2020-02-22
    ## 1874                     Xinjiang Mainland China  41.11290   85.2401 2020-02-22
    ## 1919                                        Iran  32.00000   53.0000 2020-02-23
    ## 1920                                       Italy  43.00000   12.0000 2020-02-23
    ## 1921                                 South Korea  36.00000  128.0000 2020-02-23
    ## 1922 Diamond Princess cruise ship         Others  35.44370  139.6380 2020-02-23
    ## 1923                    Guangdong Mainland China  23.34170  113.4244 2020-02-23
    ## 1924                       Hainan Mainland China  19.19590  109.7453 2020-02-23
    ## 1985                                        Iran  32.00000   53.0000 2020-02-24
    ## 1986                                       Italy  43.00000   12.0000 2020-02-24
    ## 1987                                 South Korea  36.00000  128.0000 2020-02-24
    ## 1988                        Hubei Mainland China  30.97560  112.2707 2020-02-24
    ## 1989                     Shandong Mainland China  36.34270  118.1498 2020-02-24
    ## 2048                                        Iran  32.00000   53.0000 2020-02-25
    ## 2049                                       Italy  43.00000   12.0000 2020-02-25
    ## 2050                                 South Korea  36.00000  128.0000 2020-02-25
    ## 2051                    Guangdong Mainland China  23.34170  113.4244 2020-02-25
    ## 2052                        Hubei Mainland China  30.97560  112.2707 2020-02-25
    ## 2053                     Shandong Mainland China  36.34270  118.1498 2020-02-25
    ## 2121                                      France  47.00000    2.0000 2020-02-26
    ## 2122                                        Iran  32.00000   53.0000 2020-02-26
    ## 2123                                       Italy  43.00000   12.0000 2020-02-26
    ## 2124                                       Japan  36.00000  138.0000 2020-02-26
    ## 2125                                 South Korea  36.00000  128.0000 2020-02-26
    ## 2126 Diamond Princess cruise ship         Others  35.44370  139.6380 2020-02-26
    ## 2127                        Hubei Mainland China  30.97560  112.2707 2020-02-26
    ## 2195                                        Iran  32.00000   53.0000 2020-02-27
    ## 2196                                       Italy  43.00000   12.0000 2020-02-27
    ## 2197                                       Japan  36.00000  138.0000 2020-02-27
    ## 2198                                 South Korea  36.00000  128.0000 2020-02-27
    ## 2199                      Beijing Mainland China  40.18240  116.4142 2020-02-27
    ## 2200                 Heilongjiang Mainland China  47.86200  127.7615 2020-02-27
    ## 2201                        Henan Mainland China  33.88202  113.6140 2020-02-27
    ## 2202                        Hubei Mainland China  30.97560  112.2707 2020-02-27
    ## 2269                                        Iran  32.00000   53.0000 2020-02-28
    ## 2270                                       Italy  43.00000   12.0000 2020-02-28
    ## 2271                      Beijing Mainland China  40.18240  116.4142 2020-02-28
    ## 2272 Diamond Princess cruise ship         Others  35.44370  139.6380 2020-02-28
    ## 2273                        Hubei Mainland China  30.97560  112.2707 2020-02-28
    ## 2274                     Xinjiang Mainland China  41.11290   85.2401 2020-02-28
    ## 2358                                        Iran  32.00000   53.0000 2020-02-29
    ## 2359                                       Italy  43.00000   12.0000 2020-02-29
    ## 2360                                       Japan  36.00000  138.0000 2020-02-29
    ## 2361                                 South Korea  36.00000  128.0000 2020-02-29
    ## 2362                      Beijing Mainland China  40.18240  116.4142 2020-02-29
    ## 2363                        Henan Mainland China  33.88202  113.6140 2020-02-29
    ## 2364                        Hubei Mainland China  30.97560  112.2707 2020-02-29
    ## 2365              King County, WA             US  47.60620 -122.3321 2020-02-29
    ## 2447                                        Iran  32.00000   53.0000 2020-03-01
    ## 2448                                       Italy  43.00000   12.0000 2020-03-01
    ## 2449                                       Japan  36.00000  138.0000 2020-03-01
    ## 2450                                 South Korea  36.00000  128.0000 2020-03-01
    ## 2451                                    Thailand  15.00000  101.0000 2020-03-01
    ## 2452                        Henan Mainland China  33.88202  113.6140 2020-03-01
    ## 2453                        Hubei Mainland China  30.97560  112.2707 2020-03-01
    ## 2454            Western Australia      Australia -31.95050  115.8605 2020-03-01
    ## 2543                                      France  47.00000    2.0000 2020-03-02
    ## 2544                                        Iran  32.00000   53.0000 2020-03-02
    ## 2545                                       Italy  43.00000   12.0000 2020-03-02
    ## 2546                                 South Korea  36.00000  128.0000 2020-03-02
    ## 2547                        Hubei Mainland China  30.97560  112.2707 2020-03-02
    ## 2548              King County, WA             US  47.60620 -122.3321 2020-03-02
    ## 2549         Snohomish County, WA             US  48.03300 -121.8339 2020-03-02
    ## 2639                                      France  47.00000    2.0000 2020-03-03
    ## 2640                                        Iran  32.00000   53.0000 2020-03-03
    ## 2641                                       Italy  43.00000   12.0000 2020-03-03
    ## 2642                                  San Marino  43.94240   12.4578 2020-03-03
    ## 2643                                       Spain  40.00000   -4.0000 2020-03-03
    ## 2644                        Hubei Mainland China  30.97560  112.2707 2020-03-03
    ## 2645               Inner Mongolia Mainland China  44.09350  113.9448 2020-03-03
    ## 2646              King County, WA             US  47.60620 -122.3321 2020-03-03
    ## 2740                                        Iran  32.00000   53.0000 2020-03-04
    ## 2741                                        Iraq  33.00000   44.0000 2020-03-04
    ## 2742                                       Italy  43.00000   12.0000 2020-03-04
    ## 2743                                 South Korea  36.00000  128.0000 2020-03-04
    ## 2744                                       Spain  40.00000   -4.0000 2020-03-04
    ## 2745                        Hubei Mainland China  30.97560  112.2707 2020-03-04
    ## 2746              King County, WA             US  47.60620 -122.3321 2020-03-04
    ## 2747              New South Wales      Australia -33.86880  151.2093 2020-03-04
    ## 2748            Placer County, CA             US  39.09160 -120.8039 2020-03-04
    ## 2851                                      France  47.00000    2.0000 2020-03-05
    ## 2852                                        Iran  32.00000   53.0000 2020-03-05
    ## 2853                                       Italy  43.00000   12.0000 2020-03-05
    ## 2854                                       Spain  40.00000   -4.0000 2020-03-05
    ## 2855                                 Switzerland  46.81820    8.2275 2020-03-05
    ## 2856                                          UK  55.00000   -3.0000 2020-03-05
    ## 2857                       Hainan Mainland China  19.19590  109.7453 2020-03-05
    ## 2858                        Hubei Mainland China  30.97560  112.2707 2020-03-05
    ## 2859              King County, WA             US  47.60620 -122.3321 2020-03-05
    ##      cases  type
    ## 30      17 death
    ## 60       1 death
    ## 94       1 death
    ## 95       7 death
    ## 133     16 death
    ## 178      1 death
    ## 179     12 death
    ## 180      1 death
    ## 222      1 death
    ## 223      1 death
    ## 224     24 death
    ## 266     49 death
    ## 305      1 death
    ## 306      1 death
    ## 357      1 death
    ## 358     37 death
    ## 413     42 death
    ## 468      1 death
    ## 469     45 death
    ## 525      1 death
    ## 526      1 death
    ## 527    101 death
    ## 580     64 death
    ## 638      1 death
    ## 639     65 death
    ## 695      1 death
    ## 696     70 death
    ## 697      1 death
    ## 758      1 death
    ## 759     69 death
    ## 827      1 death
    ## 828      1 death
    ## 829      1 death
    ## 830     81 death
    ## 831      1 death
    ## 895      1 death
    ## 896      1 death
    ## 897      2 death
    ## 898      1 death
    ## 899     81 death
    ## 900      1 death
    ## 965      1 death
    ## 966      1 death
    ## 967      1 death
    ## 968      1 death
    ## 969      1 death
    ## 970      1 death
    ## 971      2 death
    ## 972     91 death
    ## 973      1 death
    ## 1037     2 death
    ## 1038     1 death
    ## 1039   103 death
    ## 1040     1 death
    ## 1101     1 death
    ## 1102     1 death
    ## 1103     1 death
    ## 1104     1 death
    ## 1105     1 death
    ## 1106    94 death
    ## 1107     1 death
    ## 1174     1 death
    ## 1175     1 death
    ## 1176     1 death
    ## 1177     1 death
    ## 1178     1 death
    ## 1254     1 death
    ## 1255     1 death
    ## 1256     1 death
    ## 1257     1 death
    ## 1258     1 death
    ## 1259     1 death
    ## 1260     1 death
    ## 1261     2 death
    ## 1262   242 death
    ## 1263     1 death
    ## 1264     1 death
    ## 1332     1 death
    ## 1333     1 death
    ## 1334     2 death
    ## 1335     1 death
    ## 1336   147 death
    ## 1396     1 death
    ## 1397     1 death
    ## 1398     2 death
    ## 1399   139 death
    ## 1471   100 death
    ## 1472     1 death
    ## 1473     2 death
    ## 1474     1 death
    ## 1541     2 death
    ## 1542     3 death
    ## 1543    93 death
    ## 1602     1 death
    ## 1603     1 death
    ## 1604     3 death
    ## 1605   132 death
    ## 1606     1 death
    ## 1607     1 death
    ## 1668     2 death
    ## 1669     1 death
    ## 1670     1 death
    ## 1671     1 death
    ## 1672   108 death
    ## 1673     1 death
    ## 1674     1 death
    ## 1734     1 death
    ## 1735     1 death
    ## 1736     2 death
    ## 1737     1 death
    ## 1738     1 death
    ## 1739   115 death
    ## 1740     1 death
    ## 1741     1 death
    ## 1742     1 death
    ## 1743     1 death
    ## 1805     2 death
    ## 1806     1 death
    ## 1807     1 death
    ## 1869     1 death
    ## 1870     1 death
    ## 1871     1 death
    ## 1872   202 death
    ## 1873     1 death
    ## 1874     1 death
    ## 1919     3 death
    ## 1920     1 death
    ## 1921     4 death
    ## 1922     1 death
    ## 1923     1 death
    ## 1924     1 death
    ## 1985     4 death
    ## 1986     4 death
    ## 1987     2 death
    ## 1988   149 death
    ## 1989     1 death
    ## 2048     4 death
    ## 2049     3 death
    ## 2050     2 death
    ## 2051     1 death
    ## 2052    68 death
    ## 2053     1 death
    ## 2121     1 death
    ## 2122     3 death
    ## 2123     2 death
    ## 2124     1 death
    ## 2125     2 death
    ## 2126     1 death
    ## 2127    52 death
    ## 2195     7 death
    ## 2196     5 death
    ## 2197     2 death
    ## 2198     1 death
    ## 2199     1 death
    ## 2200     1 death
    ## 2201     1 death
    ## 2202    26 death
    ## 2269     8 death
    ## 2270     4 death
    ## 2271     2 death
    ## 2272     2 death
    ## 2273    41 death
    ## 2274     1 death
    ## 2358     9 death
    ## 2359     8 death
    ## 2360     1 death
    ## 2361     3 death
    ## 2362     1 death
    ## 2363     1 death
    ## 2364    45 death
    ## 2365     1 death
    ## 2447    11 death
    ## 2448     5 death
    ## 2449     1 death
    ## 2450     1 death
    ## 2451     1 death
    ## 2452     1 death
    ## 2453    34 death
    ## 2454     1 death
    ## 2543     1 death
    ## 2544    12 death
    ## 2545    18 death
    ## 2546    11 death
    ## 2547    42 death
    ## 2548     4 death
    ## 2549     1 death
    ## 2639     1 death
    ## 2640    11 death
    ## 2641    27 death
    ## 2642     1 death
    ## 2643     1 death
    ## 2644    32 death
    ## 2645     1 death
    ## 2646     1 death
    ## 2740    15 death
    ## 2741     2 death
    ## 2742    28 death
    ## 2743     7 death
    ## 2744     1 death
    ## 2745    36 death
    ## 2746     3 death
    ## 2747     1 death
    ## 2748     1 death
    ## 2851     2 death
    ## 2852    15 death
    ## 2853    41 death
    ## 2854     1 death
    ## 2855     1 death
    ## 2856     1 death
    ## 2857     1 death
    ## 2858    31 death
    ## 2859     1 death

``` r
sum(virus[inds, "cases"])
```

    ## [1] 3348

``` r
total_cases <- sum(virus$cases)
```

## Q3. What is the overall death rate?

inds \<- virus$type == “death”

``` r
death_cases <- sum(virus[inds, "cases"])
death_cases
```

    ## [1] 3348

``` r
round(death_cases/total_cases *100, 2)
```

    ## [1] 2.16

## Q4. What is the death rate in China?

``` r
table(virus$Country.Region)
```

    ## 
    ##            Afghanistan                Algeria                Andorra 
    ##                      1                      4                      1 
    ##              Argentina                Armenia              Australia 
    ##                      1                      1                     44 
    ##                Austria             Azerbaijan                Bahrain 
    ##                      8                      2                      9 
    ##                Belarus                Belgium Bosnia and Herzegovina 
    ##                      2                      7                      1 
    ##                 Brazil               Cambodia                 Canada 
    ##                      3                      2                     25 
    ##                  Chile                Croatia         Czech Republic 
    ##                      2                      7                      4 
    ##                Denmark     Dominican Republic                Ecuador 
    ##                      5                      1                      4 
    ##                  Egypt                Estonia          Faroe Islands 
    ##                      4                      3                      1 
    ##                Finland                 France                Georgia 
    ##                      6                     26                      3 
    ##                Germany              Gibraltar                 Greece 
    ##                     24                      1                      6 
    ##              Hong Kong                Hungary                Iceland 
    ##                     50                      1                      6 
    ##                  India              Indonesia                   Iran 
    ##                      7                      1                     38 
    ##                   Iraq                Ireland                 Israel 
    ##                      9                      3                     10 
    ##                  Italy                  Japan                 Jordan 
    ##                     41                     48                      1 
    ##                 Kuwait                 Latvia                Lebanon 
    ##                      7                      1                      7 
    ##          Liechtenstein              Lithuania             Luxembourg 
    ##                      1                      1                      1 
    ##                  Macau         Mainland China               Malaysia 
    ##                     15                   1964                     22 
    ##                 Mexico                 Monaco                Morocco 
    ##                      4                      1                      2 
    ##                  Nepal            Netherlands            New Zealand 
    ##                      2                      7                      2 
    ##                Nigeria        North Macedonia                 Norway 
    ##                      1                      1                      8 
    ##                   Oman                 Others               Pakistan 
    ##                      8                     21                      3 
    ##              Palestine            Philippines                 Poland 
    ##                      1                      5                      1 
    ##               Portugal                  Qatar                Romania 
    ##                      3                      4                      5 
    ##                 Russia       Saint Barthelemy             San Marino 
    ##                      4                      1                      6 
    ##           Saudi Arabia                Senegal              Singapore 
    ##                      2                      3                     47 
    ##               Slovenia           South Africa            South Korea 
    ##                      1                      1                     55 
    ##                  Spain              Sri Lanka                 Sweden 
    ##                     16                      2                      9 
    ##            Switzerland                 Taiwan               Thailand 
    ##                     11                     33                     30 
    ##                Tunisia                     UK                Ukraine 
    ##                      1                     16                      1 
    ##   United Arab Emirates                     US                Vietnam 
    ##                     14                     99                     13

``` r
virus$Country.Region == "Mainland China"
```

    ##    [1] FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##   [13]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ##   [25]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE
    ##   [37]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE
    ##   [49]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##   [61]  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE
    ##   [73]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##   [85]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##   [97]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [109]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [121]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [133]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE
    ##  [145]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE
    ##  [157]  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ##  [169]  TRUE FALSE FALSE  TRUE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [181] FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE
    ##  [193]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [205]  TRUE  TRUE  TRUE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [217] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [229] FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ##  [241]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [253]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE
    ##  [265]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE
    ##  [277] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [289] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ##  [301]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [313]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE
    ##  [325]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [337]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ##  [349]  TRUE FALSE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [361]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE
    ##  [373] FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ##  [385]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [397] FALSE  TRUE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE FALSE
    ##  [409] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [421]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
    ##  [433] FALSE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [445]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ##  [457]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ##  [469]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [481]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE
    ##  [493]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE
    ##  [505]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE  TRUE  TRUE
    ##  [517]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE
    ##  [529]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [541]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [553]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [565]  TRUE  TRUE  TRUE  TRUE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [577]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [589]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE
    ##  [601] FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [613]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ##  [625]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE
    ##  [637]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [649]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [661] FALSE FALSE FALSE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [673]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [685] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [697]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [709]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [721]  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [733]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [745]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE
    ##  [757]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [769]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE
    ##  [781]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
    ##  [793] FALSE  TRUE  TRUE FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [805]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [817] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [829]  TRUE  TRUE  TRUE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [841]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [853]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
    ##  [865]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [877] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [889]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [901] FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [913]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [925]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE
    ##  [937] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE
    ##  [949]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ##  [961]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [973]  TRUE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ##  [985]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ##  [997]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE
    ## [1009]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ## [1021]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1033]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE
    ## [1045]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1057]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE
    ## [1069] FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1081]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE
    ## [1093]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1105]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1117]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1129]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1141] FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1153]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1165]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1177]  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [1189]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1201] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE  TRUE  TRUE
    ## [1213]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE
    ## [1225]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE
    ## [1237]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE  TRUE  TRUE  TRUE
    ## [1249]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1261]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1273]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1285]  TRUE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE
    ## [1297]  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE
    ## [1309]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1321]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1333]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1345]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1357]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE
    ## [1369]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1381]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1393]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE
    ## [1405] FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1417]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1429]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE
    ## [1441] FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1453] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1465]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE
    ## [1477] FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1489]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE
    ## [1501]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE
    ## [1513]  TRUE FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1525]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1537] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE
    ## [1549]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1561]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ## [1573]  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE
    ## [1585]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1597]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ## [1609] FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1621]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1633]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE
    ## [1645]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE
    ## [1657]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE
    ## [1669]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE  TRUE
    ## [1681] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE
    ## [1693]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1705]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE
    ## [1717]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1729]  TRUE FALSE  TRUE  TRUE  TRUE FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ## [1741]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1753]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1765] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ## [1777] FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE  TRUE FALSE  TRUE
    ## [1789]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE FALSE FALSE FALSE  TRUE  TRUE
    ## [1801] FALSE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [1813]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1825] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE
    ## [1837] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE
    ## [1849] FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ## [1861] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE  TRUE  TRUE
    ## [1873]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1885]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1897]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE
    ## [1909]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE FALSE FALSE
    ## [1921] FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE
    ## [1933]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE
    ## [1945]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [1957]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [1969] FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE FALSE  TRUE  TRUE  TRUE
    ## [1981] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE  TRUE
    ## [1993]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE
    ## [2005]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2017] FALSE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2029] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE  TRUE
    ## [2041]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE
    ## [2053]  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2065]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2077] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE
    ## [2089] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2101] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2113] FALSE  TRUE FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2125] FALSE FALSE  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE
    ## [2137]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ## [2149]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2161]  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2173] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE
    ## [2185]  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE FALSE FALSE FALSE
    ## [2197] FALSE FALSE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE FALSE
    ## [2209]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2221]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2233]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2245] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2257] FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE FALSE FALSE
    ## [2269] FALSE FALSE  TRUE FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE
    ## [2281]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ## [2293]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ## [2305]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2317] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2329] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE
    ## [2341] FALSE FALSE  TRUE FALSE  TRUE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE
    ## [2353] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE
    ## [2365] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2377]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2389]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
    ## [2401] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2413] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2425] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
    ## [2437] FALSE  TRUE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE
    ## [2449] FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE
    ## [2461]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE
    ## [2473]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2485]  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2497] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2509] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE
    ## [2521]  TRUE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE
    ## [2533] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE
    ## [2545] FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE
    ## [2557]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2569]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE
    ## [2581] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2593] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2605] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2617] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE FALSE
    ## [2629] FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE
    ## [2641] FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2653]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE
    ## [2665]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE  TRUE  TRUE  TRUE  TRUE
    ## [2677]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2689] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2701] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2713] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE
    ## [2725] FALSE FALSE FALSE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE
    ## [2737] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE
    ## [2749] FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2761]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2773]  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2785] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2797] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2809] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2821] FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE  TRUE  TRUE
    ## [2833] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE
    ## [2845] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2857]  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [2869]  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE
    ## [2881]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE

## number of total cases in `Mainland.China`

``` r
sum(virus[virus$Country.Region == "Mainland China", "cases"])
```

    ## [1] 135675

``` r
China_total <- sum(virus[virus$Country.Region == "Mainland China", "cases"])
```

## number of total deaths in `Mainland.China`

``` r
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 3.6.3

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
dplyr::filter(virus, Country.Region == "Mainland China", virus$type == "death")
```

    ##     Province.State Country.Region      Lat     Long       date cases  type
    ## 1            Hubei Mainland China 30.97560 112.2707 2020-01-22    17 death
    ## 2            Hebei Mainland China 38.04280 114.5149 2020-01-23     1 death
    ## 3     Heilongjiang Mainland China 47.86200 127.7615 2020-01-24     1 death
    ## 4            Hubei Mainland China 30.97560 112.2707 2020-01-24     7 death
    ## 5            Hubei Mainland China 30.97560 112.2707 2020-01-25    16 death
    ## 6            Henan Mainland China 33.88202 113.6140 2020-01-26     1 death
    ## 7            Hubei Mainland China 30.97560 112.2707 2020-01-26    12 death
    ## 8         Shanghai Mainland China 31.20200 121.4491 2020-01-26     1 death
    ## 9          Beijing Mainland China 40.18240 116.4142 2020-01-27     1 death
    ## 10          Hainan Mainland China 19.19590 109.7453 2020-01-27     1 death
    ## 11           Hubei Mainland China 30.97560 112.2707 2020-01-27    24 death
    ## 12           Hubei Mainland China 30.97560 112.2707 2020-01-28    49 death
    ## 13           Henan Mainland China 33.88202 113.6140 2020-01-29     1 death
    ## 14         Sichuan Mainland China 30.61710 102.7103 2020-01-29     1 death
    ## 15    Heilongjiang Mainland China 47.86200 127.7615 2020-01-30     1 death
    ## 16           Hubei Mainland China 30.97560 112.2707 2020-01-30    37 death
    ## 17           Hubei Mainland China 30.97560 112.2707 2020-01-31    42 death
    ## 18       Chongqing Mainland China 30.05720 107.8740 2020-02-01     1 death
    ## 19           Hubei Mainland China 30.97560 112.2707 2020-02-01    45 death
    ## 20       Chongqing Mainland China 30.05720 107.8740 2020-02-02     1 death
    ## 21           Hubei Mainland China 30.97560 112.2707 2020-02-02   101 death
    ## 22           Hubei Mainland China 30.97560 112.2707 2020-02-03    64 death
    ## 23           Hubei Mainland China 30.97560 112.2707 2020-02-04    65 death
    ## 24         Guizhou Mainland China 26.81540 106.8748 2020-02-05     1 death
    ## 25           Hubei Mainland China 30.97560 112.2707 2020-02-05    70 death
    ## 26         Tianjin Mainland China 39.30540 117.3230 2020-02-05     1 death
    ## 27    Heilongjiang Mainland China 47.86200 127.7615 2020-02-06     1 death
    ## 28           Hubei Mainland China 30.97560 112.2707 2020-02-06    69 death
    ## 29       Guangdong Mainland China 23.34170 113.4244 2020-02-07     1 death
    ## 30          Hainan Mainland China 19.19590 109.7453 2020-02-07     1 death
    ## 31           Henan Mainland China 33.88202 113.6140 2020-02-07     1 death
    ## 32           Hubei Mainland China 30.97560 112.2707 2020-02-07    81 death
    ## 33           Jilin Mainland China 43.66610 126.1923 2020-02-07     1 death
    ## 34         Beijing Mainland China 40.18240 116.4142 2020-02-08     1 death
    ## 35           Gansu Mainland China 36.06110 103.8343 2020-02-08     1 death
    ## 36    Heilongjiang Mainland China 47.86200 127.7615 2020-02-08     2 death
    ## 37           Henan Mainland China 33.88202 113.6140 2020-02-08     1 death
    ## 38           Hubei Mainland China 30.97560 112.2707 2020-02-08    81 death
    ## 39           Hunan Mainland China 27.61040 111.7088 2020-02-08     1 death
    ## 40           Anhui Mainland China 31.82570 117.2264 2020-02-09     1 death
    ## 41           Gansu Mainland China 36.06110 103.8343 2020-02-09     1 death
    ## 42         Guangxi Mainland China 23.82980 108.7881 2020-02-09     1 death
    ## 43          Hainan Mainland China 19.19590 109.7453 2020-02-09     1 death
    ## 44           Hebei Mainland China 38.04280 114.5149 2020-02-09     1 death
    ## 45    Heilongjiang Mainland China 47.86200 127.7615 2020-02-09     1 death
    ## 46           Henan Mainland China 33.88202 113.6140 2020-02-09     2 death
    ## 47           Hubei Mainland China 30.97560 112.2707 2020-02-09    91 death
    ## 48        Shandong Mainland China 36.34270 118.1498 2020-02-09     1 death
    ## 49           Anhui Mainland China 31.82570 117.2264 2020-02-10     2 death
    ## 50    Heilongjiang Mainland China 47.86200 127.7615 2020-02-10     1 death
    ## 51           Hubei Mainland China 30.97560 112.2707 2020-02-10   103 death
    ## 52         Jiangxi Mainland China 27.61400 115.7221 2020-02-10     1 death
    ## 53           Anhui Mainland China 31.82570 117.2264 2020-02-11     1 death
    ## 54         Beijing Mainland China 40.18240 116.4142 2020-02-11     1 death
    ## 55       Chongqing Mainland China 30.05720 107.8740 2020-02-11     1 death
    ## 56    Heilongjiang Mainland China 47.86200 127.7615 2020-02-11     1 death
    ## 57           Henan Mainland China 33.88202 113.6140 2020-02-11     1 death
    ## 58           Hubei Mainland China 30.97560 112.2707 2020-02-11    94 death
    ## 59         Tianjin Mainland China 39.30540 117.3230 2020-02-11     1 death
    ## 60          Hainan Mainland China 19.19590 109.7453 2020-02-12     1 death
    ## 61           Henan Mainland China 33.88202 113.6140 2020-02-12     1 death
    ## 62           Hunan Mainland China 27.61040 111.7088 2020-02-12     1 death
    ## 63        Liaoning Mainland China 41.29560 122.6085 2020-02-12     1 death
    ## 64        Shandong Mainland China 36.34270 118.1498 2020-02-12     1 death
    ## 65           Anhui Mainland China 31.82570 117.2264 2020-02-13     1 death
    ## 66       Chongqing Mainland China 30.05720 107.8740 2020-02-13     1 death
    ## 67       Guangdong Mainland China 23.34170 113.4244 2020-02-13     1 death
    ## 68         Guangxi Mainland China 23.82980 108.7881 2020-02-13     1 death
    ## 69           Hebei Mainland China 38.04280 114.5149 2020-02-13     1 death
    ## 70    Heilongjiang Mainland China 47.86200 127.7615 2020-02-13     1 death
    ## 71           Henan Mainland China 33.88202 113.6140 2020-02-13     2 death
    ## 72           Hubei Mainland China 30.97560 112.2707 2020-02-13   242 death
    ## 73         Tianjin Mainland China 39.30540 117.3230 2020-02-13     1 death
    ## 74        Xinjiang Mainland China 41.11290  85.2401 2020-02-13     1 death
    ## 75           Anhui Mainland China 31.82570 117.2264 2020-02-14     1 death
    ## 76       Chongqing Mainland China 30.05720 107.8740 2020-02-14     1 death
    ## 77    Heilongjiang Mainland China 47.86200 127.7615 2020-02-14     2 death
    ## 78           Henan Mainland China 33.88202 113.6140 2020-02-14     1 death
    ## 79           Hubei Mainland China 30.97560 112.2707 2020-02-14   147 death
    ## 80         Beijing Mainland China 40.18240 116.4142 2020-02-15     1 death
    ## 81           Henan Mainland China 33.88202 113.6140 2020-02-15     2 death
    ## 82           Hubei Mainland China 30.97560 112.2707 2020-02-15   139 death
    ## 83           Hubei Mainland China 30.97560 112.2707 2020-02-16   100 death
    ## 84           Hunan Mainland China 27.61040 111.7088 2020-02-16     1 death
    ## 85         Sichuan Mainland China 30.61710 102.7103 2020-02-16     2 death
    ## 86       Guangdong Mainland China 23.34170 113.4244 2020-02-17     2 death
    ## 87           Henan Mainland China 33.88202 113.6140 2020-02-17     3 death
    ## 88           Hubei Mainland China 30.97560 112.2707 2020-02-17    93 death
    ## 89         Guizhou Mainland China 26.81540 106.8748 2020-02-18     1 death
    ## 90           Hebei Mainland China 38.04280 114.5149 2020-02-18     1 death
    ## 91           Henan Mainland China 33.88202 113.6140 2020-02-18     3 death
    ## 92           Hubei Mainland China 30.97560 112.2707 2020-02-18   132 death
    ## 93           Hunan Mainland China 27.61040 111.7088 2020-02-18     1 death
    ## 94        Shandong Mainland China 36.34270 118.1498 2020-02-18     1 death
    ## 95       Guangdong Mainland China 23.34170 113.4244 2020-02-19     1 death
    ## 96    Heilongjiang Mainland China 47.86200 127.7615 2020-02-19     1 death
    ## 97           Hubei Mainland China 30.97560 112.2707 2020-02-19   108 death
    ## 98        Shanghai Mainland China 31.20200 121.4491 2020-02-19     1 death
    ## 99          Yunnan Mainland China 24.97400 101.4870 2020-02-19     1 death
    ## 100      Chongqing Mainland China 30.05720 107.8740 2020-02-20     1 death
    ## 101         Fujian Mainland China 26.07890 117.9874 2020-02-20     1 death
    ## 102          Hebei Mainland China 38.04280 114.5149 2020-02-20     1 death
    ## 103          Hubei Mainland China 30.97560 112.2707 2020-02-20   115 death
    ## 104        Shaanxi Mainland China 35.19170 108.8701 2020-02-20     1 death
    ## 105       Shandong Mainland China 36.34270 118.1498 2020-02-20     1 death
    ## 106         Yunnan Mainland China 24.97400 101.4870 2020-02-20     1 death
    ## 107       Zhejiang Mainland China 29.18320 120.0934 2020-02-20     1 death
    ## 108          Hebei Mainland China 38.04280 114.5149 2020-02-22     1 death
    ## 109          Hubei Mainland China 30.97560 112.2707 2020-02-22   202 death
    ## 110       Shanghai Mainland China 31.20200 121.4491 2020-02-22     1 death
    ## 111       Xinjiang Mainland China 41.11290  85.2401 2020-02-22     1 death
    ## 112      Guangdong Mainland China 23.34170 113.4244 2020-02-23     1 death
    ## 113         Hainan Mainland China 19.19590 109.7453 2020-02-23     1 death
    ## 114          Hubei Mainland China 30.97560 112.2707 2020-02-24   149 death
    ## 115       Shandong Mainland China 36.34270 118.1498 2020-02-24     1 death
    ## 116      Guangdong Mainland China 23.34170 113.4244 2020-02-25     1 death
    ## 117          Hubei Mainland China 30.97560 112.2707 2020-02-25    68 death
    ## 118       Shandong Mainland China 36.34270 118.1498 2020-02-25     1 death
    ## 119          Hubei Mainland China 30.97560 112.2707 2020-02-26    52 death
    ## 120        Beijing Mainland China 40.18240 116.4142 2020-02-27     1 death
    ## 121   Heilongjiang Mainland China 47.86200 127.7615 2020-02-27     1 death
    ## 122          Henan Mainland China 33.88202 113.6140 2020-02-27     1 death
    ## 123          Hubei Mainland China 30.97560 112.2707 2020-02-27    26 death
    ## 124        Beijing Mainland China 40.18240 116.4142 2020-02-28     2 death
    ## 125          Hubei Mainland China 30.97560 112.2707 2020-02-28    41 death
    ## 126       Xinjiang Mainland China 41.11290  85.2401 2020-02-28     1 death
    ## 127        Beijing Mainland China 40.18240 116.4142 2020-02-29     1 death
    ## 128          Henan Mainland China 33.88202 113.6140 2020-02-29     1 death
    ## 129          Hubei Mainland China 30.97560 112.2707 2020-02-29    45 death
    ## 130          Henan Mainland China 33.88202 113.6140 2020-03-01     1 death
    ## 131          Hubei Mainland China 30.97560 112.2707 2020-03-01    34 death
    ## 132          Hubei Mainland China 30.97560 112.2707 2020-03-02    42 death
    ## 133          Hubei Mainland China 30.97560 112.2707 2020-03-03    32 death
    ## 134 Inner Mongolia Mainland China 44.09350 113.9448 2020-03-03     1 death
    ## 135          Hubei Mainland China 30.97560 112.2707 2020-03-04    36 death
    ## 136         Hainan Mainland China 19.19590 109.7453 2020-03-05     1 death
    ## 137          Hubei Mainland China 30.97560 112.2707 2020-03-05    31 death

``` r
virus[virus$Country.Region == "Mainland China" & virus$type == "death", "cases"]
```

    ##   [1]  17   1   1   7  16   1  12   1   1   1  24  49   1   1   1  37  42   1
    ##  [19]  45   1 101  64  65   1  70   1   1  69   1   1   1  81   1   1   1   2
    ##  [37]   1  81   1   1   1   1   1   1   1   2  91   1   2   1 103   1   1   1
    ##  [55]   1   1   1  94   1   1   1   1   1   1   1   1   1   1   1   1   2 242
    ##  [73]   1   1   1   1   2   1 147   1   2 139 100   1   2   2   3  93   1   1
    ##  [91]   3 132   1   1   1   1 108   1   1   1   1   1 115   1   1   1   1   1
    ## [109] 202   1   1   1   1 149   1   1  68   1  52   1   1   1  26   2  41   1
    ## [127]   1   1  45   1  34  42  32   1  36   1  31

``` r
sum(virus[virus$Country.Region == "Mainland China" & virus$type == "death", "cases"])
```

    ## [1] 3013

``` r
China_deaths <- sum(virus[virus$Country.Region == "Mainland China" & virus$type == "death", "cases"])
```

## rate of `Mainland.China` deaths

``` r
round(China_deaths/China_total * 100, 2)
```

    ## [1] 2.22

## Q5. What is the death rate in Italy, Iran and the US?

\#\#italy

## number of deaths in Italy

``` r
sum(virus[virus$Country.Region == "Italy" & virus$type == "death", "cases"])
```

    ## [1] 148

``` r
Italy_deaths <- sum(virus[virus$Country.Region == "Italy" & virus$type == "death", "cases"])
```

\#\#use this for total cases

``` r
virus[virus$Country.Region == "Italy", "cases"]
```

    ##  [1]   2   1  17   1  42   1   1  93   1   1  74   4  -1  93   3 131   2   2 202
    ## [20]   5  42 233   4   1 240   8 566   5  37 342  18  66 466  27  11 587  28 116
    ## [39] 769  41 138

\#\#use this for total cases

``` r
sum(virus[virus$Country.Region == "Italy", "cases"])
```

    ## [1] 4420

``` r
Italy_total <- sum(virus[virus$Country.Region == "Italy", "cases"])
```

``` r
round(Italy_deaths/Italy_total * 100, 2)
```

    ## [1] 3.35

\#\#Iran

## number of deaths in Iran

``` r
sum(virus[virus$Country.Region == "Iran" & virus$type == "death", "cases"])
```

    ## [1] 107

``` r
Iran_deaths <- sum(virus[virus$Country.Region == "Iran" & virus$type == "death", "cases"])
```

\#\#use this for total cases

``` r
sum(virus[virus$Country.Region == "Iran", "cases"])
```

    ## [1] 4359

``` r
Iran_total <- sum(virus[virus$Country.Region == "Iran", "cases"])
```

``` r
round(Iran_deaths/Iran_total * 100, 2)
```

    ## [1] 2.45

\#US

``` r
sum(virus[virus$Country.Region == "US" & virus$type == "death", "cases"])
```

    ## [1] 12

``` r
US_deaths <- sum(virus[virus$Country.Region == "US" & virus$type == "death", "cases"])
```

\#\#use this for total cases

``` r
sum(virus[virus$Country.Region == "US", "cases"])
```

    ## [1] 241

``` r
US_total <- sum(virus[virus$Country.Region == "US", "cases"])
```

``` r
round(US_deaths/US_total * 100, 2)
```

    ## [1] 4.98
