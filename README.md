# chineseWordPredict

###### tags: `自然語言處理` `N-Gram`

[TOC]

目標
---
根據上文推薦接續的文字，機率愈大愈前面

資料
---
中文Wiki

前處理
---
利用jieba斷詞，並用正規表示取出「中文字元」

模型算法
---
1. 利用wiki資料建造多個ngram模型
2. 利用Interpolation Smoothing 來避免下個詞機率會是0的情況
3. 假設前面有n個字，那就會用到(n+1)gram，例子如下：
```
假設前面有2個字 => 用到3-gram
P1表1-gram的機率，P2表2-gram的機率，P3表3-gram的機率
P3^ = a*P3 + (1-a)(a*P2 + (1-a*P1))
P3^ 為下個字的機率
```