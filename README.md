# 国土数値情報 道路データを用いた経路探索・空間分析

2026年4月に **CC BY 4.0** で公開された[国土数値情報 道路データ（N13）](https://nlftp.mlit.go.jp/ksj/)（ラインデータ）を、経路探索に利用できる**道路ネットワークデータ（ノード・リンク）**へ変換し、これまで有償データ（DRM等）が前提だった全国規模の到達圏分析・経路探索を、**オープンデータのみ**で実現する取り組みです。

道路ネットワーク化という共通基盤（[`common/network-conversion/`](common/network-conversion/)）の上に、複数の分析事例を順次追加していきます。

## 分析事例一覧

| # | 事例 | 概要 |
|---|------|------|
| 01 | [到達圏分析・経路探索](cases/01-reachability-routing/) | 指定地点から N 分以内の到達範囲と最短経路を車・徒歩モードで可視化 |
| 02 | [立ち寄り分析（時刻スライス型到達圏分析）](cases/02-stopover-analysis/) | 移動実績から通過し得た道路リンクの範囲を推定 |
| 03 | [公共交通空白地域の抽出](cases/03-transit-desert/) | 道路ネットワーク上の徒歩距離で全国の空白地域を定量化 |
| 04 | [津波避難シミュレーション](cases/04-tsunami-evacuation/) | 避難施設の整備段階別に避難困難率を推計（静岡県焼津市） |

新しい事例は [`templates/case-template/`](templates/case-template/) を `cases/NN-slug/` にコピーして追加してください。

## デモ・資料

- 国土数値情報 活用事例ページ: https://nlftp.mlit.go.jp/ksj/case_studies.html
- 発表資料（MIERUNE JCT #03）: https://www.docswell.com/s/shi-works/KMQ6VX-2026-06-10-205515
- 到達圏分析デモ: https://shiwaku.github.io/ksj-route-search-api/
- 公共交通空白地域デモ: https://shiwaku.github.io/japan-transit-desert-analysis-125/

## リポジトリ構成

```
.
├── common/network-conversion/  # 全事例が共有する道路ネットワーク変換の基盤
├── data/                       # 利用データの出典・入手方法（実データは含まない）
├── cases/                      # 分析事例（1事例 = 1ディレクトリ）
├── docs/                       # リポジトリ全体の共有ドキュメント・図
└── templates/case-template/    # 新規事例の雛形
```

- [利用データについて](data/) … 各事例が利用する国土数値情報等の一覧と出典
- [道路ネットワーク変換](common/network-conversion/) … ノード・リンク生成の共通手法

## 使用ソフトウェア

- Python（ネットワーク変換・経路探索の独自実装）
- MapLibre GL JS（可視化）

## 課題・今後

- 一方通行が未考慮
- 高速自動車国道と都市高速道路の区別ができない
- 速度設定の精緻化（道路種別・幅員別・時間帯）

これらは今後の国土数値情報の整備に期待したい点です。

## ライセンス

本リポジトリで利用している国土数値情報 道路データ（N13, 2026年4月版）は **CC BY 4.0** で提供されています。出典の表示にあたっては[国土数値情報ダウンロードサイト](https://nlftp.mlit.go.jp/ksj/)の利用規約に従ってください。
