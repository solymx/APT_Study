封包測試是開一個 kali linux 充當 C2 Server (IP 要改成 C2 IP)
使用 pwntools
```
from pwn import *
l = listen(80)

data_from_client = l.recv()
```
上面這樣就可以拿到 client 傳過來的資料

下面是我執行兩次，獲取 Client 報到的封包
```
In [13]: q
Out[13]: b'POST / HTTP/1.1\r\nContent-Type: application/x-www-form-urlencoded\r\nUser-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.6422.142 Safari/537.36\r\nHost: 167.179.66.89\r\nContent-Length: 233\r\nConnection: Keep-Alive\r\nCache-Control: no-cache\r\n\r\nPkdD=iUBausBQO_Zks3cMnBg7rij3fKGVGOx_lf0pHzZpWx7S4JUc69v6m10yuMi-CN6NuabUVWo6VPuKWlg1CDvghqd_dB05Xz8_Pz9BMfnH20eFa-X6GYs013ETtdeiTiB4fU4lEFJMkBVkBa3olnluMBtYLLyLZRH_rWAVUUuvUVhwY2_8pdcnfozXue9QkaQcvqYZ5DTEMrLIw-z2c-PC0tdU_JJOEKwai8Y.'

In [14]: qq
Out[14]: b'POST / HTTP/1.1\r\nContent-Type: application/x-www-form-urlencoded\r\nUser-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.6422.142 Safari/537.36\r\nHost: 167.179.66.89\r\nContent-Length: 233\r\nConnection: Keep-Alive\r\nCache-Control: no-cache\r\n\r\nawdD=D6BaPEBQ9_ZkNfcMINg7Muj3AWGVUxw3w_mRG6G0diWPxdNDR4SDsyWfQSSvMBU4b5QGxqCVm4vjf9ikjvs94Oi9m9Ne_JycnJyZcdBQ90YpizF2IZToLweK9-ZguiLvfJSH9vqRplAdNJ_9qWiqkTe1aK5JeecXN7V33eI3XUgNkPTGYUs1DI2zVfGb7tLYq_w6yuJ65GFVM7aVPoob-qsxC82DPrw_DkY.'

```
