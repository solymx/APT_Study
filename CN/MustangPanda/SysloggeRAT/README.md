## Summary

- 從 CrowdStrike 看到
- go binary
- windows , linux 版本都有

## 看 c2
函數：`main_init`
這邊注意大小寫，會有另一個是 `main_Init` 這是不對的

進去第一個函數會拿到 malware version
(下斷點在進去第一個函數：`runtime_slicebytetostring`)
