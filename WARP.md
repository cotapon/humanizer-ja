# WARP.md

このファイルはWARP（warp.dev）がこのリポジトリで作業する際のガイダンスを提供します。

## このリポジトリについて
このリポジトリは**Claude Codeスキル**で、すべてMarkdownで実装されています。

「ランタイム」となる成果物は `SKILL.md` です。Claude CodeはYAMLフロントマター（メタデータと許可ツール）およびその後に続くプロンプト/指示を読み込みます。

`README.md` は人間向けです: インストール方法、使い方、パターンの概要が記載されています。

## 主要ファイル（相互関係）
- `SKILL.md`
  - 実際のスキル定義。
  - `name`（humanizer-ja）、`version`（3.0.0）、`description`、`allowed-tools` を含むYAMLフロントマター（`---` … `---`）で始まる。
  - フロントマターの後は編集者プロンプト: 20パターンのリストとBefore/After例。
- `README.md`
  - インストール・使用方法の説明。
  - 20パターンのサマリーテーブルとバージョン履歴を含む。

動作/内容を変更する場合、`SKILL.md` を信頼できる唯一の情報源として扱い、`README.md` を整合性を保って更新してください。

## よく使うコマンド

### Claude Codeへのスキルインストール
推奨（Claude Codeスキルディレクトリに直接クローン）:
```bash
mkdir -p ~/.claude/skills
git clone https://github.com/cotapon/humanizer-ja.git ~/.claude/skills/humanizer-ja
```

手動インストール/更新（スキルファイルのみ）:
```bash
mkdir -p ~/.claude/skills/humanizer-ja
cp SKILL.md ~/.claude/skills/humanizer-ja/
```

## スキルの「実行」方法（Claude Code）
スキルを呼び出す:
- `/humanizer-ja` と入力してテキストを貼り付ける

## 安全な変更方法

### バージョン管理（同期を保つ）
- `SKILL.md` のYAMLフロントマターに `version:` フィールドがある。
- `README.md` に「バージョン履歴」セクションがある。

バージョンを上げる場合は両方を更新すること。

### `SKILL.md` の編集
- 有効なYAMLフロントマットの書式とインデントを保持すること。
- パターン番号付けを意図的に変更する場合を除き安定させること（READMEのテーブルと例が同じ番号を参照しているため）。
- 現在は20パターン（日本語特化）。英語固有パターンは削除済み。

### 自明でない修正のドキュメント化
プロンプトを変更してトリッキーな失敗ケース（繰り返しの誤編集や予期しないトーンの変化など）に対応した場合は、何を修正しどこが問題だったかを説明する短いノートを `README.md` のバージョン履歴に追加すること。
