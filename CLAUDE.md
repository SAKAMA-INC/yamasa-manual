# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

水産物B2Bマーケットプレイス「サカマ」関連アプリの使用マニュアルサイト（静的HTML）。ヤマサ／脇口水産が運営。

## Architecture

ビルドツール・フレームワークなしの純粋な静的HTMLサイト。CSSはすべて各HTMLファイル内の`<style>`タグにインライン記述。

```
index.html          — マニュアル一覧（トップページ、4つのマニュアルへのカードリンク）
kakouba/index.html  — 加工場アプリ マニュアル（産地スタッフ向け：受注・加工・納品書・出荷確定）
shohin/index.html   — 商品管理アプリ マニュアル（産地スタッフ向け：出品・注文管理・納品書作成）
chuhmon/index.html  — 注文アプリ マニュアル（飲食店・小売店向け：仕入れ・注文・履歴管理）
shuppin/index.html  — 産地出品アプリ マニュアル（産地スタッフ向け：出品・注文管理・納品書作成）
```

## Design System

全ページ共通のCSS変数によるデザインシステム:
- フォント: Google Fonts — `Noto Sans JP`（本文）、`Shippori Mincho`（見出し）
- カラー: `--navy: #0d1f3c`, `--teal: #0e8a8a`, `--accent: #f0a500` 等
- レスポンシブ: 768px breakpoint でサイドバー非表示・パディング縮小

サブページ共通のUIコンポーネント:
- 固定サイドバーナビゲーション（`#sidebar`, 幅280px）
- IntersectionObserver によるアクティブナビ追従
- コールアウト: `.note`（警告）、`.info`（情報）、`.tip`（ヒント）
- `.flow-box` でステップフロー表示
- `.table-wrap > table` でデータテーブル

## Conventions

- 言語: すべて日本語
- セクションIDは `sec1`, `sec2`, ... の連番
- ナビアイテムは `<a href="#secN" class="nav-item">` で統一
- トップページのカードは相対パス `./kakouba/`, `./shohin/`, `./chuhmon/`, `./shuppin/` でリンク
