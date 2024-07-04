封包測試是開一個 kali linux 充當 C2 Server (IP 要改成 C2 IP)
使用 pwntools
```
from pwn import *
l = listen(80)

data_from_client = l.recv()
```
上面這樣就可以拿到 client 傳過來的資料
