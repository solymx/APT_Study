
樣本是 2023.10 拿到，沒在 VT 上面


# 惡意程式功能概述

1. 一開始會產 User-Agent 和受害者電腦資訊 (作為之後傳輸給 c2 的內容)
2. 用 hardcoded aes key 和 iv 透過 CBC-MODE ，之後是 QuickLZ Decompress ，解出兩個 c2 位置
3. 加密受害者電腦資訊，傳輸給 c2 做報告
4. 接收 c2 傳來的加密資料並解密
5. 執行後門指令
