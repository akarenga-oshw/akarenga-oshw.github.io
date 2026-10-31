# Akarenga OSHW Docs

Akarenga OSHW プロジェクトのドキュメントサイトのソースです。

https://akarenga-oshw.github.io/

## 構成

| パス | 内容 |
|---|---|
| `docs/` | ドキュメント本体 (Markdown) |
| `mkdocs.yml` | MkDocs 設定 |
| `overrides/` | テーマのテンプレート上書き |

## ローカルで確認する

```bash
pip install -r requirements.txt
mkdocs serve
```

`http://127.0.0.1:8000` で確認できます。

## 公開の仕組み

`develop` が開発用のブランチです。`main` にマージすると GitHub Actions がサイトをビルドし、公開サイトへ反映されます。

## コントリビュート

ブランチ運用と執筆手順は [CONTRIBUTING.md](CONTRIBUTING.md) を参照してください。
