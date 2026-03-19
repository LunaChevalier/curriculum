# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## リポジトリの概要

職務経歴書（履歴書）のリポジトリです。`README.md` に職務経歴が記載されており、masterブランチへのpush時にGitHub Actionsが自動でPDFを生成して同リポジトリにコミットします。

## コマンド

### PDFのローカル生成

```bash
npm install
npx md-to-pdf --stylesheet ./pdf.css --pdf-options '{ "format": "A4", "margin": "20mm" }' README.md
```

生成物は `README.pdf` として出力されます。

## アーキテクチャ

- **`README.md`**: 職務経歴書の本文（編集対象はここのみ）
- **`pdf.css`**: PDF生成時のスタイルシート（日本語フォント設定を含む）
- **`.github/workflows/generate-pdf.yml`**: masterへのpush時に自動でPDFを生成し、`README.pdf` としてコミットするGitHub Actionsワークフロー
- **`package-lock.json`**: 依存パッケージ（`md-to-pdf ^5.1.0`のみ）

## 運用ルール

- 職務経歴の編集は `README.md` のみを変更する
- `README.pdf` はGitHub Actionsが自動生成するため、手動で編集しない
- masterへpushするとPDF自動生成が走り、`generate PDF` というコミットメッセージでPDFがコミットされる
