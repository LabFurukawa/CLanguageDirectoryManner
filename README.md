<!--

This document is written in Markdown.
You can preview on such as VisualStudio Code.
If you want to know more, search with "vscode markdown" or refer to official document https://code.visualstudio.com/Docs/languages/markdown .

-->

[ ! ] 注意書き

- このドキュメントにはC言語にまつわる習慣的と思われること、独自研究が記されています。この通りにする必要はありません。
- 言語によってもまったく異なってきます。
- GitHubなどの有名なレポジトリを参考にすることは良いです。
- 物理屋などが書いたコードはこれらの習慣に沿っていない場合があるので気を付けてください。

# C Language Directory Manner

## ディレクトリ構造

- 必須
	- /src
	- /include
	- /docs
	- /test
	- makefile or .sln/.vcxproj/.vcxproj.filters or CMakeLists.txt

- 必要に応じて
	- /bin
	- /build
	- /lib
	- readme.md
	- .gitignore
	- LICENSE

"/"から始まっているのはディレクトリである。
上のグループのディレクトリは作成できるようになりたい。


### /src

- "source"の略
- ソースコード置き場。ないわけがない。
- `.c` `.cpp`を置く。
- コンパイル時に取り込まれてしまい、公開されないヘッダーファイル`.h`、`.hpp`もここに置くこともあるが外部から使われるコードは`/include`に置く。
- 画像などはテスト用なら/testであったりUIとして取り込まれるなら/srcとは別に"/resource"や"/image"などのディレクトリを作ってもいいし/srcの下に何かディレクトリを作ってもいい。

### /include

- headerファイル`.h`や`.hpp`を置く。
- gccの"-I"で追加されるディレクトリになる。(#include ""ではなく#include <>な参照になる)

### /docs

- "documents"の略
- 他人が使うこともあるならドキュメントは書くように。
- フォーマットはdocxなどの外部ソフトが要求されるものよりはテキストファイル `.txt`やMarkdown `.md`やHTML `.html`が良いだろう。

### /test
- この下にもディレクトリを区切ってソースごとのテストを残すと良い。
- それぞれにmakefileなどがあると検証も簡単だろう。

### makefile or .sln/.vcxproj/.vcxproj.filters or CMakeLists.txt
- makefileはUNIX系のビルド自動化ツールのファイル
- .sln/.vcxproj/.vcxproj.filters はVisual Studio(msbuild)のビルド自動化ツールのファイル
- CMakeLists.txtは上記のビルド自動化ツールを環境に依存しない形で記述する。`cmake`コマンドでmakefileや`.sln`を生成することができる。
- どのようにコンパイルすべきなのかわかるように記述すべきである。

### /bin

- "binary"の略
- 外部のバイナリファイル、`.dll`や`.so`、ビルドに必要なツールを入れることもある。

### /build

- 自分でコンパイルしたものを入れて置いたり、コンパイルの出力先としたりする。
- 自分の出力したものは参照できるように`/build/bin`、`/build/lib`などにわけておくべきである。
- dist(distribute)やdest(destination)の時もある。

### /lib

- "library"の略
- 外部のライブラリ、`.lib`や`.a`などを置く場所。


### readme.md

- GitHubではreadme.mdがプレビュー表示されるため、GitHubにpushする場合は作成しておくとよい。詳しいドキュメントなどは/docsに置くとルートディレクトリはきれいにしておける。

### .gitignore

- Gitでは.gitignoreで対象になっているファイルやディレクトリはGitの対象にならない。
- GitHubなどにpushしたくないバイナリファイルなどはここに記述する。

### LICENSE

- GitHubなどではMITやGPLなどのテンプレートが備わっているが自分で書いてもよい


<!-- Written by Croyfet in 2022-->
