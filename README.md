# Pandoc for Report (Markdownでレポート作成)
## 概要
Markdownを使ってレポート作成する事ができる。

## 必要環境
- texlive(Tex)
- pandoc
- pandoc-crossref

## 準備(Mac)
- texlive(非常に時間かかる)
```shell
$ brew install texlive
```

- pandoc
```shell
$ brew install pandoc
```

- pandoc-crossref
```shell
$ brew install pandoc-crossref
```

## 準備(Windows)
- texlive(非常に時間かかる)<br>
[TeXLive](https://www.tug.org/texlive/acquire-netinstall.html) -> `install-tl-windows.exe`起動

- pandoc<br>
[pandoc(Github)](https://github.com/jgm/pandoc/releases/) -> Latest -> `pandoc-x.x-windows-x86_64.msi`

- pandoc-crossref<br>
[pandoc-crossref(Github)](https://github.com/lierdakil/pandoc-crossref/releases) -> Latest(Pandocと対応するバージョン) -> `pandoc-crossref-Windows.7z`(7z解凍ソフトが必要)<br>

    解凍後は`pandoc-crossref.exe`ファイルをPandocのディレクトリ(`C:\Program Files\Pandoc\`)に配置

## 確認
- Tex
```
luatex --version
```

- pandoc
```
pandoc --version
```

- pandoc-crossref
```
pandoc-crossref --version
```

## 生成
本リポジトリにて用意した、`.\test.md`をPandocを用いて`.pdf`ファイルに変換する。サンプルとして、`.\test.pdf`という名称で生成する。

### シェルスクリプト/バッチファイルから
本リポジトリではコマンドの入力が面倒な人向けに、macOS/Windows両方向けにそれぞれのスクリプトを用意した。
- macOSなどといった、Unix/Linux系シェル
```shell
$ .\exportPDF .\test.md test.pdf
```

- Windows/PowerShell
```prompt
.\exportPDF.bat .\test.md test.pdf
```

### ターミナル/プロンプトから
- 共通
```shell
pandoc -F pandoc-crossref .\test.md -o .\test.pdf --pdf-engine=lualatex --template=.\report.tex -N
```
テンプレート`--template=.\report.tex`を使わない/別のテンプレートを用いる場合は省略や変更可。省略した場合は、デフォルトのテンプレートが適用される。

## 書き方とか
本リポジトリでのテンプレートは、自身が通っている大学の学科でよく用いられるレポート形式に基づいて構成した。個人で新たにテンプレートを構成する事も可能です。


Markdownを作成後は先頭に以下のような`YAML`データを記述します。
```yaml
---
title: レポート名  # 題名
author:  # 作成者(複数人可, それぞれ省略可)
    - name: 田中　太郎  # 氏名
      id: XX21AXXX  # 学籍番号
      email: xx21axxx@xxx.jp # 学校用アドレス等
date: 2023年1月24日  # 提出日/作成日等といった日付
figureTitle: "図"
tableTitle: "表"
listingTitle: "ソースコード"
figPrefix: "図"
eqnPrefix: "式"
tblPrefix: "表"
lstPrefix: "ソースコード"
documentclass: ltjsarticle
indent: true  # 字下げを有効にするかどうか
coverpage: true  # 表紙だけのページにするかどうか
---
```
後はMarkdown記法に沿って書くだけです。

詳しい記法は`.\test.md`や`.\sample.pdf`(`.\test.md`から生成)を見てもらう方が早いかと思います。

## 利点とか
レポートの作成には一般的にWord等の文書作成ソフトウェアが使われます。が、作成する環境によって形式が崩れたりフォントが変わったりする経験があり、不便に感じる場面が多々ありました。また、ソースコードを綺麗に貼り付ける方法が無かったりします。

Pandocを用いたMarkdownによる記述では、以下の利点が挙げられます。
- LaTexよりも簡素に書ける
- フォーマットが環境によって左右されない
- ソースコードを綺麗に貼り付けられる
    - シンタックスハイライトにも対応
    - 行番号も表示可
- テンプレートが決まってしまえば、記述が楽
- 相互参照が楽
- Word等に比べてGUI操作が少ない　　など

一方で、以下の状況に当てはまる人にはPandocによるメリットは少ないと思われます。<br>
(従来での方法で作成する方が早いと思われるケース)
- `.docx`での提出が必須となっている
- 決められたレポートのひな形が指定されている
- テンプレート(ひな形)が毎回異なる方
- LaTexテンプレートの作成が難しい方
- 環境構築が難しい方
- 環境構築されておらず、レポート提出期限が迫っている方
- 数式やソースコードを貼り付ける場面がほとんど無い方
- ほとんど同じ環境でレポート作成する方
- Markdown記法を理解していない方
- HTMLやMarkdown等といったコード系アレルギー体質の方　　など


## テンプレート
本リポジトリに付属している`.\report.tex`は、自身が通っている大学の学科でよく用いられるレポート形式に基づいて再構成したものです。個人で新たにテンプレートを再構成する事も可能です。

新たに`pdf`テンプレートを構成するには、`.tex`形式のファイルをpandoc記法に基づいて構成する形となります。デフォルトのテンプレートを再構成する方が早いでしょう。デフォルトのテンプレートを取得し、`foo.tex`という名称で保存するには、以下のコマンドを実行します。
```shell
pandoc -D latex > foo.tex
```

そして、保存された`foo.tex`を編集します。Markdownで記述した`YAML`データに基づいて埋め込んだり、記述の順序を変えたりする事が出来るでしょう。また、フォントやフォントサイズを変える事も出来ます。

作成したテンプレート`foo.tex`を用いてpdfを生成する場合には、コマンドに`--template=.\foo.tex`を付加する事を忘れないようにしてください。