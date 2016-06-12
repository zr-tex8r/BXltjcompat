BXltjcompat パッケージバンドル
==============================

LaTeX: LuaTeX-ja の pLaTeX に対する互換性を改善する

### 前提環境

  * フォーマット： LaTeX
  * エンジン： LuaTeX
  * 依存パッケージ： LuaTeX-ja

### インストール

  - `*.sty` → $TEXMF/tex/latex/BXltjcompat

### ライセンス

本パッケージは MIT ライセンスの下で配布される。

bxpdfver パッケージ
-------------------

### パッケージ読込

    \usepackage{bxltjcompat}

### 機能

パッケージを読みこむと、pLaTeX 互換の以下の命令が使えるようになる。

  * `\kanjiskip` （長さ命令）
  * `\autospacing`
  * `\noautospacing` 
      - 上記3つの命令による設定内容は LuaTeX-ja の `kanjiskip` パラメタ
        に反映される。
  * `\xkanjiskip` （長さ命令）
  * `\autoxspacing`
  * `\noautoxspacing`
      - 上記3つの命令による設定内容は LuaTeX-ja の `xkanjiskip` パラメタ
        に反映される。
  * `\ybaselineshift` （長さ命令）
      - 設定内容は LuaTeX-ja の `yalbaselineshift` パラメタに反映される。
  * `\tbaselineshift` （長さ命令）
      - 設定内容は LuaTeX-ja の `talbaselineshift` パラメタに反映される。

また、calc パッケージの `\setlength`／`\addtolength` 命令の引数の式に
おいて、以下に挙げる pLaTeX 特有の単位が使えるようになる。

  * zw
  * zh
  * Q
  * H

従って、LaTeX 命令中の長さ値の引数について、それが calc に対応している
（つまり式が書ける）ならば、そこでも上掲の単位を使うことができる。例えば
`\parbox` の幅指定で zw が使える。

    \parbox{20zw}{...}

### 注意事項

特に TeX 言語を知っている人のための注意。

  * LaTeX レベルのコードでの互換を目指したものであり、一般の TeX 言語の
    コードでの互換命令の使用は考慮されていない。
  * 特に、互換長さ命令に対して `\kanjiskip=10pt` のように TeX の代入文を
    直接使った場合の動作については、「当該の代入文がエラーにならない」
    こと以外は未定義とする。多くの場合、外見上は代入が無視されたような
    挙動になる。
  * 互換長さ命令は1トークンの先読みを行う。従って、対話モードにおいて
    `\show\kanjiskip` という行を入力した場合、その場ではなく、次の行を
    入力した時点で初めて `\show` の表示が行われる。

更新履歴
--------

  * Version 0.2  [2016/06/12]
      - 最初の公開版。

--------------------
Takayuki YATO (aka. "ZR")  
http://zrbabbler.sp.land.to/
