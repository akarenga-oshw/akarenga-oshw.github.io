# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Akarenga Open Source Hardware (OSHW) プロジェクトのドキュメントサイト。MkDocs + Material テーマで構築する。

## Repository Architecture

ソースと配信を 2 つのリポジトリに分けている。**ソースは常に private に留め、public 側にはビルド済み HTML だけを送る**。これは公開前の下書きが GitHub 上でクロールされるのを防ぐため。

| リポジトリ | 可視性 | 役割 |
|---|---|---|
| `akarenga-oshw.github.io-develop` (このリポジトリ) | private | MkDocs ソース。編集はすべてここで行う |
| `akarenga-oshw.github.io` | public | `gh-pages` ブランチで配信するのみ。ソースは置かない |

デプロイの流れ: このリポジトリの `main` に push → GitHub Actions が `mkdocs build` → `peaceiris/actions-gh-pages` が deploy key (`ACTIONS_DEPLOY_KEY`) で public リポジトリの `gh-pages` へ push → `https://akarenga-oshw.github.io/` に反映。

`main` への push が公開スイッチになる。公開前の作業は `develop` など別ブランチで行い、`main` にマージしない。

## Commands

```bash
pip3 install -r requirements.txt  # 依存関係インストール
mkdocs serve                       # ローカルプレビュー (http://127.0.0.1:8000)
mkdocs build                       # 静的サイト生成 → site/
```

`mkdocs gh-deploy` は使わない (public リポジトリへの配信は Actions が担うため)。

## Notes

- SSH は `~/.ssh/config` のホストエイリアス `github-akarenga` 経由で akarenga-oshw アカウント用の鍵を使う (remote URL は `git@github-akarenga:...`)
- `site/` はビルド成果物 (.gitignore 済み)
- MkDocs 2.0 に関する Material チームの警告がビルド時に出るが、現行構成には影響しない
