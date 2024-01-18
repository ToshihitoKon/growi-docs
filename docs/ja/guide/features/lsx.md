# lsx 機能を使ってページリストを表示する

lsx 機能を使うと、特定のページの配下に存在するページを一覧表示できます。

たとえばあるページに `$lsx()` と記述すると、画像のようにそのページの配下に存在するページ一覧を出力できます。

複数のページへのショートカットを記載したいときなどに便利です。

<img :src="$withBase('/assets/images/ja/lsx.png')" alt="lsx">

## 指定したページの配下ページ一覧を出力する

ページの指定方法は、ルートページからの絶対パスと、編集中のページからの相対パスの 2 種類です。

存在しないページを指定した場合、`$lsx(/サンプル) has no contents` のようなエラーメッセージが表示されます。

- `$lsx(/user)` と記述すると、トップページ直下の user ページ配下のページ一覧が出力されます。
- `$lsx(./サンプル)` と記述すると、編集中のページの配下の `サンプル` というページ配下のページ一覧が出力されます。

## オプションを設定する

lsx 機能には、複数のオプション設定があります。同時に複数のオプションを設定する場合は、カンマ区切りで `$lsx(/ページ, depth=1, sort=createdAt, reverse=true)` のように記述します。

### オプション一覧

| パラメータ    | デフォルト値    |  説明   | 詳細 |
| --- | --- | --- | --- |
|  num   |  50   | ページ数を指定する| [numオプション詳細](./lsx.html#num-オプション) |
|  depth   |  未設定   | ページの階層を指定する| [depthオプション詳細](./lsx.html#depth-オプション) |
|  sort   |  path   | ページの並び順を指定する| [sortオプション詳細](./lsx.html#sort-オプション) |
|  reverse   |  false   | ページの並び順を逆にする| [reverseオプション詳細](./lsx.html#reverse-オプション) |
|  filter   |  未設定   | ページをフィルタする | [filterオプション詳細](./lsx.html#filter-オプション) |

### num オプション

出力するページの数を指定できます。デフォルトの値は 50 です。

- `$lsx(num=N)` : N 件のページを出力します。N には自然数を入力してください。
- `:` や `+` を使って、出力するページを制御できます。
  - `$lsx(num=1:10)` : 1件目から10件目までのページを出力します。
  - `$lsx(num=2:)` : 2件目から最後までのページを出力します。
  - `$lsx(num=5+2)` : 5件目から2件先まで (5,6,7番目)のページを出力します。

### depth オプション

出力するページの階層を指定できます。デフォルトでは、存在する全ての階層のページを出力します。

- `$lsx(depth=N)` : 編集中のページ、もしくは指定したページを起点にして、N 階層下のページまで出力します。N には自然数を入力してください。
- `:` や `+` を使って、出力するページを制御できます。
  - `$lsx(depth=2:3)` : 2階層下から3階層下までのページを出力します。
  - `$lsx(depth=2:)` : 2階層下から最下層までのページを出力します。
  - `$lsx(depth=1+2)` : 1階層下から2階層先まで (1,2,3階層下)のページを出力します。

### sort オプション
  
ページ一覧の並び順を、以下のいずれかで指定できます。

- `$lsx(sort=path)` (デフォルト) : ページ名順に出力する（ページ名の文字コードの昇順）
- `$lsx(sort=createdAt)` : 作成日の昇順で出力する (作成日が古い順)
- `$lsx(sort=updatedAt)` : 最終更新日の昇順で出力する (更新日が古い順)

### reverse オプション

出力順を逆にします。

- `$lsx(sort=updatedAt, reverse=true)` : 最終更新日の降順で出力する (更新日が新しい順)

### filter オプション

出力するページを、ページ名に含まれる文字列でフィルタできます。filter のマッチタイプは部分一致です。

- `$lsx(filter=2023)` : ページ名に `2023` が含まれるページのみが出力されます。

## GitHub

lsx は [Pukiwiki lsx plugin](http://ukiya.sakura.ne.jp/index.php?PukiWiki%2F1.4%2F%E3%83%9E%E3%83%8B%E3%83%A5%E3%82%A2%E3%83%AB%2F%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3%2F%E7%8B%AC%E8%87%AA%E3%81%AB%E8%BF%BD%E5%8A%A0%E3%81%97%E3%81%9F%E3%82%82%E3%81%AE%2Flsx) を参考にして、GROWI に組み込んだ機能です。

[GitHub](https://github.com/weseek/growi-plugin-lsx)