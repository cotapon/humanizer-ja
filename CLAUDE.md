# humanizer-ja

[blader/humanizer](https://github.com/blader/humanizer)（英語版）の日本語適応版 Claude Code スキル。
日本語テキストからAI生成の痕跡を検出・除去し、より自然で人間らしい文章に修正します。

## ファイル構成

- `SKILL.md` — スキル定義（Single Source of Truth）
- `README.md` — ドキュメント（インストール方法、パターン一覧、バージョン履歴）
- `WARP.md` — 開発ガイド（Warpターミナル向け）

## 変更時の注意事項

### パターン数の整合
SKILL.md本文のパターンリスト、README.mdのパターンサマリーテーブル、WARP.mdの記述は常に一致させること。

### バージョニング
- SKILL.mdフロントマターの `version` フィールドを更新
- README.mdの「バージョン履歴」セクションに変更内容を追記
- 両ファイルを同一コミットで更新すること

## 日本語適応ルール（upstream-sync Issueへの対応）

`upstream-sync` ラベルのIssueで `@claude` から呼ばれた場合:

1. **Issue本文を分析**: compare URLとコミット一覧からアップストリームの変更内容を理解する
2. **3ファイルを読む**: SKILL.md、README.md、WARP.mdの現在の内容を確認する
3. **適応の判断**:
   - 新パターン追加 → 日本語の同等パターンとして意味的に適応する（直訳禁止）
   - 英語固有パターン（例: "actually"の過剰使用、英語の接続詞表現）→ スキップし、日本語で同等の問題があれば独自のパターンを考案する
   - 構造・プロセス・フォーマットの変更 → 同様の変更を日本語版に適用する
   - LICENSE や英語ドキュメントのみの変更 → スキップ
4. **変更の適用**: SKILL.md、README.md、WARP.mdに適応変更を加える
5. **変更不要な場合**: Issueにコメントで理由を説明しPR作成はスキップする
6. **PRの作成**: 変更がある場合、`upstream-sync` ラベルを付けてPRを作成する
   - PRのdescriptionに `<!-- upstream-new-sha: {new_sha} -->` を含めること（自動state更新に使用）
