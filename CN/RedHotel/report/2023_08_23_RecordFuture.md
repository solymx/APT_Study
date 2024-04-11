[report url](https://go.recordedfuture.com/hubfs/reports/cta-2023-0808.pdf)

# 前言

觀察到至少 2019 年開始就有活動

有打到台灣

其他公司定義的名字
- Aquatic Panda(CrowdStrike)
- BRONZE UNIVERSITY (SecureWorks)
- Charcoal Typhoon (Microsoft)
- Earth Lusca (Trend Micro)
- Red Scylla (PWC)

活動目標
- 竊取資料

C2 infra 分 2 種：
- 初始進去
- 維持 c2 通訊

使用的工具
- 攻擊性安全工具
  - Cobalt Strike
  - Brute Ratel 
- 沒開源但分享的
  - ShadowPad
  - Winnti
- 客製化工具
  - Spyder
  - FunnySwitch

# 背景

因為使用常見的中國內部共用工具，如 Winnti 而難以去歸因

但因為有獨特的 TTP 和自定義的惡意程式，以此分類

相關報告
- 2021.07 報告跟[裡面有打台灣相關](https://www.recordedfuture.com/blog/chinese-group-tag-22-targets-nepal-philippines-taiwan)
  - 攻擊活動跟 [2020.01 ESET 報告](https://www.welivesecurity.com/2020/01/31/winnti-group-targeting-universities-hong-kong/)重疊
  - 同一時間 [AVAST](https://decoded.avast.io/luigicamastra/backdoored-client-from-mongolian-ca-monpass/) 跟 [NCC](https://hello.global.ntt/-/media/ntt/global/insights/white-papers/the-operations-of-winnti-group.pdf)也有發相關報告 
- [2021 pwc 報告](https://www.pwc.co.uk/issues/cyber-security-services/research/chasing-shadows.html)
  - 強調用客製化打包方式混淆 ShadowPad payload ，惡意程式名稱為 ShadowShredder or PoppingBee
- [2021 CrowdStrike 報告](https://www.crowdstrike.com/blog/overwatch-exposes-aquatic-panda-in-possession-of-log-4-shell-exploit-tools/)
  - 用 log4Shell 漏洞情況
- [2022 趨勢科技報告](https://www.trendmicro.com/content/dam/trendmicro/global/en/research/22/a/earth-lusca-employs-sophisticated-infrastructure-varied-tools-and-techniques/technical-brief-delving-deep-an-analysis-of-earth-lusca-operations.pdf)
  - 講述完整的攻擊生命週期  

C2 Infra
- 使用多層次設置
- 用大量的 vps 作為 reverse proxy 作為該攻擊組織惡意程式 c2 相關，如
  - Spyder、Cobalt Strike、ShadowPad 和 PlugX
- 一般都是配製為 https
- 憑證有自簽憑證但會故意模仿合法的憑證的資，底下舉例

```
Subject Distinguished Name (DN)
emailAddress=admin@sophos.com, C=So, ST=Abingdon-on-Thames, O=Sophos Ltd,
OU=IT, CN=www.sophos.com, emailAddress=admin@sophos.com
Issuer DN
emailAddress=admin@sophos.com, C=So, ST=Abingdon-on-Thames, L=England,
O=Sophos Ltd, OU=IT, CN=www.sophos.com, emailAddress=admin@sophos.com
Validity: 2022-02-28 to 2023-02-28
Serial Number (Decimal): 2
Fingerprint
SHA-256
b02aed9a615b6dff2d48b1dd5d15d898d537033b2f6a5e9737d27b0e0817b30e
SHA-1
7fe0ef289f0e29412f8b20a3d737b1750fa91d36
MD5
c22db64af83e159e40ada38e6d3f7699
```

攻擊族群也會盜取使用合法憑證

# Wider RedHotel Tooling

- 2019 - 2023 常用 CobaltStrike , Winnti
- 開源工具
  - [nps（一種內部網路滲透代理）](https://github.com/ehang-io/nps)
  - [Supershell（C2遠端控制平台）](https://github.com/tdragon6/Supershell)
  - [ARL](https://github.com/TophantTechnology/ARL)
  - [reGeorg（Webshel​​l 和代理工具）](https://github.com/sensepost/reGeorg)
