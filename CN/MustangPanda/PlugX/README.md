
# 總結

- loader 解密 payload 的方式跟 payload 解 config 方式雷同

# 收集

[1]
- 來源：hunt from vt
- 執行方式：dll sideLoading
- launcher: `LMIGuardianSvc.exe`
- loader: `LMIGuardianDll.dll`
  - export function: 很多垃圾，有用的是 `Init` function
  - decrypt shellcode: `xor`
  - 執行 shellcode 方式：`EnumSystemCodePagesW` 
- payload: `test.msd`
  - decrypt config data use: `xor`  


# 參考
- [1] [2022.12.27 - Diving into a PlugX sample of Mustang Panda group](https://kienmanowar.wordpress.com/2022/12/27/diving-into-a-plugx-sample-of-mustang-panda-group/)
