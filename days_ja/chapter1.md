# 第1章：プログラミングLLMとAI開発入門

## コース概要

大規模言語モデル時代において、ソフトウェア開発は革命的な変革を遂げています。本コースでは、最新のAIプログラミングツールを習得し、AI支援開発のベストプラクティスを理解していきます。

### 学習目標
- 大規模言語モデル(LLM)の基本原理を理解する
- 効率的なプロンプトエンジニアリング技術を習得する
- Human-agent engineeringの中核スキルを明確にする
- LLMの能力の境界を理解する

---

## 1. なぜこれを学ぶのか?

> "You won't be replaced by AI. You'll be replaced by a competent engineer who knows how to use AI."

AIプログラミングは、未来のソフトウェアエンジニアにとってコアスキルです。AIを使えないエンジニアは、AIを使えるエンジニアに取って代わられるでしょう。しかし、これは「vibe coding」コースでは**ありません**。AIの出力を盲目的に信じてはいけません。Human-agent engineeringこそが中核なのです。

> Prompts are the lingua franca for getting LLMs to do what we want and also effectively programming them
>
> — Andrej Karpathy

### 悪いニュース vs 良いニュース

| ニュース | 内容 |
|------|------|
| **悪いニュース** | Windsurfチーム(AIプログラミング企業が買収された) |
| **良いニュース** | 開発者はこれまで以上に高効率に働ける; AIエンジニアは前例のないスピードで技術スタックとツールを習得できる |

---

## 1.1 コース情報

| 項目 | 内容 |
|------|------|
| コースコード | CS146S |
| 大学 | スタンフォード大学、2025年秋学期 |
| 講師 | Mihail Eric |
| コースウェブサイト | themodernsoftware.dev |

### コーススケジュール
- **授業時間**: 月曜/金曜 8:30-9:20 am PT
- **提出物**: 9回の課題(毎週1回) + 1つの期末プロジェクト
- **評価方法**: プロジェクト80% / 課題15% / 参加度5%

### 講師紹介
Mihail Ericはスタンフォード大学の学部生/大学院生で、以下の経験があります:
- セールス領域のステルススタートアップでAIをリード
- Amazon AlexaでLLMの初期構築に携わる
- ML教育スタートアップを創業・売却
- YCが支援するAIプログラミング企業を創業

### コースTA
- Febie Lin

### ゲスト講義
本コースには、トップAI開発者スタートアップの創業者によるゲスト講義が含まれます:
- 数億ドルの資金調達、数十億ドルの評価額
- これらの講義を見逃さないでください!

### Human-agent Engineeringのコアスキル
1. **大量のコードを読んでレビューする** - 良いコードと悪いコードを見分ける方法を学ぶ
2. **良いセンスを持つ** - 優れたソフトウェアとは何かを理解する
3. **積極的に実験する** - 誰も標準的な答えを持っていない、全員が探索している

### 重要な洞察
- LLMはあなたと同じくらい優秀(良いコンテキストが良いコードを生む)
- もしあなたが自分のコードベースを理解できないなら、LLMも理解できない

---

## 2. LLM基礎概念

### LLMとは何か?
LLM(Large Language Models、大規模言語モデル)は、次のトークン予測のための**自己回帰モデル**(autoregressive models)です。

```
入力テキスト → トークン化 → 埋め込み → Transformerレイヤー(12-96+) → 出力予測
```

#### Transformerレイヤー
- セルフアテンションメカニズムを使用(Self-attention mechanism、Viswani et al.を参照)
- 12-96+レイヤーのTransformer
- トークンを固定次元の数値ベクトルに変換(~1-3K次元)

#### 埋め込み
テキストトークンを固定次元の数値ベクトルに変換します。

---

## 3. LLM訓練プロセス

### 3つの訓練段階

| 段階 | 名称 | データ量 | 目標 |
|------|------|--------|------|
| Stage 1 | Self-supervised Pretraining | 100B - 1T+ tokens | 言語概念を学習 |
| Stage 2 | Supervised Finetuning | 10K - 100K pairs | 指示に従う |
| Stage 3 | Preferencing Tuning | 10K - 100K comparisons | 人間の好みに整合 |

### Stage 1: 事前学習 (Pretraining)
- 大量の公開データを使用(Common Crawl, Wikipedia, StackExchange、GitHub)
- 言語の基本概念とパターンを学習
- **例**: "Write a for loop" → "that could be used in a piece of code"

### Stage 2: 教師あり微調整 (SFT)
- 高品質な指示-応答ペアを使用
- モデルに人間の指示に従うことを教える
- **例**: "what is the capital of Croatia" → "Zagreb is the capital"

### Stage 3: 好み調整 (Preferencing)
- 同じプロンプトに対する複数の出力ペアを収集
- 報酬モデルを訓練して好ましい出力を予測
- 人間の好み(有用性、正確性、可読性)に整合
- **例**: "Write a for loop" → "for idx in range(10):"

#### Reasoning Models(推論モデル)
- chain-of-thought推論トレースを追加
- ツール使用能力を統合
- 強化学習を通じて推論プロセスの評価を学習
- バックトラックなどの推論ステップを学習

#### モデル規模の参考
- GPT-3 / Claude 3.5 Sonnet: ~175Bパラメータ
- LLaMA 3.1: 405Bパラメータ
- GPT-4: ~1.8Tパラメータ

---

## 4. LLMの能力と限界

### 強み
- **Expert-level code completion** - エキスパートレベルのコード補完
- **Code understanding** - コード理解
- **Code fixing** - コード修正

### 限界性
| 限界 | 説明 | 対応策 |
|--------|------|----------|
| Hallucinations | 幻覚(存在しない/古いAPIを生成) | 堅牢なコンテキストエンジニアリング |
| Context window limits | コンテキストウィンドウの制限(~100-200K tokens、ただし全てが同等に有効というわけではない) | 厳選されたコンテキスト |
| Latency | 遅延(1秒から数分まで様々) | タスクに応じた計画 |
| Cost | コスト(入力$1-3/百万tokens、出力$10+/百万) | プロンプト長の最適化 |

---

## 5. プロンプトエンジニアリング技術

### プロンプトエンジニアリングの背景
プロンプティングは芸術であると同時に科学でもあります。LLMのブラックボックス特性は、いくつかの「LLMウィスパリング」トリックを意味します...しかし、LLMのパフォーマンスを経験的に向上させる確立された技術があります。

### Zero-shot Prompting
例を示さずに、LLMに直接タスクを実行させます。

**例**: Write me a Rust for-loop that iterates over a list of strings for every, printing every value in an even index

### K-shot Prompting
k個の例(1, 3, 5個)を提供します。「コンテキスト内学習」(in-context learning)とも呼ばれ、特定のフォーマットが必要なタスクに適しています。

**例**:
```
Write a for-loop iterating over a list of strings using the naming convention in our repo. Here are some examples of how we typically format variable names.

<example>var StRaRrAy = ['cat', 'dog', 'wombat']</example>
<example>def func CaPiTaLiZeStR = () => {}</example>
```

### Chain-of-Thought (CoT)
- **Multi-shot CoT**: 推論ステップの例を示す
- **Zero-shot CoT**: "Let's think step-by-step"を追加するか、明示的な<reasoning>タグ内で推論するようプロンプト
- 複数ステップの論理タスク(プログラミング、数学)に適している

### Role Prompting
モデルのロールを指定して、出力品質を向上させます。

**ロールプロンプトの例**:
```
You are a helpful assistant that loves programming at the level of a senior software developer and is very detailed and pedantic in your answers.
```
```
You are a Gen Z digital bestie. Always sound like you're texting on Snapchat at 2am.
```

### System Prompt vs User Prompt

| タイプ | 説明 |
|------|------|
| **System Prompt** | 最初のメッセージで、LLMの全体的な動作とルールを定義(通常エンドユーザーには見えない) |
| **User Prompt** | ユーザーの実際のリクエストと指示 |
| **Assistant** | LLMが実際に生成する応答 |

### ベストプラクティス

#### プロンプトの改善
- [Claude Prompt Improver](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/prompt-improver)を使用
- コンテキストをほとんど知らない人にプロンプトを見せて、その人が混乱したらLLMも混乱する

#### 構造化プロンプト
```
Here are the logs:
<log>LOG MESSAGE</log> and the stack trace:
<error>STACK TRACE</error>
```

#### 明確で具体的に
- 言語、技術スタック、ライブラリ、制約条件を指定

#### タスクの分解
- 複雑なタスクをシンプルなステップに分割

---

## 6. 実践演習

### 演習1: 異なるプロンプト技術を試す
Claudeまたはその他のLLMを使って試してみましょう:
1. Zero-shot: "Write a function to check if a number is prime"
2. K-shot: 例を提供した後、同じフォーマットで出力させる
3. CoT: "Let's think step-by-step"を追加して出力の変化を観察

### 演習2: ロールプロンプト
異なるロールプロンプトを試して、出力品質を比較しましょう:
- "You are a junior developer..."
- "You are a senior software architect..."
- "You are a Gen Z digital bestie..."

### 演習3: 構造化プロンプト
ログとエラー情報を提供し、LLMがどのように解析して応答するかを観察します。

### 演習4: Prompt Improverを使用
Claude Prompt Improverを使ってプロンプトを最適化し、改善効果を観察します。

---

## 7. コース学習パス

| 章 | トピック |
|------|------|
| Chapter 1 | LLM基礎 + プロンプトエンジニアリング |
| Chapter 2 | Coding Agent + MCP |
| Chapter 3 | AI IDE + 同期/非同期 |
| Chapter 4 | Agent管理 + Claude Code |
| Chapter 5 | AI開発プロダクトデザイン |
| Chapter 6 | テストとセキュリティ |
| Chapter 7 | Code Review |
| Chapter 8 | AIアプリケーション構築 |
| Chapter 9 | AI DevOps |
| Chapter 10 | 将来の展望 |

---

## 講義資料

### Lecture 1: Introduction and How LLMs are Made
- [Slides (PDF)](../slides/week1-lecture1-introduction.pdf)
- **講師**: Mihail Eric

### Lecture 2: Power Prompting for LLMs
- [Slides (PDF)](../slides/week1-lecture2-power-prompting.pdf)

---

## 読書資料

### 必読
1. **[Prompt Engineering Guide](https://www.promptingguide.ai/techniques)** - 包括的なプロンプトエンジニアリング技術ガイド
2. **[Deep Dive into LLMs (YouTube)](https://www.youtube.com/watch?v=7xTGNNLPyMI)** - LLMの詳細解説

### 選択読書
3. **[Prompt Engineering Overview](https://cloud.google.com/discover/what-is-prompt-engineering)** - Google Cloudのプロンプトエンジニアリング概要

---

## 課題

### LLM Prompting Playground
**[Chapter 1 Assignment](https://github.com/mihail911/modern-software-dev-assignments/tree/master/week1)**

実践を通じてLLMプロンプト技術を習得します。

---

## 重要な概念

| 用語 | 意味 |
|------|------|
| **Tokenization** | テキストがトークンに分割される方法 |
| **Context Window** | モデルが処理できるコンテキストの長さ |
| **Temperature** | 出力のランダム性を制御するパラメータ |
| **Embedding** | トークンを固定次元の数値ベクトルに変換 |
| **Human-agent Engineering** | 人間エンジニアがAIの管理者および意思決定者として機能 |
| **Autoregressive Models** | 自己回帰モデル、次のトークン予測に使用 |
| **Self-attention** | セルフアテンションメカニズム |
| **In-context Learning** | コンテキスト内学習、すなわちK-shot Prompting |

---

## 次の章

[次の章: Chapter 2](./chapter2.md)

---
