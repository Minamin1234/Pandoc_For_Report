---
title: レポート作成演習4
subtitle: レポート
author:
    - name: 田中　太郎
      id: XX21AXXX
      email: xx21axxx@xxx.jp
date: 2023年1月24日
figureTitle: "図"
tableTitle: "表"
listingTitle: "ソースコード"
figPrefix: "図"
eqnPrefix: "式"
tblPrefix: "表"
lstPrefix: "ソースコード"
documentclass: ltjsarticle
indent: true
coverpage: true
---


# 見出し
## 見出し
本文的なもの。本文。1つ改行を空けて記述すれば別のパラグラフとして表示される。改行を挟まない限り、一つのまとまりとして、表示される。

別のパラグラフ。注釈[^1]はこの通り。適当な図を以下に示す。

[^1]: 注釈

![適当な図[^fig]](fig1.png){#fig:randomfig}

[^fig]: 図タイトルにも注釈可

|X  |Y  |結果|
|:-:|:-:|:-:|
|0  |0  |0  |
|0  |1  |0  |
|1  |0  |0  |
|1  |1  |1  |

:ANDゲートの真理値表 {#tbl:table}

\clearpage

## ソースコード
```{#lst:HelloWorldのソースコード .cpp .numberLines caption="HelloWorld"}
#include <iostream>

int main() {
    std::cout << "Hello World!" << std::endl;
    return 0;
}

```

# 参考文献 {-}
`{-}`をつけると通し番号がつかない。

- その1
- その2
    - あ
    - い
    - う