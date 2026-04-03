# game-asset-search-skill

A distribution-only skill and registry for finding game asset sources with AI.

## 日本語

### Purpose / このリポジトリの目的

このリポジトリは、ゲーム用アセットの配布元を AI が探しやすくするための **配布専用** skill と registry をまとめたものです。目的は次の 2 点だけです。

1. ユーザーが skill を取得して使えること
2. AI が参照できる構造化 registry を同梱すること

### Contents / 含まれているもの

- `skills/game-asset-search/SKILL.md`  
  配布元候補を選ぶための手順と出力方針を記述した skill 本体
- `skills/game-asset-search/ref/registry.json`  
  アセット配布元をサイト単位で整理した構造化 registry
- `LICENSE`  
  このリポジトリ内のファイルに対する MIT License

### Installation / インストール方法

このリポジトリを clone またはダウンロードしてください。

```bash
git clone <repository-url>
cd game-asset-search-skill
```

### Placement / 配置方法

`skills/game-asset-search/` ディレクトリを、利用するツールやワークフローが参照する `skills/` 配下へ配置してください。`SKILL.md` と `ref/registry.json` の相対関係はそのまま維持してください。

もし利用環境が別のルート構成を要求する場合でも、`game-asset-search/` フォルダ内の構造は崩さずに配置してください。

### Usage with Claude Code / Claude Code での利用方法

Claude Code 側で `skills/` 配下の skill を参照できる構成であれば、`skills/game-asset-search/` を読み込ませたうえで、アセット条件を指定して依頼します。

例:

- `Find sources for low-poly fantasy 3D assets for Unity with commercial-friendly licensing.`
- `Recommend sites for pixel art UI assets, and include cautions and query hints.`

この skill は `registry.json` を参照して、上位 3〜5 件程度の候補、選定理由、注意点、検索ヒントを返す想定です。

### Notes / 注意事項

- registry は **サイト単位** の傾向と注意点を整理したものです。個別アセット単位の保証は行いません。
- 個別作品ごとのライセンス、品質、真偽、商用利用可否は最終的に各配布元・各作品ページで確認してください。
- スクレイピング、API、データベース、検索 UI、ベクトル検索、自動更新は含みません。
- Piskel と Aseprite は配布元カタログというより、主にピクセルアート作成・編集ワークフローに関係するツールとして registry に含めています。

### Distribution-only notice / 配布専用について

このリポジトリは配布専用です。フィードバック受付やサポート対応は行いません。Issue や Discussion を前提にした運用も想定していません。

### License scope / ライセンス適用範囲

このリポジトリのライセンスは、このリポジトリ内のファイルにのみ適用されます。外部のアセット配布元および個別アセットには、それぞれ独自のライセンスや利用規約が適用されます。

## English

### Purpose

This repository provides a **distribution-only** skill and registry that help AI find game asset sources. It has only two goals:

1. Let users obtain and use the skill
2. Ship a structured registry that AI can reference

### Contents

- `skills/game-asset-search/SKILL.md`  
  The skill instructions that describe the selection procedure and response format
- `skills/game-asset-search/ref/registry.json`  
  A structured registry of asset source sites at the site level
- `LICENSE`  
  The MIT License for the files in this repository

### Installation

Clone or download this repository.

```bash
git clone <repository-url>
cd game-asset-search-skill
```

### Placement

Place the `skills/game-asset-search/` directory under the `skills/` directory used by your tool or workflow. Keep the relative path between `SKILL.md` and `ref/registry.json` unchanged.

If your environment expects a different root directory, adapt only the outer placement and keep the internal `game-asset-search/` folder structure intact.

### Usage with Claude Code

If your Claude Code setup can load skills from a `skills/` directory, make `skills/game-asset-search/` available there and ask for asset-source recommendations with your constraints.

Examples:

- `Find sources for low-poly fantasy 3D assets for Unity with commercial-friendly licensing.`
- `Recommend sites for pixel art UI assets, and include cautions and query hints.`

The skill is designed to read `registry.json` and return roughly 3 to 5 recommended sources, why they fit, cautions, and suggested query hints.

### Notes

- The registry summarizes **site-level** tendencies and cautions only. It does not guarantee anything about individual assets.
- Always verify the final license, quality, authenticity, and commercial-use terms on the source site and on the specific asset page.
- This repository does not include scraping, APIs, a database, a search UI, vector search, or automatic updates.
- Piskel and Aseprite are included as pixel-art creation or editing tools rather than primary asset-distribution catalogs.

### Distribution-only notice

This repository is for distribution only. Feedback and support are not provided here. It is not designed around Issues or Discussions as a support channel.

### License scope

The license of this repository applies only to the files in this repository. External asset sources and individual assets are subject to their own licenses and terms.
