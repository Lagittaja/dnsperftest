# DNS Performance Test

Shell script to test the performance of the most popular DNS resolvers from your location.

Includes by default:
 * CloudFlare 1.1.1.1
 * Google 8.8.8.8
 * Quad9 9.9.9.9
 * OpenDNS
 * Norton
 * CleanBrowsing
 * Yandex
 * AdGuard
 * Neustar
 * Comodo

# Required 

You need to install bc and dig. For Ubuntu:

```
 $ sudo apt-get install bc dnsutils
```

# Utilization

``` 
 $ git clone --depth=1 https://github.com/Lagittaja/dnsperftest/
 $ cd dnsperftest
 $ bash ./dnstest.sh 
                  test1   test2   test3   test4   test5   test6   test7   test8   test9   test10  test11  test12  test13  test14  test15   Average
cloudflare        14 ms   14 ms   14 ms   14 ms   17 ms   13 ms   13 ms   13 ms   14 ms   13 ms   17 ms   15 ms   14 ms   14 ms   13 ms     14.13
google            31 ms   19 ms   18 ms   19 ms   19 ms   42 ms   21 ms   19 ms   19 ms   46 ms   19 ms   26 ms   40 ms   65 ms   91 ms     32.93
quad9             33 ms   33 ms   34 ms   144 ms  32 ms   34 ms   35 ms   62 ms   34 ms   36 ms   33 ms   145 ms  69 ms   188 ms  32 ms     62.93
opendns           57 ms   59 ms   40 ms   43 ms   150 ms  58 ms   41 ms   38 ms   38 ms   59 ms   41 ms   39 ms   57 ms   55 ms   39 ms     54.26
norton            43 ms   44 ms   43 ms   44 ms   48 ms   44 ms   44 ms   43 ms   42 ms   44 ms   44 ms   43 ms   44 ms   45 ms   44 ms     43.93
cleanbrowsing     118 ms  118 ms  122 ms  118 ms  118 ms  189 ms  120 ms  122 ms  117 ms  151 ms  114 ms  141 ms  271 ms  141 ms  118 ms    138.53
yandex            26 ms   19 ms   25 ms   85 ms   135 ms  85 ms   25 ms   132 ms  55 ms   214 ms  26 ms   20 ms   1000 ms 93 ms   129 ms    137.93
adguard           32 ms   32 ms   30 ms   30 ms   30 ms   84 ms   32 ms   31 ms   49 ms   182 ms  30 ms   36 ms   74 ms   94 ms   48 ms     54.26
neustar           42 ms   43 ms   42 ms   44 ms   44 ms   43 ms   45 ms   46 ms   43 ms   43 ms   47 ms   44 ms   42 ms   43 ms   43 ms     43.60
comodo            48 ms   52 ms   53 ms   49 ms   49 ms   68 ms   49 ms   48 ms   48 ms   70 ms   51 ms   49 ms   114 ms  61 ms   48 ms     57.13
```

To sort with the fastest first, add `sort -k 32 -n` at the end of the command:

```
  $ bash ./dnstest.sh |sort -k 32 -n
                  test1   test2   test3   test4   test5   test6   test7   test8   test9   test10  test11  test12  test13  test14  test15   Average
cloudflare        14 ms   15 ms   13 ms   14 ms   18 ms   16 ms   16 ms   14 ms   13 ms   14 ms   13 ms   13 ms   13 ms   13 ms   14 ms     14.20
google            29 ms   29 ms   19 ms   18 ms   64 ms   29 ms   20 ms   29 ms   18 ms   65 ms   21 ms   20 ms   42 ms   29 ms   97 ms     35.26
neustar           43 ms   42 ms   43 ms   43 ms   44 ms   44 ms   44 ms   43 ms   44 ms   44 ms   43 ms   45 ms   43 ms   45 ms   43 ms     43.53
adguard           30 ms   31 ms   29 ms   29 ms   31 ms   29 ms   36 ms   31 ms   51 ms   46 ms   45 ms   37 ms   31 ms   40 ms   161 ms    43.80
norton            43 ms   43 ms   43 ms   44 ms   49 ms   45 ms   53 ms   44 ms   43 ms   46 ms   44 ms   43 ms   43 ms   45 ms   44 ms     44.80
opendns           40 ms   60 ms   39 ms   43 ms   41 ms   56 ms   43 ms   39 ms   39 ms   64 ms   40 ms   40 ms   86 ms   39 ms   39 ms     47.20
quad9             39 ms   32 ms   33 ms   69 ms   33 ms   142 ms  39 ms   33 ms   32 ms   37 ms   33 ms   33 ms   75 ms   141 ms  78 ms     56.60
yandex            25 ms   20 ms   20 ms   19 ms   25 ms   98 ms   20 ms   219 ms  54 ms   96 ms   27 ms   26 ms   122 ms  70 ms   66 ms     60.46
comodo            58 ms   60 ms   53 ms   50 ms   51 ms   50 ms   50 ms   216 ms  51 ms   49 ms   50 ms   51 ms   109 ms  48 ms   50 ms     66.40
cleanbrowsing     118 ms  118 ms  117 ms  120 ms  118 ms  117 ms  119 ms  118 ms  118 ms  118 ms  118 ms  118 ms  118 ms  118 ms  119 ms    118.13
```

# For Windows users using the Linux subsystem

If you receive an error `$'\r': command not found`, convert the file to a Linux-compatible line endings using:

    tr -d '\15\32' < dnstest.sh > dnstest-2.sh
    
Then run `bash ./dnstest-2.sh`
