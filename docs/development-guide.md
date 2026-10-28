# 開発ガイド

シーケンサータウンは、外部ライブラリに依存しない静的なブラウザアプリです。公開時はリポジトリのルートを GitHub Pages で配信します。

## ローカルで動かす

Node.js を用意し、リポジトリのルートで `npm start` を実行します。ブラウザで `http://127.0.0.1:5176` を開いてください。音は画面上の操作後に開始します。ビルドコマンドはありません。

## 検証

- `npm test`：水路・池・建設・動物の移動・音などのテストを実行します。
- `npm run check`：`src/` 内の JavaScript の構文を検査します。

画面を変えた場合は、PC・スマホで道具の選択、建設と取り消し、音の開始とミュート、JSON の保存・読み込み、街の写真の保存も確認してください。

## コード構成

- `index.html` と `style.css`：画面の構造と見た目。
- `src/core.js`：街の状態、建設、水の接続、保存形式の復元。
- `src/app.js`：画面操作、自動保存、JSON の入出力。
- `src/render.js`、`src/art.js`、`src/water-shapes.js`：街と水路の SVG 表示。
- `src/music.js`：音の進行と合成。
- `src/photo.js`：街の PNG 作成と共有。
- `src/legacy-core.js`、`src/legacy-render.js`：以前の街の読み込みと表示。
- `tests/`：状態・描画・音の回帰テスト。

保存形式を変更する際は、`src/core.js` のバージョンと復元処理を確認し、既存の JSON とブラウザ内の保存データを読み込めることを検証してください。画面の JavaScript・CSS を変更した際は、`index.html` とモジュール import のバージョン付き URL も確認してください。
