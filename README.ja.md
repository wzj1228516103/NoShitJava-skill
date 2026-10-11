# NoShitJava-skill

[English](README.en.md) · [简体中文](README.md) · 日本語 · [Español](README.es.md)

<div align="center">
  <img src="data/images/noshitjava-skill-logo.png" alt="NoShitJava-skill プロジェクトビジュアル" width="260">
  <p><strong>屎山なしの Java —— AI による Java 開発フルサイクルアシスタント</strong><br>
  <sub>A Java development skill for keeping codebases maintainable.</sub></p>
</div>

> Java/Spring バックエンド向けのオンデマンド読み込みスキル：コード生成・API 設計・データベース変更・コードレビュー・テスト追加が、一貫した本番品質の制約に従います。

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![CI](https://github.com/wzj1228516103/NoShitJava-skill/actions/workflows/quality.yml/badge.svg?branch=master)](https://github.com/wzj1228516103/NoShitJava-skill/actions/workflows/quality.yml)
[![Java](https://img.shields.io/badge/Java-17%2B-orange.svg)](https://www.oracle.com/java/technologies/javase/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![理論：無屎理論](https://img.shields.io/badge/理論-無屎理論-2563EB)](THEORY.md)
[![副作用：保守性向上](https://img.shields.io/badge/副作用-保守性向上-success)](THEORY.md)

![NoShitJava-skill アーキテクチャ：ルーティング、7 つのエントリ、オンデマンドのルールライブラリ、プロジェクト設定と評価リグレッション](data/images/noshitjava-skill-architecture.png)

![NoShitJava-skill 全体紹介：7 つの開発フロー入口、技術スタックとエンジニアリング能力](data/images/noshitjava-skill-overview.png)

## 概要

NoShitJava-skill は Java/Spring バックエンド向けで、『Alibaba Java 開発マニュアル（黄山版）』をベースに一般的なエンジニアリング実践を補足しています。タスクに関連するルールだけを読み込み、開発・設計・レビュー・テスト・バグ修正・リファクタリング・規約検索を支援します。プロジェクト独自の規約やセキュリティレビューの代わりにはなりません。

ルールの詳細、リポジトリ構成、メンテナンス方法は[詳細版 README](README-DETAILS.md)（中国語）をご覧ください。

## 無屎理論（No-Shit Theory）

「大水理論（水をたくさん飲む）」「大睡理論（たくさん寝る）」の兄弟分として、一日の 3 番目の大事——**コードを書くこと**——を担当します。核心は一句：

> 屎山は一度で書かれるものではない。「とりあえず今はこう、後で直そう」が積もってできるものだ。

三か条：**書く前に設計する。境界と失敗パスはテストで守る。セキュリティとデータ正確性の赤線は譲らない。** 本スキルはこの理論を AI に実践させるための道具——7 つのエントリで三か条を守らせ、規約はオンデマンドで服用します。理論の全文は[『無屎理論宣言』](THEORY.md)（中国語）で。

## 7 つのエントリ

| エントリ | 用途 | 主な成果物 |
|---|---|---|
| `/java-dev` | 新機能の実装 | プロジェクトの既存スタイルに合わせて API・ビジネスロジック・スケルトンを実装 |
| `/java-design` | 設計から着手 | API・テーブル設計・トランザクション・リスクを整理 |
| `/java-review` | コードチェック | 証拠に基づく問題を位置と修正案つきで指摘 |
| `/java-test` | テスト追加 | 正常系・境界・異常系をカバー |
| `/java-fix` | 不具合調査 | 原因を特定し、必要な修正とリグレッションテストを追加 |
| `/java-refactor` | レガシーコード整理 | 動作を変えずに段階的に改善 |
| `/java-rules` | 規約検索 | 具体例でルールと適用条件を解説 |

`/java-dev` などの名称はエントリ名であり、お使いの AI ツールのスラッシュコマンドと一致するとは限りません。使えなくても問題ありません。スキルを有効にしたら、やりたいことを普通の言葉で伝えるだけで動作します。

## 効果検証

同一の Java/Spring タスクをスキルあり / なしで評価し、規約の項目ごとに採点しました：

| **指標** | **スキルあり** | **なし** | **改善** |
|---|---:|---:|---:|
| **品質アサーション平均通過率（holdout-v6）** | **100.00%** | 88.89% | **+11.11pp** |
| **ケース完全通過率（holdout-v6）** | **100.00%**（15/15） | 73.33%（11/15） | **+26.67pp** |
| **最悪ケース平均品質率（holdout-v6）** | **100.00%** | 77.78% | **+22.22pp** |
| **品質アサーション平均通過率（eval-v9）** | **100.00%** | 91.67% | **+8.33pp** |

品質アサーション通過率は Judge（自動評価モデル）の品質アサーションで集計し、`expect` ゲートは含みません。holdout-v6 は検証のために取り分けたタスク集合、eval-v9 はメインスイートです。評価設定・ケース・指標は [`evals/`](evals/README.md) を参照。ソースタスクはチューニングに使用したため、結果はリグレッション検証であり、独立した汎化効果の証明ではありません。

## カバレッジ

| 分野 | 内容 |
|---|---|
| Java 基礎 | 命名、日時、金額、コレクション、並行処理、リソース解放 |
| Spring API | Controller、DTO、バリデーション、レスポンス、API 互換性 |
| データとトランザクション | SQL、インデックス、ページング、トランザクション、冪等性、マイグレーション |
| セキュリティと信頼性 | 認可、ログのマスキング、キャッシュ、メッセージ、タイムアウト、リトライ |
| テストとアーキテクチャ | 単体/結合テスト、レイヤリング、モジュール境界 |

## インストール

次のコマンドで NoShitJava-skill を Codex にインストールできます：

```bash
npx skills add https://github.com/wzj1228516103/NoShitJava-skill -g -a codex -y
```

インストール後、次のコマンドで確認します：

```bash
npx skills list -g -a codex
```

`noshitjava-skill` が表示されればインストール完了です。Codex を再起動し、メッセージで `$noshitjava-skill` に続けてタスクを入力してください。見つからない場合は Codex を再起動して再度確認してください。

## 使用例

スキルを有効にしたら、エントリ名を暗記する必要はありません。普通に要件を伝えるだけです：

| こう伝える | どう動くか |
|---|---|
| 「このプロジェクトの既存の書き方に合わせて、注文作成 API を追加し、関連テストを実行して。」 | 既存コードと技術スタックを確認してから実装し、検証します。 |
| 「この変更の権限・トランザクション・SQL の問題をチェックして。レビューのみで、コードは変更しないで。」 | コードの証拠に基づき問題・位置・修正案を指摘します。勝手には変更しません。 |
| 「在庫引き落としはどう設計すべき？並行制御と失敗時の扱いも含め、まず案を出して。」 | コードを書く前に設計とリスクを整理します。 |
| 「この API はときどき古い注文ステータスを読む。原因を突き止めて修正し、リグレッションテストを追加して。」 | 原因を調査し、必要な修正を行い、関連テストを確認します。 |

## プロジェクト設定

- `memory.md` に個人の好みを保存し、`project/_template.md` をコピーしてプロジェクトごとの技術スタックと規約を記入します。
- プロジェクトの規約は個人設定より優先されますが、セキュリティとデータ正確性の要件は緩和できません。その場限りの選択を長期設定に書き込まず、認証情報や内部情報もコミットしないでください。

設定の詳細は [`project/README.md`](project/README.md) をご覧ください。

## 適用範囲

- ルールは現在のタスクにのみ適用します。デモや使い捨てスクリプトは軽量なままで構いません。
- プロジェクトの既存規約が優先されます。ただしセキュリティとデータ正確性の要件は緩和できません。スキルを使わないようユーザーが求めた場合は適用を停止します。

本プロジェクトはエンジニアリングの指針を提供するものであり、チームのセキュリティ監査・データベース変更承認・リリースプロセスの代わりにはなりません。

## 参考文献・謝辞

- [**Alibaba Java 開発マニュアル（黄山版）**](https://github.com/alibaba/p3c) —— 本スキルの規約の出典。Alibaba Java コミュニティの実践の集大成であり、本プロジェクトは関連部分の選定と再編成のみ行っています。
- [Alibaba Java Development Guide](https://github.com/Sxuan-Coder/alibaba-java-development-guide) —— オンデマンドルーティング、ルールのレベル分け、プロジェクト設定を参考。
- [backend-skill](https://github.com/zhangloveyan/backend-skill) —— 開発フロー、コードテンプレート、テストループを参考。
- [**skill-up**](https://github.com/alibaba/skill-up) —— `evals/` のベンチマークとリグレッションを支える評価ツール。

本プロジェクトは Alibaba の公式製品ではなく、Alibaba の承認も受けていません。オリジナルコンテンツは [MIT License](LICENSE)、引用コンテンツとサードパーティ素材はそれぞれのライセンスに従います。
第三者ソース・改変範囲・ライセンスは [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) をご覧ください。

## メンテナンスとフィードバック

Issue や改善提案を歓迎します。変更後はリポジトリのメンテナンスチェックを実行できます：

```powershell
pwsh -NoProfile -File ./data/maintenance/scripts/validate-registry.ps1
pwsh -NoProfile -File ./data/maintenance/scripts/validate-content.ps1
```

バージョン履歴は [CHANGELOG](CHANGELOG.md)、セキュリティポリシーは [SECURITY](SECURITY.md) をご覧ください。
コントリビューターは[コントリビューションガイド](CONTRIBUTING.md)と[行動規範](CODE_OF_CONDUCT.md)を先にお読みください。
