SICP
====

<img src="http://sicpebook.files.wordpress.com/2013/09/dreamsmile3.png"
 alt="Par dreaming and smiling" align="right" />

This is a PDF version of "Structure and Interpretation of Computer Programs" by Harold Abelson, Gerald Jay Sussman, and Julie Sussman. It is a further development of the [Unofficial Texinfo Format](http://www.neilvandyke.org/sicp-texi/) (UTF), which was originally derived from the [HTML version](http://mitpress.mit.edu/sicp/) at The MIT Press.

これはPDF版の"Structure and Interpretation of Computer Programs"です。Harold Abelson, Gerald Jay Sussman, そして Julie Sussmanによる著書です。PDF版は[Unofficial Texinfo Format](http://www.neilvandyke.org/sicp-texi/) (UTF)からのさらなる開発であり、
元々はMIT Pressの[HTML version](http://mitpress.mit.edu/sicp/)からの派生です。

* これはAndres Raba氏による[PDF版SICP](https://github.com/sarabander/sicp-pdf) の日本語翻訳です。日本語版はminghaiが翻訳を担当しました。

Biggest change in this revision (2.andresraba5) is the conversion to LaTeX, which opens the door to design and customization possibilities that the massive CTAN archive enables. Also, the latest typesetting engine XeTeX can be used, along with the Unicode and OpenType goodness it brings.

このバージョン(2.andresraba5)での大きな変更はLaTeXへの変換です。これにより大規模なCTANアーカイブが可能にするデザインとカスタマイズの可能性への扉を開きました。また、最新の組版エンジンであるXeTeXが、それがもたらすUnicodeとOpenTypeの良さと共に使用可能です。

* 日本語版ではIPAフォントを使用しました。

Source
------

The `src` directory contains both Texinfo and LaTeX sources. To recompile the book, go there and enter:

`src`ディレクトリがTexinfoとLaTeXの両方のソースを含みます。本をリコンパイルするためにはその場所まで移動して以下を入力して下さい。

```bash
$ make
```

* 日本語版ではTexinfoファイルがLaTeXファイル上の変更を反映しておりません(すみません)。そのため直接、xelatex jsicp.texを実行して下さい。

The file `preamble.tex` contains all the configuration and style declarations. Note that the LaTeX file `sicp.tex` will be generated on the fly, overwriting the previous version. To keep `sicp.texi` and `sicp.tex` in sync, I make changes to `sicp.texi,` which is already a hybrid of Texinfo and LaTeX code. This is fine, because all non-Texinfo content remains unchanged by the script.

`preamble.tex`ファイルが全ての設定とスタイル宣言を含みます。LaTeXファイル`sicp.tex`が動的に生成されることに注意して下さい。以前のバージョンを上書きしてしまいます。`sicp.texi`と`sicp.tex`の同期を続けるために、既にTexinfoとLaTeXのコードのハイブリッドである`sicp.texi`に変更を加えることにします。これは問題ありません。全ての非Texinfoコンテンツがスクリプトにより変更されない状態を維持するためです。

* 日本語版では既にLaTeXファイルとTexinfoファイルとの間の同期が破綻しています(すみません)。今後Texinfoファイルを直接利用したい方はいないと思いますが(少なくとも私はPDFにしか用が無いのですが)もし必要でしたら頑張って修正を反映して下さい orz。なお、preamble.texはそのままでは日本語が表示できないため、こちらにも変更の反映が必要です。

Chances for successful compilation are increased if you have almost complete installation of recent TeX Live distribution (the pdf here is compiled with 2012 release). The needed OpenType fonts must be installed in the operating system. You also need Inkscape to recreate image PDFs from SVGs.

成功裏のコンパイルの可能性は最新のTeX Liveのディストリビューションをインストールすることにより増します。(ここのPDFファイルは2012のリリースにてコンパイルされています)。必要なOpenTypeフォントがOSにインストールされなければなりません。またSVGをPDFに変換するためにはInkscapeも必要です。

* 日本語を通すには最低でもTeX Live 2013が必要です。日本語対応のminghaiは当初は最新の(RCのUbuntu)ディストリのLinux上で
texi2dviとdvipdfmxを用いてPDF化していました。最終的にはWindowsに最新のW32TeXを入れ、xelatexにてコンパイルしています。
日本語環境ではIPAフォントをインストールすることが必須です。また実際には足りないスタイルファイルが結構有りますので、
エラーが出る度にCTANにてスタイルファイルを落としてインストールすることを何度かしなければいけませんでした。

If compilation stops with "LaTeX Error: Too many unprocessed floats.", you could try to increase the width and height of text area in [preamble](https://github.com/sarabander/sicp-pdf/blob/master/src/preamble.tex#L70-L71). Newer TeX Live or updated fonts could result in different character metrics, so that some figures no longer fit. The problem is reported in issue [#5](https://github.com/sarabander/sicp-pdf/issues/5).

コンパイルが"LaTeX Error: Too many unprocessed floats"で停止した場合には、[preamble](https://github.com/sarabander/sicp-pdf/blob/master/src/preamble.tex#L70-L71)の中にあるテキストの幅と高さを増やしてみると良いかもしれません。
新しいTeX Liveや更新されたフォントの使用は異なる文字メトリックスの結果を引き起し、いくつかの図が合わなくなる恐れがあります。
問題がissue [#5](https://github.com/sarabander/sicp-pdf/issues/5)にて報告されています。

* 日本語版では図では特に問題が出ていませんが、図がそもそも翻訳していません。そもそもそんなに英語のある図がありませんが、図を翻訳して下さる方を募集しています。図を翻訳して下さる方がいらしましたら、図の中の日本語には特に問題が無い限りIPAフォントを使用して下さると表示できないとか、PDFファイルサイズのさらなる増大とかフォントの著作権等の問題が防げますのでよろしくお願いいたします。

To clean up after the build:

ビルド後に全ての不要なファイルを削除するためには以下を入力して下さい。

```bash
$ make clean
```

* 日本語版では絶対に行わないで下さい。ファイル名が変更してあるため問題無いと思いますが、何が起こってもしりません。

This deletes the temporary files written during sicp.pdf creation, including sicp.pdf itself. Move it up to root directory if you want to keep it.

これはsicp.pdf作成の間に書かれた一時ファイルをsicp.pdf自体を含めて削除します。PDFを保持したい場合には(レポジトリの)ルート
ディレクトリに上げて下さい。

To remove all the generated PDFs and auxiliary files in the whole `src` tree:

`src`ツリー内のPDFと全ての補助的なファイルを削除するには以下を実行します。

```bash
$ make clean-all
```

* 日本語版ではやっちゃダメです

謝辞
----------------

* Lytha Ayth
* Neil Van Dyke
* Gavrie Philipson
* J. E. Johnson
* Mingshen Sun
* holomorph
* Andres Raba

License
-------

WARNING: This is not a translation. This is a license only for MY Japanese version.

The files `sicp.texi, sicp.tex, sicp.pdf,` and the diagrams in directory `src/fig` are licensed under Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License ([CC BY-NC-SA](http://creativecommons.org/licenses/by-nc-sa/3.0/)).

I (minghai) added NC constraints to original (PDF's) CC BY-SA license because MIT changed its license of SICP to CC BY-NC (from CC BY-SA), recently. I believe there's no need to do this, but I just want to respect the MIT's decision.
          
The script files `ex-fig-ref.pl, survey.rb,` and `texi-to-latex.pl` are licensed under GNU General Public License version 3 (for details, see src/LICENSE). (as-is the same with the original PDF version).

日本語版ライセンス：

日本語版のsicp.texi、sicp.texはCreative CommonsのCC BY-NC-SAとさせて頂きます。改変、再配布は同じCC BY-NC-SA 3.0にて行う限り自由に行って頂いてかまいません。ただし、NCですので非商業活動に限定します。これは元々のMITサイトのSICP配布ライセンスの変更に従う物です。

また`ex-fig-ref.pl, survey.rb,texi-to-latex.pl`は元の作者であるAndres Raba氏の指定によりGPL v3です。
