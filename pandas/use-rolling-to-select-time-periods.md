# use rolling to select time periods
With a timeseries index, you can use .rolling to select time periods as the window. For example launched.rolling('7d') creates a rolling window that contains all the data in the previous 7 days. The window contains the current record, so if we want to count all the previous projects but not the current one, we'll need to subtract 1. We'll plot the results to make sure it looks right.

```python
count_7_days = launched.rolling('7d').count() - 1
print(count_7_days.head(20))

# Ignore records with broken launch dates
plt.plot(count_7_days[7:]);
plt.title("Competitions in the last 7 days");
```

```
launched
1970-01-01 01:00:00     0.0
1970-01-01 01:00:00     1.0
1970-01-01 01:00:00     2.0
1970-01-01 01:00:00     3.0
1970-01-01 01:00:00     4.0
1970-01-01 01:00:00     5.0
1970-01-01 01:00:00     6.0
2009-04-21 21:02:48     0.0
2009-04-23 00:07:53     1.0
2009-04-24 21:52:03     2.0
2009-04-25 17:36:21     3.0
2009-04-27 14:10:39     4.0
2009-04-28 13:55:41     5.0
2009-04-29 02:04:21     5.0
2009-04-29 02:58:50     6.0
2009-04-29 04:37:37     7.0
2009-04-29 05:26:32     8.0
2009-04-29 06:43:44     9.0
2009-04-29 13:52:03    10.0
2009-04-29 22:08:13    11.0
Name: count_7_days, dtype: float64
```

https://www.kaggleusercontent.com/kf/31657929/eyJhbGciOiJkaXIiLCJlbmMiOiJBMTI4Q0JDLUhTMjU2In0..DMCo4h4S8g1FYkGdNdcG-g.PtG6rWVeZYSoJzuLVF4M35qMs6hh-RJwnpqOWHPlybLrEZ7-m2PJtgtuRbOgsK6yDFRlmhVu8cRx96FDplsrXnwaDDoHtdjpYPXZsVMCAzs2_FG0xJ_UKpDMhAVvFVI9XRuKraoIFkMWnvkzT5gibGqlCpT-OzBH1xlOdnkuarDpA7HmfPXykI5va94SjByXZ5K4QVZSyDJvgWhCPm-_HL36U6dINw4W-dNQnCeNLWQRjpGwTu0mCSGF6d8bZTI2W0mst3M6QlM_evT0Mt0uC8cbbn5DbVY-Oxaei4Dtw5VIChD4t4oM2WpfcoywNsLIlk4U0Qxn9zImdtapJNaSq-0xBnTmKqsTXrLrgXC6c0uMhDOxHpK87VQyOdjfji9yoS-WXC89Sd3BVS7uWAlIpNkglyYTcSQ5loYwbhb4vgWZmbjRanjjCpuYE0kkPZ_NmXyKROreCATF4AH5fYSPHeIDkmocYoBlhmWwSgnonz5eIva_rV8xuwz623gTj16u8iYKYoca-TV3lVymLcgWw5zXDRrIx9BMSKVXVMDxoo18VxV1PQOvH4wHtIjPADxVAvKaNCqeOWNBbKqfypJ0HobTHyKJjBPDCH-hSV2PucvmYXJI1iQOfDRhLEEPFp_0iXuQnw66AcwGW2OJ7iweCTjj_wUEJsP6LgH1l8TiwfM.flbCkr3TUApDhfy5MGZv7g/__results___files/__results___11_1.png
