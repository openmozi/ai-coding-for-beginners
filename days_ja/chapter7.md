# 第7章:現代的ソフトウェアサポート

## コース概要

> "Software code review is one of the highest leverage activities you can do to become a better engineer"

コードレビューは最も高いレバレッジの活動です。AIコードレビューは、これまで以上に重要になっています。

### 学習目標
- コードレビューの重要性を理解する
- コードレビューのベストプラクティスを習得する
- AIコードレビューツールの使用方法を学ぶ
- AIコードレビューの限界を理解する

---

## 1. コードレビュー統計データ

| 指標 | データ |
|------|------|
| コードレビューエラー検出率 | 55-60% |
| コードレビューなしのエラー率 | 4.5 errors/100 lines |
| コードレビューありのエラー率 | 0.82 errors/100 lines |
| AT&Tケース | 生産性14%向上、欠陥90%減少 |
| テストモードエラー検出率 | 25-45% |

**出典**: Coding Horror

---

## 2. コードレビューで何をチェックすべきか?

### ロジックと正確性
- コードロジックは正しいか?
- バグはないか?
- 境界条件は処理されているか?

### 可読性と保守性
- コードは明確で読みやすいか?
- 命名は適切か?
- 関数が長すぎないか?

### パフォーマンス
- パフォーマンス上の問題はないか?
- アルゴリズムは最適か?
- 不要な計算はないか?

### セキュリティ
- セキュリティ脆弱性はないか?
- 入力検証は十分か?
- 機密データ漏洩のリスクはないか?

### ベストプラクティス
- プロジェクト規範に従っているか?
- 言語/フレームワークのベストプラクティスに従っているか?
- 重複したコードはないか?

---

## 3. 良いコードレビュー vs 悪いレビュー

### 悪いレビュー
> "This won't work"

### 良いレビュー
> "I see your new method matches the existing style in this file, taking [X] parameters. Having that many parameters hurts readability and implies the function is doing too much. What do you think about refactoring this method and the existing ones in a later pull request to reduce how many parameters they take?"

**出典**: Blake Smith

---

## 4. AIコードレビューツール

### 既存ツール

| ツール | 説明 |
|------|------|
| **Graphite** | AIコードレビュープラットフォーム、本講義のゲスト |
| **Greptile** | AIコードレビューサービス |
| **CodeRabbit** | AI駆動のコードレビュー |
| **Claude Code / Codex** | AI支援コードレビュー |

---

## 5. AIコードレビューは何を変えたか?

| 側面 | 変化 |
|------|------|
| **効率性** | 大量のコードを迅速にスキャンし、問題を発見 |
| **一貫性** | すべてのコードに同じ基準を適用 |
| **知識共有** | チームのベストプラクティスを普及 |
| **認知負荷の軽減** | ルーチンチェックを自動化 |
| **継続的改善** | システムが時間とともに学習し改善 |
| **全体的な理解** | コードベースをより包括的に理解 |

**出典**: Greptile, Graphite

---

## 6. AIコードレビューの限界

### 限界

| 限界 | 説明 |
|------|------|
| **より多くの設定/構成** | 追加の設定と学習が必要 |
| **誤検出** | システムの継続的なトレーニングが必要 |
| **イディオムを捉えられない** | 特定のリポジトリのイディオムやベストプラクティスを捉えられない場合がある |
| **複雑なロジック** | 複雑なビジネスロジックやアーキテクチャの意思決定を処理できない |
| **セキュリティ変更は慎重に** | セキュリティ変更には特別な注意が必要 |
| **エッジケース** | エッジケースを見逃すことが多い |

> **重要な注意**:AIを使用したコードレビューは、これまで以上に重要です。
> あなたがマージしたコードに責任を持ち、AIを責めることはできません。AIはアシスタントであり、あなたが最終責任者です。

---

## 7. 実践演習

### 演習1: コードレビューの練習
毎日コードレビューの練習を行い、習慣を身につけましょう。

### 演習2: AIを使用したレビュー支援
GraphiteまたはClaude Codeを使用してコードレビューを支援しましょう。

### 演習3: レビュー品質の向上
建設的なコードレビューフィードバックを提供する方法を学びましょう。

---

## 講義資料

### Lecture 13: AI Code Review
- [Slides (PDF)](../slides/week7-lecture1-code-review.pdf)
- **Guest Speaker**: Tomas Reimers, CPO of Graphite
- **日付**: 11/7/25

---

## 参考資料

1. **[Code Reviews: Just Do It](https://blog.codinghorror.com/code-reviews-just-do-it/)**
2. **[How to Review Code Effectively](https://github.blog/developer-skills/github/how-to-review-code-effectively-a-github-staff-engineers-philosophy/)**

---

## 課題

**[Week 7 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week7)**

コードレビューを実践し、コードレビュー能力を養いましょう。

---

## 次の章

[次の章:Chapter 8](./chapter8.md)

---
