# 国土数値情報 活用事例集

[国土数値情報](https://nlftp.mlit.go.jp/ksj/)（KSJ）を用いた空間分析・可視化の活用事例をまとめたリポジトリです。データ種別や分析テーマを問わず、事例を順次追加していきます。

各事例は [`cases/`](cases/) に1事例 = 1ディレクトリで自己完結し、複数事例で再利用する処理は [`common/`](common/) の共通コンポーネントに切り出しています。

## 分析事例一覧

| # | 事例 | テーマ | 主な利用データ |
|---|------|--------|----------------|
| 01 | [到達圏分析・経路探索](cases/01-reachability-routing/) | 道路ネットワーク | 道路データ（N13） |
| 02 | [公共交通空白地域の抽出](cases/02-transit-desert/) | 道路ネットワーク | 道路データ（N13）, バス停留所（P11）, 駅別乗降客数（S12）, 国勢調査125mメッシュ人口（参考） |

> 現在の事例はいずれも「道路ネットワーク」テーマで、[`common/road-network/`](common/road-network/) の道路ネットワーク変換を共通基盤としています。今後は他のデータ・テーマの事例も追加していきます。

新しい事例は [`templates/case-template/`](templates/case-template/) を `cases/NN-slug/` にコピーして追加してください（手順は下記）。

## リポジトリ構成

```
.
├── cases/                   # 分析事例（1事例 = 1ディレクトリ。テーマ・データを問わない）
├── common/                  # 複数事例で再利用する共通コンポーネント
│   └── road-network/        # 道路ネットワーク変換（道路系事例の共通基盤）
├── data/                    # 利用データの出典・入手方法（実データは含まない）
├── docs/                    # リポジトリ全体の共有ドキュメント・図
└── templates/case-template/ # 新規事例の雛形
```

- [利用データについて](data/) … 各事例が利用する国土数値情報等の一覧と出典
- [共通コンポーネント](common/) … 複数事例で共有する処理（現状は道路ネットワーク変換）

## 新規事例の追加手順

1. [`templates/case-template/`](templates/case-template/) を `cases/NN-slug/` にコピー（`NN` は次の連番、`slug` は英小文字）
2. `README.md` を埋め、図を `images/` に配置
3. 利用データを [`data/README.md`](data/README.md) のカタログに追記
4. トップの「分析事例一覧」表に1行追記
5. （道路ネットワークを使う事例なら [`common/road-network/`](common/road-network/) を参照。新しいテーマで再利用可能な処理が出たら `common/` に切り出す）

## デモ・資料

- 国土数値情報 活用事例ページ: https://nlftp.mlit.go.jp/ksj/case_studies.html
- 発表資料（MIERUNE JCT #03）: https://www.docswell.com/s/shi-works/KMQ6VX-2026-06-10-205515
- 到達圏分析・経路探索デモ: https://shiwaku.github.io/ksj-route-search-api/
- 公共交通空白地域デモ: https://shiwaku.github.io/japan-transit-desert-analysis-125/

## ライセンス

利用している国土数値情報は、データ・整備年次により提供ライセンスが異なります（例: 道路データ N13 の2026年4月版は **CC BY 4.0**）。出典の表示にあたっては各データおよび[国土数値情報ダウンロードサイト](https://nlftp.mlit.go.jp/ksj/)の利用規約に従ってください。
