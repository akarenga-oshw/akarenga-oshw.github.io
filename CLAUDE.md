# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

`akarenga-oshw-docs` is the documentation repository for the Akarenga Open Source Hardware (OSHW) project. The repository is in its early stages — structure, tooling, and content are still being established on the `docproto` branch before merging to `main`.

## Commands

```bash
pip3 install -r requirements.txt  # 依存関係インストール
mkdocs serve                       # ローカルプレビュー (http://127.0.0.1:8000)
mkdocs build                       # 静的サイト生成 → site/
mkdocs gh-deploy                   # gh-pages ブランチへ手動デプロイ
```

## Structure

- `docs/` — ドキュメントのソース (Markdown)
- `mkdocs.yml` — MkDocs 設定
- `site/` — ビルド成果物 (.gitignore 済み)
