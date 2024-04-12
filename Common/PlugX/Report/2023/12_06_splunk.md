[url](https://www.splunk.com/en_us/blog/security/unmasking-the-enigma-a-historical-dive-into-the-world-of-plugx-malware.html)

# 概述

launcher: msbtc.exe
loader: version.dll
payload: msbtc.dat

loader 的 export function: `VerQueryValueW` 用 RC4 解 payload

進入 shellcode 會經過一連串的運算

最後透過 `RtlDecompressBuffer` 做解壓縮，得到一個沒有 header 的 shellcode 之後會注入到其他 process 中

# 分析
