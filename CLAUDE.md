# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Akarenga Open Source Hardware (OSHW) プロジェクトのドキュメントサイト。MkDocs + Material テーマで構築する。

## Repository Architecture

単一の public リポジトリ `akarenga-oshw/akarenga-oshw.github.io` でソースと配信の両方を行う。

| ブランチ | 役割 |
|---|---|
| `main` | **公開ブランチ**。push されると Actions がビルドし `gh-pages` へデプロイ |
| `gh-pages` | ビルド済み HTML。GitHub Pages の配信元。直接編集しない |
| 作業ブランチ | PR 経由で `main` にマージする |

デプロイの流れ: `main` に push → GitHub Actions が `mkdocs gh-deploy --force` を実行 → `gh-pages` が更新され `https://akarenga-oshw.github.io/` に反映。

公開を遅らせたいページは、そのブランチを `main` にマージせず PR を開いたままにする。

**ハードウェア設計データ (回路図・ガーバー・BOM) は、リリース承認が出るまでリポジトリに入れない。** public リポジトリでは git 履歴からファイルを完全に削除できないため。

## Commands

```bash
pip3 install -r requirements.txt  # 依存関係インストール
mkdocs serve                       # ローカルプレビュー (http://127.0.0.1:8000)
mkdocs build                       # 静的サイト生成 → site/
```

デプロイは Actions が行うため、手元から `mkdocs gh-deploy` を実行する必要はない。

## Notes

- SSH は `~/.ssh/config` のホストエイリアス `github-akarenga` 経由で akarenga-oshw アカウント用の鍵を使う (remote URL は `git@github-akarenga:...`)
- `site/` はビルド成果物 (.gitignore 済み)
- MkDocs 2.0 に関する Material チームの警告がビルド時に出るが、現行構成には影響しない
