# 全国市区町村議会の会議録リンク集

## 概要
全国の市区町村議会「会議録検索ページ」を一覧化した静的サイトです。
各自治体ごとに、会議録検索などの公式URLを整理し、都道府県別に整理しています。
「自治体ごとの会議録ページを横断的に探したい」
といった用途を想定しています。

**リンク先は取得作業中です。まだ全ての自治体に対応できていません。**
サイト上部にある「対応自治体数…XX/XX（X%）」は、cities_all.xmlの`<result>` が `ok` の件数（=URLリンクがある件数）を表示しています。

## このリポジトリに含まれるもの

| ファイル | 説明 |
|----------|------|
| `index.html` | ページ本体 |
| `style.css` | スタイル |
| `script.js` | `cities_all.xml` を読み込み、リストを描画 |
| `cities_all.xml` | 都道府県別の各自治体の読みとリンク先URLをまとめたもの → `<municipality>`（`ja` / `en` / `url` / `result`） |
| `favicon.svg` | ファビコン |
| `checks/*.mjs` | URLチェック用スクリプト（`node checks/check_ssp.mjs` など。親の `cities_all.xml` を読む） |
| `results/` | 上記チェックの出力 XML（`check_*_YYYYMMDD_HHmm.xml`） |

`merge_xml.mjs`（直下）は `results/check_*.xml` を `cities_all.xml` にマージする。例: `node merge_xml.mjs results/check_ssp_xxx.xml`

## ローカルでの表示

`fetch` で XML を読むため、`file://` 直開きでは環境によって失敗することがあります。プロジェクトフォルダをルートにした簡易サーバーで開いてください。

```bash
npx --yes serve .
```

## データの出典

自治体一覧の基礎データは [localgovjp](https://github.com/code4fukui/localgovjp)（[CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)）を加工したものです。英字スラッグ・各 `<url>`・`result` は別途取得・付与した値です。

## ライセンス

本リポジトリのオリジナル部分のライセンスは未指定です。必要に応じて `LICENSE` を追加してください。第三者データ・サービス（localgovjp、リンク先の各サイト）の利用条件は各提供元に従います。

## フィードバック歓迎
- URLの誤り報告
- 未登録自治体の追加
- UI改善
- スクリプト改善

Issue / PR 歓迎です。ぜひお力をお貸しください。
