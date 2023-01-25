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