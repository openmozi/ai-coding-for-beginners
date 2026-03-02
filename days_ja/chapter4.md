# 第4章:プログラミングインテリジェントエージェントパターン

## 授業概要

開発者は「実行」から「管理」へと変化しています。Subagentsは未来のトレンドです:エージェントがエージェントを管理します。

### 学習目標
- エージェント管理の設計パターンを理解する
- Claude Codeの使用テクニックをマスターする
- Hooks、Commands、Subagentsの使用方法を学ぶ
- Anthropicの内部実践経験を理解する

---

## 1. 開発の進化トレンド

### 1.1 開発役割の進化

```mermaid
graph LR
    subgraph "開発進化の4段階"
        S1[段階1<br/>単一の開発者<br/>自分の成果物を管理]
        S2[段階2<br/>チームリーダー<br/>複数の開発者を管理]
        S3[段階3<br/>チームリーダー + AI<br/>開発者の成果物を管理]
        S4[段階4<br/>単一の開発者<br/>複数のAI Agentsを管理]
    end

    S1 --> S2 --> S3 --> S4

    style S1 fill:#bfb
    style S2 fill:#bbf
    style S3 fill:#f9f
    style S4 fill:#f55
```

| 段階 | 役割 | 説明 |
|------|------|------|
| 1 | 独立開発者 | 単一の開発者が単一の開発者の成果物を管理 |
| 2 | チームリーダー | リーダーが複数の開発者の成果物を管理 |
| 3 | AI支援チーム | リーダーが複数の開発者の成果物を管理(AIシステムの支援あり) |
| 4 | エージェント管理者 | 単一の開発者が複数のAIエージェントの作業を管理 |

### 1.2 ソフトウェアチームの歴史

```mermaid
timeline
    title ソフトウェアチーム発展の歴史
    1940 : 独立開発者が完全なプロジェクトを処理
    1960 : 初のソフトウェアチームが出現<br/>(NASA、DoDプロジェクトの需要が推進)
    1970 : ソフトウェアチームの主流採用<br/>専門化された役割が出現
    1990 : ソフトウェアエンジニアリングの成熟<br/>方法論とツールの標準化
    2023 : 開発者が多様なエージェントグループを管理
    2025 : 開発者 + AIコーディングシステムの協力
    2030 : 未来展望
```

| 年度 | マイルストーン | 象徴的な変化 |
|------|--------|------------|
| 1940 | 独立開発者 | 1人が完全なプロジェクトを処理 |
| 1960 | 初のソフトウェアチーム | NASA、DoDプロジェクトの需要が推進 |
| 1970 | 主流採用 | 専門化された役割が出現 |
| 1990 | エンジニアリングの成熟 | 方法論とツールの標準化 |
| 2023 | エージェントグループ管理 | 開発者が多様なエージェントを管理 |
| 2025 | AI協力 | 開発者 + AIコーディングシステム |
| 2030 | 未来展望 | エージェントがエージェントを管理 |

---

## 2. プログラミング生産性の指数関数的成長

### 2.1 プログラミング言語の生産性の進化

```mermaid
graph LR
    subgraph "プログラミング言語の生産性成長"
        direction LR
        A[1950s<br/>Fortran/Assembly] --> B[1960s<br/>Cobol/Basic]
        B --> C[1970s<br/>C/Pascal]
        C --> D[1980s<br/>C++/Objective-C]
        D --> E[1990s<br/>Java/Python]
        E --> F[2000s<br/>C#/Ruby]
        F --> G[2010s<br/>Go/Swift/Rust/TypeScript]
        G --> H[2020s<br/>AI-Assisted Coding]
    end
```

**重要な洞察**:プログラミング言語の生産性はAIによって推進され、指数関数的に成長しています。

### 2.2 IDEの生産性の進化

```mermaid
graph LR
    subgraph "IDEの生産性成長"
        I1[IBM 029<br/>1964] --> I2[ed<br/>1969]
        I2 --> I3[Smalltalk-80<br/>1980]
        I3 --> I4[Visual Basic<br/>1991]
        I4 --> I5[Eclipse<br/>2001]
        I5 --> I6[Sublime/Neovim<br/>2010s]
        I6 --> I7[Copilot<br/>2021]
        I7 --> I8[Devin/Claude Code<br/>2024]
    end
```

**重要な洞察**:IDEの生産性も同様の指数関数的成長を示し、同じくAIによって推進されています。

### 2.3 検証方法の進化

```mermaid
graph TB
    subgraph "検証方法の進化"
        V1[手動デバッグ]
        V2[静的型付け<br/>Algol]
        V3[自動化テスト]
        V4[継続的インテグレーション<br/>CI]
        V5[プロパティテスト<br/>QuickCheck]
        V6[E2Eテスト]
        V7[カオステスト<br/>Chaos Monkey]
        V8[AI駆動脆弱性テスト]
        V9[AI駆動ユニットテスト<br/>TestGen]
        V10[AI駆動ファズテスト<br/>Sapienz]
        V11[Self Play]
    end

    V1 --> V2 --> V3 --> V4 --> V5 --> V6 --> V7 --> V8 --> V9 --> V10 --> V11

    style V8 fill:#f9f
    style V9 fill:#f9f
    style V10 fill:#f9f
    style V11 fill:#f9f
```

---

## 3. ソフトウェアタスクのステップと責任分担

### 3.1 タスクステップの概要

```mermaid
graph TB
    subgraph "ソフトウェアタスクのステップ"
        R1[高レベル要件を提供 🟩]
        R2[要件を設計ドキュメントに変換 🟩/🟦]
        R3[ドキュメントからソリューションを実装 🟦]
        R4[テストを追加 🟦]
        R5[CIの通過を確保 🟦]
        R6[Code Review 🟦]
        R7[ドキュメントを更新 🟦]
    end

    R1 --> R2 --> R3 --> R4 --> R5 --> R6 --> R7

    style R1 fill:#bfb
    style R2 fill:#ff9
    style R3 fill:#bbf
    style R4 fill:#bbf
    style R5 fill:#bbf
    style R6 fill:#bbf
    style R7 fill:#bbf
```

### 3.2 責任分担の凡例

| 色 | 意味 | 実行者 |
|------|------|--------|
| 🟩 緑色 | 人間主導 | 開発者 |
| 🟩/🟦 黄色 | 協力完成 | 開発者 + エージェント |
| 🟦 青色 | エージェント主導 | AIエージェント |

---

## 4. エージェント管理テクニック

### 4.1 4つの核心技術

```mermaid
graph TB
    subgraph "エージェント管理テクニック"
        A[Agent Behavior Files<br/>CLAUDE.md/cursorrules/AGENTS.md]
        B[Hooks<br/>イベント駆動スクリプト]
        C[Commands<br/>よく使うプロンプトファイル]
        D[Subagents<br/>ランタイム委譲]
    end

    A --> |静的設定| E[エージェント行動ガイド]
    B --> |動的制御| F[確定的実行]
    C --> |効率向上| G[ワークフローの再利用]
    D --> |能力拡張| H[マルチエージェント協力]

    style A fill:#bfb
    style B fill:#bbf
    style C fill:#f9f
    style D fill:#f55
```

### 4.2 Hooks(フック)

> **定義**:事前定義されたイベントタイプで実行される確定的スクリプト

```mermaid
sequenceDiagram
    participant User as ユーザー
    participant Agent as エージェント
    participant Hook as Hookスクリプト
    participant Tool as ツール

    Note over User,Tool: PreToolUse Hook
    User->>Agent: タスクの実行を要求
    Agent->>Hook: PreToolUseトリガー
    Hook->>Hook: パラメータの検証/変更
    Hook-->>Agent: 許可/拒否
    Agent->>Tool: ツールを実行

    Note over User,Tool: PostToolUse Hook
    Tool-->>Agent: 結果を返す
    Agent->>Hook: PostToolUseトリガー
    Hook->>Hook: 結果の処理/検証
    Hook-->>Agent: 処理完了
    Agent-->>User: レスポンスを返す
```

**Hookのタイプ:**

| Hookタイプ | トリガータイミング | 典型的な用途 |
|-----------|----------|----------|
| `PreToolUse` | ツール使用前 | パラメータの検証、制約の追加 |
| `PostToolUse` | ツール使用後 | 結果の検証、ログ記録 |
| `UserPromptSubmit` | ユーザーがプロンプトを送信時 | 入力の前処理 |
| `PreCompact` | コンテキスト圧縮前 | 重要な情報を保持 |
| `...` | その他のタイプ | 継続的に拡張 |

### 4.3 Commands(コマンド)

> **定義**:よく使うプロンプトをファイルとして保存し、エージェントが実行

**使用シナリオ:**

| シナリオ | 説明 |
|------|------|
| テストの実行 | 自動化テストフロー |
| コードレビュー | 標準化されたレビューフロー |
| Git操作 | コミット、プッシュの標準化 |
| デプロイフロー | 自動化されたデプロイステップ |

**利点:**
- 高頻度ワークフローの再利用
- チームの標準化
- 繰り返し入力の削減

### 4.4 Subagents(サブエージェント)

> **定義**:ランタイム委譲、独立した開発者の役割を作成

```mermaid
graph TB
    subgraph "Subagentアーキテクチャ"
        Main[メインエージェント]

        Main --> FE[フロントエンドSubagent<br/>UI/UXに専念]
        Main --> BE[バックエンドSubagent<br/>API/データに専念]
        Main --> Test[テストSubagent<br/>テストに専念]
        Main --> Doc[ドキュメントSubagent<br/>ドキュメントに専念]
    end

    style Main fill:#f9f
    style FE fill:#bfb
    style BE fill:#bbf
    style Test fill:#ff9
    style Doc fill:#9ff
```

**Subagentの目的:**

1. **異なる開発者の役割を作成**
   - フロントエンド専門家
   - バックエンド専門家
   - テスト専門家
   - ドキュメント専門家

2. **コンテキストの明確な分離**
   - 独立したワークフローコンテキスト
   - コンテキストの汚染を回避

3. **カスタマイズ機能を提供**
   - カスタムシステムプロンプト
   - 専用ツールセット
   - 独立したコンテキストウィンドウ

4. **エージェントがエージェントを管理する方向へ**
   - 階層的管理
   - 専門化された分業

**参考リソース:**
- [Awesome Claude Agents](https://github.com/vijaythecoder/awesome-claude-agents)
- [SuperClaude Framework](https://github.com/SuperClaude-Org/SuperClaude_Framework)

### 4.5 Agent Behavior Files

| ファイル | ツール | 用途 |
|------|------|------|
| `CLAUDE.md` | Claude Code | Claudeが自動的にロードするコンテキスト |
| `cursorrules` | Cursor | Cursorのルール設定 |
| `AGENTS.md` | 汎用 | オープンフォーマットのエージェント指示 |

---

## 5. Claude Code詳細ガイド

### 5.1 Claude Codeの方法論

```mermaid
graph TB
    subgraph "Claude Codeの核心理念"
        W[Works Everywhere<br/>どこでも使える]
        T[Terminal-Native<br/>ターミナルネイティブ]
        L[Low-level Model Access<br/>低レベルモデルアクセス]
        I[Infinitely Hackable<br/>無限にカスタマイズ可能]
    end

    style W fill:#bfb
    style T fill:#bbf
    style L fill:#f9f
    style I fill:#ff9
```

### 5.2 SDLC全体をカバー

```mermaid
graph LR
    subgraph "ソフトウェア開発ライフサイクル"
        D1[Discover<br/>発見] --> D2[Design<br/>設計]
        D2 --> D3[Build<br/>構築]
        D3 --> D4[Deploy<br/>デプロイ]
        D4 --> D5[Support & Scale<br/>サポートと拡張]
    end

    D1 -.->|コードベースと履歴を探索| E1[Search docs<br/>オンボーディングと学習]
    D2 -.->|プロジェクトを計画| E2[Develop tech specs<br/>アーキテクチャを定義]
    D3 -.->|コードを実装| E3[Write & execute tests<br/>コミット/PRを作成]
    D4 -.->|CI/CDを自動化| E4[Configure envs<br/>デプロイを管理]
    D5 -.->|エラーをデバッグ| E5[Monitor usage<br/>大規模リファクタリング]
```

**チームのCLIツールを使用**:git、docker、bqなど、ソリューションに集中し、構文ではありません。

### 5.3 複数のインターフェース

```mermaid
graph TB
    subgraph "Claude Codeインターフェース"
        Terminal[Terminal<br/>ターミナル]
        IDE[IDE<br/>統合開発環境]
        Web[Web & iOS<br/>Webとモバイル]
        SDK[SDK<br/>開発者ツールキット]
    end

    subgraph "SDK使用例"
        SDK_Example["$ claude -p 'what did i do this week?' --allowedTools Bash(git log:*) --output-format stream-json"]
        SDK_Pipe["$ get-gcp-logs | claude -p 'correlate errors + commits' --output-format=json | jq '.result'"]
    end

    SDK --> SDK_Example
    SDK --> SDK_Pipe
```

### 5.4 インストール

```bash
npm install -g @anthropic-ai/claude-code
```

### 5.5 核心使用シナリオ

#### シナリオ1:コードベースQ&A + リサーチ

```mermaid
graph LR
    subgraph "コードベースQ&Aとリサーチ"
        Q1[コード構造の理解]
        Q2[Git履歴の追跡]
        Q3[Issue修正の理解]
        Q4[バージョン追跡]
        Q5[PR検証]
        Q6[作業サマリー]
    end
```

**質問例:**
```
> how do I make a new @app/services/ValidationTemplateFactory?
> why does recoverFromException take so many arguments? look through git history to answer
> why did we fix issue #18363 by adding the if/else in @src/login.ts api?
> in which version did we release the new @api/ext/PreHooks.php api?
> look at PR #9383, then carefully verify which app versions were impacted
> what did I ship last week?
```

#### シナリオ2:コードを書く

| モード | 説明 |
|------|------|
| **1-shot** | 1回で完成、シンプルなタスクに適している |
| **Sidekick** | アシスタントモード、人間とマシンの協力 |
| **Prototype** | 高速プロトタイプ、反復最適化 |

#### シナリオ3:ツールとMCPの統合

```bash
# MCP Serverを追加
$ claude mcp add barley_server -- node myserver

# MCPを使用
> use the barley mcp server to check for error logs
```

#### シナリオ4:パワーオートメーション

複雑なワークフローを自動化し、繰り返し作業を削減します。

### 5.6 タスクにワークフローを適応

```mermaid
graph TB
    subgraph "探索計画型タスク"
        EP1[explore] --> EP2[plan] --> EP3[confirm] --> EP4[code] --> EP5[commit]
    end

    subgraph "テスト駆動型タスク"
        TD1[tests] --> TD2[commit] --> TD3[code] --> TD4[iterate] --> TD5[commit]
    end

    subgraph "プロトタイプ反復型タスク"
        PI1[code] --> PI2[screenshot] --> PI3[iterate] --> PI1
    end
```

**ワークフロー例:**

**探索計画型:**
```
> figure out the root cause for issue #983, then propose a few fixes.
  Let me choose an approach before you code. ultrathink
```

**テスト駆動型:**
```
> write tests for @utils/markdown.ts to make sure links render properly
  (note the tests won't pass yet, since links aren't yet implemented).
  then commit. then update the code to make the tests pass.
```

**プロトタイプ反復型:**
```
> implement [mock.png]. Then screenshot it with puppeteer and iterate
  till it looks like the mock.
```

### 5.7 プロトタイプ反復の例

Claude CodeがUIデザインを迅速に反復する方法を示します:

```
> make it so instead of todos showing up as they come in, we hide the
  tool use and result for todos, and render a fixed todo list above
  the input. title it "/todo (1 of 3)" in grey

> actually don't show a todo list at all, and instead render the tool
  uses inline, as bold headings when the model starts working on a todo

> also add a todo pill under the text input, similar to bg tasks

> actually undo both the pill and headings. instead, make the todo list
  render to the right of the input, vertically centered with a grey divider

> instead of showing todos above the input, merge them into the spinner.
  show the current todo as the spinner message in active verb form
```

---

## 6. ベストプラクティス

### 6.1 保護措置

```mermaid
graph TB
    subgraph "ベストプラクティスフレームワーク"
        B1[慎重な保護措置]
        B2[監査可能性]
        B3[モデル選択]
        B4[定期的なCheckpoint]
    end

    B1 --> B1a[コードベースのテスト]
    B1 --> B1b[CI/CDベストプラクティス]

    B2 --> B2a[各エージェントのdiffをマーク]
    B2 --> B2b[操作ログを保持]

    B3 --> B3a[複雑なタスク: より多くのガイダンス]
    B3 --> B3b[シンプルなタスク: より少ない介入]

    B4 --> B4a[定期的なコミット]
    B4 --> B4b[ブランチ戦略]
```

### 6.2 核心原則

| 原則 | 説明 |
|------|------|
| **保護措置** | テスト、CI/CD、セキュリティチェック |
| **監査可能性** | 各エージェントのdiffをマーク、ログを保持 |
| **モデル選択** | 異なるタスクに異なるモデルを使用 |
| **定期的なCheckpoint** | 頻繁なコミット、ロールバックが容易 |

### 6.3 オープンな課題

1. **リサーチ段階の自動化**
   > どのタスクでも最初の10-20%のリサーチ段階を自動化する方法は?

2. **タスクキュー管理**
   > 保留中のタスクキューをどのように維持するか(1回限りの変更の方が簡単)?

---

## 7. Anthropic内部実践事例

> **How Anthropic Uses Claude Code**の読み物に基づく

### 7.1 各チームのClaude Code適用シナリオ

```mermaid
graph TB
    subgraph "Anthropicチームの適用"
        DI[Data Infrastructure<br/>Kubernetesデバッグ<br/>データワークフロー自動化<br/>新人コードベースナビゲーション]
        PD[Product Development<br/>製品機能開発<br/>バグ修正<br/>リファクタリング]
        SE[Security Engineering<br/>セキュリティコードレビュー<br/>脆弱性修正]
        DS[Data Science<br/>データ分析<br/>可視化]
        API[API Team<br/>APIドキュメント生成<br/>SDK開発]
        GM[Growth Marketing<br/>A/Bテスト分析<br/>マーケティング自動化]
        PX[Product Design<br/>デザインシステムドキュメント<br/>プロトタイプ反復]
    end
```

| チーム | 適用シナリオ |
|------|----------|
| **Data Infrastructure** | Kubernetesデバッグ、データワークフロー自動化、新人コードベースナビゲーション |
| **Product Development** | 製品機能開発、バグ修正、リファクタリング |
| **Security Engineering** | セキュリティコードレビュー、脆弱性修正 |
| **Data Science** | データ分析、可視化 |
| **API Team** | APIドキュメント生成、SDK開発 |
| **Growth Marketing** | A/Bテスト分析、マーケティング自動化 |
| **Product Design** | デザインシステムドキュメント、プロトタイプ反復 |

### 7.2 ベストプラクティスのポイント(Anthropicチームより)

1. **詳細なCLAUDE.mdファイル** - より詳細なドキュメントほど、Claude Codeのパフォーマンスが向上
2. **MCPサーバーを使用** - Claude Codeの能力を拡張
3. **スクリーンショット補助** - スクリーンショットで期待するインターフェースを示す
4. **インクリメンタル開発** - 一度に1つのステップを実装
5. **セッション終了時のドキュメント** - 完了した作業をまとめ、ワークフローを改善

---

## 8. 重要な教訓

```mermaid
graph TB
    subgraph "3つの重要な教訓"
        L1[6ヶ月後のモデルのために構築<br/>Build for the model<br/>six months from now]
        L2[進化する準備をする<br/>Be ready to evolve]
        L3[主体的に考える<br/>Ask not what the model<br/>can do for you]
    end

    style L1 fill:#f9f
    style L2 fill:#bbf
    style L3 fill:#bfb
```

### 8.1 核心的な洞察

1. **Build for the model six months from now**
   - モデルの能力は急速に向上
   - 今日の設計は未来の能力を考慮する必要がある

2. **Be ready to evolve**
   - ツールと方法論は急速に変化
   - 学習と適応能力を維持

3. **Ask not what the model can do for you**
   - モデルにより良いコンテキストを提供する方法を考える
   - ワークフローを主体的に最適化

### 8.2 生産性のトレンド

- **プログラミング言語の生産性**:指数関数的に成長中(AI駆動)
- **IDEの生産性**:同様の指数関数的成長を示す
- **検証方法**:AI駆動のテストが主流になりつつある

---

## 9. 実践演習

### 演習1: CLAUDE.mdの設定
プロジェクトのCLAUDE.mdを作成し、以下を含める:
- プロジェクト概要
- よく使うコマンド
- コードスタイル
- テスト説明

### 演習2: Claude Codeを使用
1. Claude Codeをインストール
2. コードベースを探索
3. コードを書いてみる
4. 異なるワークフローモードを実践

### 演習3: MCPを追加
MCP Serverを追加してみる、例:
```bash
claude mcp add barley_server -- node myserver
```

### 演習4: Hooksの設定
PreToolUse hookを作成し、ファイル変更前に検証を行う。

### 演習5: Subagentsを使用
異なるタスクのために専用のsubagent設定を作成してみる。

---

## 講義資料

### Lecture 7: How to be an Agent Manager
- [Slides (PDF)](../slides/week4-lecture1-agent-manager.pdf)
- **ゲストスピーカー**: Boris Cherny, Anthropic(Claude Code創設者)
- **日付**: 10/17/25

### Lecture 8: Welcome to Claude Code
- [Slides (PDF)](../slides/week4-lecture2-claude-code.pdf)
- **スピーカー**: Boris Cherny
- **核心**: Claude Codeアーキテクチャ、使用シナリオ、ベストプラクティス

---

## 読み物

### 必読
1. **[Claude Code公式ドキュメント](https://docs.anthropic.com/en/docs/claude-code)**
2. **[How Anthropic Uses Claude Code (PDF)](../readings/how-anthropic-uses-claude-code.pdf)**

### 推奨リソース
1. **[Awesome Claude Agents](https://github.com/vijaythecoder/awesome-claude-agents)**
2. **[SuperClaude Framework](https://github.com/SuperClaude-Org/SuperClaude_Framework)**

---

## 課題

**[Chapter 4 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week4)**

エージェント管理テクニックを実践し、カスタムワークフローを作成します。

---

## 次の章

[次の章:Chapter 5](./chapter5.md)

---
