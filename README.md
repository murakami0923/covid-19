# covid-19

<!-- TOC -->

- [covid-19](#covid-19)
- [概要](#%e6%a6%82%e8%a6%81)
- [前提](#%e5%89%8d%e6%8f%90)
- [環境構築](#%e7%92%b0%e5%a2%83%e6%a7%8b%e7%af%89)
- [使い方](#%e4%bd%bf%e3%81%84%e6%96%b9)
  - [データファイルをダウンロード](#%e3%83%87%e3%83%bc%e3%82%bf%e3%83%95%e3%82%a1%e3%82%a4%e3%83%ab%e3%82%92%e3%83%80%e3%82%a6%e3%83%b3%e3%83%ad%e3%83%bc%e3%83%89)
  - [Jupyter Lab](#jupyter-lab)

<!-- /TOC -->

# 概要

- COVID-19の感染者データ
  - ~~https://github.com/kaz-ogiwara/covid19.git~~
  - [https://jag-japan.com/covid19map-readme/](https://jag-japan.com/covid19map-readme/)
    - CSV : [https://dl.dropboxusercontent.com/s/6mztoeb6xf78g5w/COVID-19.csv](https://dl.dropboxusercontent.com/s/6mztoeb6xf78g5w/COVID-19.csv)

# 前提

- OS
  - Mac
  - Linux
  - WSL
- Python 3.8.2
    - 開発の際はpyenvを使っています。

# 環境構築

```sh
pip install -U pip
pip install -r requirements.txt
```

# 使い方
## データファイルをダウンロード

```sh
curl -o COVID-19.csv https://dl.dropboxusercontent.com/s/6mztoeb6xf78g5w/COVID-19.csv
```

## Jupyter Lab

```sh
jupyter lab
```

Jupyter Labが起動したら、`notebook.ipynb` を開き、実行します。
詳細については `notebook.ipynb` に記載していきます。

