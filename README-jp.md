# covid-19

<!-- TOC depthTo:3 -->

- [covid-19](#covid-19)
- [概要](#概要)
- [データファイルの取得元について](#データファイルの取得元について)
- [動作環境](#動作環境)
- [注意、お願い](#注意お願い)
- [事前準備](#事前準備)
    - [ローカル環境で使う場合](#ローカル環境で使う場合)
        - [前提](#前提)
        - [環境構築](#環境構築)
        - [データファイルをダウンロード](#データファイルをダウンロード)
        - [Jupyter Labを起動](#jupyter-labを起動)
    - [GoogleColaboratoryで使う場合](#googlecolaboratoryで使う場合)
        - [githubから](#githubから)
        - [ダウンロードを有効に（初回実行、データファイルの最新版を取得し直す場合）](#ダウンロードを有効に初回実行データファイルの最新版を取得し直す場合)
        - [ダウンロードを無効に（ダウンロードしたファイルで実行）](#ダウンロードを無効にダウンロードしたファイルで実行)

<!-- /TOC -->

# 概要

COVID-19の感染者数について、

- 都道府県を指定（できれば複数）して、それらの都道府県の時系列変化をみてみたい
- 特定の日付（今日、昨日、先週の○曜日、など）を指定して、その日の都道府県別の感染者数を見てみたい

という思いがあり、感染者データのCSVファイルから集計してグラフを生成する処理を、Jupyter Labで作成しました。

# データファイルの取得元について

COVID-19の感染者データについては、ジャッグジャパン株式会社様が「都道府県別新型コロナウイルス感染者数マップ」のサイト（[https://jag-japan.com/covid19map-readme/](https://jag-japan.com/covid19map-readme/)）にて公開されているCSVデータを使用しています。

# 動作環境

当初は、ローカルでPython3、Jupyter Labをインストールして実行するように作成しましたが、  
ローカルに環境を立てる手間がかかる、勃て方がわからない、などのケースも考えられることから、  
Google Colaboratoryにノートブックをインポートして実行できるようにしました。

# 注意、お願い

- データファイルや、都道府県CSVのファイル(Google Colaboratoryの場合)のダウンロードは、必要最低限の回数にしてください。
- 手探りで作っているので、間違いや使いにくいところなど、あるかと思いますが、ご了承ください。
- このソフトウェアを使用することにより損害が生じた場合には、第三者への損害や被害の修復も含み、その結果責任は全て利用者に帰することとします。

# 事前準備
## ローカル環境で使う場合
### 前提

- OS
  - Mac
  - Linux
  - WSL
- sqlite等（jupyter labの実行時に必要）
- Python 3.8.2
    - 開発の際はpyenvを使っています。
      - pyenv、pyenv-virtualenvインストールの参考 : [https://qiita.com/Kodaira_/items/feadfef9add468e3a85b](https://qiita.com/Kodaira_/items/feadfef9add468e3a85b)

### 環境構築

```sh
pip install -U pip
pip install -r requirements.txt
```

### データファイルをダウンロード

初回実行時、および、最新のデータファイルを取得する際には、以下のようにしてデータファイルをダウンロードします。

```sh
curl -o COVID-19.csv https://dl.dropboxusercontent.com/s/6mztoeb6xf78g5w/COVID-19.csv
```

### Jupyter Labを起動

```sh
jupyter lab
```

【注意】
sqliteに関するパッケージをインストールしていない場合、jupyter labを起動しようとしたときに、sqliteに関するエラーが表示されることがあります。  
その場合、aptやyum等でsqliteに関するパッケージをインストールします。

参考：[Qiita : pyenv, pipenv 環境でjupyter notebook使う時にsqliteに関するエラーが出たとき](https://qiita.com/kazetof/items/adeb331c99d408853f07)

ubuntuの場合の一例：

```sh
sudo apt install libsqlite3-dev libreadline6-dev libbz2-dev libssl-dev libsqlite3-dev libncursesw5-dev libffi-dev libdb-dev libexpat1-dev zlib1g-dev liblzma-dev libgdbm-dev libmpdec-dev
```

※既にパッケージがインストールされていて、インストール済みのバージョンの方が新しいなどのエラーになるケースもあるため、その場合は、インストール対象のパッケージから該当するものを除外して再実行します。

Jupyter Labが起動したら、`covid-19-jp-notebook.ipynb` を開き、実行します。
詳細については `covid-19-jp-notebook.ipynb` に記載していきます。

## GoogleColaboratoryで使う場合
### githubから
#### ノートブックを開くダイアログを表示

Google Colaboratoryのサイト（[https://colab.research.google.com/](https://colab.research.google.com/)）を開きます。

最初に開いたタイミングで、ノートブックを開くダイアログが表示されます。  
ダイアログが表示されない場合は、「ファイル」→「ノートブックを開く」でダイアログが表示されます。

![](readme-static/img/colab-open.png)

#### githubからのインポート

ノートブックを開くダイアログが開いたら、「GitHub」タブを開き、以下のように入力・選択します。

- githubのURL：[https://github.com/murakami0923/covid-19](https://github.com/murakami0923/covid-19)
- リポジトリ：murakami0923/covid-19
- ブランチ：master

これを入力すると、以下のように、ノートブックのファイルの一覧が表示されます。

![](readme-static/img/colab-github-import.png)

`covide-19-jp-notebook.ipynb` のファイル名をクリックすると、ブラウザの新しいタブにノートブックが表示されます。

#### ドライブにコピーを保存

githubからインポートしたノートブックの画面になるので、ドライブにコピーを保存します。  
「ファイル」→「ドライブにコピーを保存」

![](readme-static/img/colab-copy-to-drive.png)

### ダウンロードを有効に（初回実行、データファイルの最新版を取得し直す場合）

Google Colaboratory上では、初回実行時に、都道府県CSVとデータファイルをダウンロードする必要があります。  
ダウンロードを有効にするフラグを `DOWNLOAD` の定数として設定していますので、初回だけ値を変更してノートブックを実行します。

![](readme-static/img/colab-download-01-true.png)

### ダウンロードを無効に（ダウンロードしたファイルで実行）

一旦、都道府県CSVとデータファイルをダウンロードしたら、 `DOWNLOAD` の定数をもとに戻します。

![](readme-static/img/colab-download-02-false.png)

