# Scratch Curriculum Project Rules

**Version: 1.2**

---

# 1. このプロジェクトの目的

本プロジェクトは、子ども向けScratch教材を体系的に制作・管理・公開するためのプロジェクトである。

教材は単なる「作品集」ではなく、次の3軸を関連付けて管理する。

1. **基礎**

   * Scratchの基本ブロック
   * プログラミングの基本概念
   * 検定につながる基礎知識

2. **技・ギミック**

   * 重力
   * ジャンプ
   * 円運動
   * 当たり判定
   * スクロール
   * 敵AI
   * 弾
   * HP
   * スコア
   * タイマー
   * クローン
   * その他ゲーム制作で頻繁に使う仕組み

3. **作品**

   * ゲーム
   * アニメーション
   * シミュレーション
   * オリジナル作品
   * 有名ゲームの仕組みを参考にした教材

生徒はWEB教材を見ながらScratch作品を制作する。

動画教材を基本とせず、

* 画像
* Scratchブロック
* 短い説明
* ステップ形式
* 動作確認
* 講師チェック

を中心としたWEB教材とする。

---

# 2. プロジェクトの基本方針

## 2.1 生徒が自分で進められる教材にする

WEBページを見れば、生徒自身が次に何をすればよいか判断できることを目標とする。

講師は常に横について説明するのではなく、

* 困ったときのサポート
* 理解度確認
* スタンプチェック
* 発展課題への誘導

を担当する。

---

## 2.2 完成体験を重視する

特に初心者・低学年では、

「分かった」

よりもまず、

「できた」
「動いた」
「完成した」

という体験を重視する。

その上で、

完成
↓
仕組みを理解
↓
改造
↓
オリジナル化

へ進める。

---

## 2.3 教材は徐々にステップアップする

教材には推奨学習順序を設定する。

ただし、完全な一本道にはしない。

生徒が興味のある作品を選択できる余地を残す。

必要な基礎や技が未習得の場合は、関連教材へ誘導できる構造にする。

---

# 3. 3者の役割

本プロジェクトでは、以下の3者で役割を分担する。

---

## 3.1 ChatGPT（チャッピー）

### 役割

**プロジェクトマネージャー / カリキュラム設計 / 品質管理**

### 主な担当

* プロジェクト全体管理
* カリキュラム設計
* 教材候補の整理
* LEVEL設計
* 基礎スキル体系設計
* ギミック体系設計
* 作品体系設計
* 検定体系設計
* 各教材仕様書作成
* Claude Code向け指示書作成
* Antigravity向け指示書作成
* 完成物レビュー
* カリキュラム全体の重複・不足チェック
* 修正方針決定
* STATUS管理
* CHANGELOG管理方針決定
* 仕様変更時の3者同期管理
* lesson-specと実装成果物の整合確認
* WEB教材が実際の授業で利用可能かの最終判断

### 原則

教材内容について最終判断が必要な場合は、チャッピーが全体設計との整合性を確認する。

---

## 3.2 Claude Code

### 役割

**Scratch教材・プログラム・データ実装担当**

### 主な担当

* Scratch完成作品制作
* Scratch開始用ファイル制作
* SB3関連処理
* project.json等のScratch内部データ処理
* lesson-manifest.json生成
* 教材用プログラム制作
* JSONデータ制作
* 必要な変換ツール制作
* 必要な素材処理
* 管理機能用プログラム制作
* 技術的検証
* プログラム修正
* 自動チェック・ビルド処理の検討

### Claude Codeが独自判断してはいけないもの

以下を独自変更しない。

* 教材の学習目的
* LEVEL
* STEP構成
* 使用する基礎項目
* 使用するギミック
* 検定対応
* 作品名
* 教材ID
* 完成条件
* 生徒に教える内容そのもの

変更が必要な場合は、着手前または作業途中でチャッピーへ差し戻す。

---

## 3.3 Antigravity

### 役割

**生徒向けWEB教材制作・UI/UX担当**

### 主な担当

* 生徒向け教材ページ
* STEP解説
* 基礎解説ページ
* ギミック解説ページ
* 作品検索画面
* 教材一覧
* 生徒進捗画面
* スタンプ画面
* 検定画面
* 素材ダウンロード画面
* 完成作品ダウンロード画面
* UI/UX改善
* 共通WEBコンポーネント制作
* デザインシステム整備
* スマートフォン・タブレット・PC表示対応

### Antigravityが独自判断してはいけないもの

以下を独自変更しない。

* STEP順序
* 学習内容
* 使用するScratchブロック
* 教材の完成条件
* 基礎・ギミック分類
* LEVEL
* 検定内容
* 教材ID
* 作品名

WEB上の見せ方は改善してよいが、教材仕様そのものは変更しない。

---

# 4. 情報の正本

## 最重要ルール

各教材について、

**lesson-spec.md を教材仕様の唯一の正本とする。**

チャット上の会話、口頭指示、Claude Code側のメモ、Antigravity側のメモよりも、

`lesson-spec.md`

を優先する。

仕様変更を行った場合は、必ずlesson-spec.mdへ反映する。

---

# 5. lesson-spec.mdの構造

lesson-spec.mdは、

**YAML frontmatter + Markdown本文**

で構成する。

## 5.1 YAML frontmatter

機械可読な情報を記録する。

例：

```yaml
---
lesson_id: SC001
title: クレーンゲーム
level: 1
spec_version: 1.0
status: draft

basics:
  - B001
  - B003
  - B004

gimmicks:
  - G001
  - G005

genre:
  - game
  - crane
---
```

## 5.2 Markdown本文

人間が読む詳細仕様を記載する。

最低限、以下を含める。

* 教材概要
* 完成条件
* 使用ブロック
* 使用スプライト
* 使用背景
* 使用音
* 素材一覧
* STEP構成
* 各STEPの目的
* 各STEPの完成条件
* Scratchコード設計
* オリジナル改造課題
* 講師チェック項目
* スタンプ条件
* 検定対応
* Claude Code向け注意事項
* Antigravity向け注意事項

---

# 6. spec_version

すべてのlesson-spec.mdに、

```yaml
spec_version: 1.0
```

のように仕様バージョンを記録する。

仕様変更時はバージョンを更新する。

例：

```text
1.0 → 1.1
1.1 → 1.2
```

大規模な仕様変更の場合は、

```text
1.x → 2.0
```

としてよい。

---

# 7. 実装側のspec version管理

Claude CodeとAntigravityは、それぞれREPORTに、

```text
implemented_spec_version: 1.0
```

を必ず記録する。

レビュー時にlesson-spec.mdのspec_versionと一致しているか確認する。

例：

```text
lesson-spec: 1.2
Claude Code: 1.1
Antigravity: 1.2
```

の場合、

Claude Code側は旧仕様として扱い、修正対象とする。

---

# 8. 着手前エスカレーション

Claude CodeまたはAntigravityが、以下のいずれかを発見した場合は、制作を開始または継続せず、チャッピーへ差し戻す。

* 技術的に実装不可能
* 著しく非効率
* 安全性・保守性に問題がある
* 仕様同士が矛盾している
* 必要情報が不足している
* 現実的な代替案が存在する
* 後工程へ大きな悪影響が予想される
* 生徒の理解を著しく妨げる
* ScratchとWEBの表記・動作に不一致がある

フロー：

```text
仕様受領
↓
実装前チェック
↓
問題なし
↓
制作開始
```

問題がある場合：

```text
仕様受領
↓
問題発見
↓
STOP
↓
チャッピーへ質問・提案
↓
仕様確認
↓
必要ならlesson-spec更新
↓
制作再開
```

---

# 9. GitHubフォルダ構成

```text
scratch-curriculum/
│
├── README.md
├── LICENSE
├── .gitattributes
│
├── 00_project/
│   ├── PROJECT_RULES.md
│   ├── CURRICULUM_MASTER.md
│   ├── STATUS.md
│   └── CHANGELOG.md
│
├── 01_master/
│   ├── basics.json
│   ├── gimmicks.json
│   ├── works.json
│   ├── exams.json
│   ├── levels.json
│   └── dictionary.json
│
├── 02_lessons/
│   ├── SC001/
│   │   ├── lesson-spec.md
│   │   ├── lesson-manifest.json
│   │   ├── claude-task.md
│   │   ├── claude-report.md
│   │   ├── antigravity-task.md
│   │   ├── antigravity-report.md
│   │   ├── review.md
│   │   │
│   │   ├── assets/
│   │   │
│   │   ├── scratch/
│   │   │   ├── source/
│   │   │   │   ├── start/
│   │   │   │   └── complete/
│   │   │   └── dist/
│   │   │       ├── SC001_start.sb3
│   │   │       └── SC001_complete.sb3
│   │   │
│   │   └── web/
│   │
│   └── ...
│
├── 03_basics/
├── 04_gimmicks/
├── 05_exams/
│
├── 06_templates/
│   ├── lesson-template.md
│   ├── lesson-manifest-template.json
│   ├── claude-task-template.md
│   ├── antigravity-task-template.md
│   ├── claude-code-report-template.md
│   ├── antigravity-report-template.md
│   └── scratch-lesson-review-template.md
│
├── 07_assets/
│   ├── ASSET_LICENSES.md
│   ├── common/
│   ├── images/
│   ├── sounds/
│   └── sprites/
│
├── 08_tools/
│
└── 09_web/
    ├── components/
    ├── styles/
    ├── scripts/
    └── design-system/
```

---

# 10. 教材IDルール

Scratch作品教材には連番IDを設定する。

```text
SC001
SC002
SC003
...
```

教材名を変更してもIDは変更しない。

---

# 11. 基礎ID

基礎学習項目には専用IDを設定する。

例：

```text
B001 座標
B002 向き
B003 繰り返し
B004 条件分岐
B005 変数
B006 乱数
B007 メッセージ
B008 クローン
```

最終的にはScratch主要ブロックを網羅する。

---

# 12. ギミックID

ゲーム制作で利用する技・仕組みにIDを設定する。

例：

```text
G001 キー移動
G002 重力
G003 ジャンプ
G004 二段ジャンプ
G005 当たり判定
G006 弾を撃つ
G007 敵追跡
G008 HP
G009 スコア
G010 タイマー
G011 円運動
G012 スクロール
```

---

# 13. lesson-manifest.json

各教材には、

`lesson-manifest.json`

を用意する。

これは、

**Scratch作品に実際に実装された内容を記録する実装事実データ**

として扱う。

lesson-spec.mdが、

**「何を教えるか」**

を定義するのに対し、

lesson-manifest.jsonは、

**「実際のScratch作品に何が存在するか」**

を記録する。

---

# 14. lesson-manifest.jsonの主な内容

最低限、以下を保持する。

```json
{
  "lesson_id": "SC001",
  "spec_version": "1.0",
  "sprites": [],
  "variables": [],
  "broadcasts": [],
  "backdrops": [],
  "sounds": [],
  "assets": [],
  "files": {
    "start_sb3": "",
    "complete_sb3": ""
  }
}
```

将来的には必要に応じて、

* ブロック一覧
* コスチューム
* 使用拡張機能
* Scratchバージョン
* STEP対応情報

等を追加してよい。

---

# 15. manifest生成

可能な限り、lesson-manifest.jsonはClaude CodeがScratch成果物から自動生成する。

手入力による表記ズレを避けることを目的とする。

SC001パイロットでは自動生成が難しい場合、手動作成を許可する。

ただし、将来的には自動生成を目標とする。

---

# 16. ScratchとWEBの完全一致項目

以下はScratch作品とWEB教材で原則完全一致させる。

* スプライト名
* 変数名
* メッセージ名
* 背景名
* 音名
* ファイル名
* 数値
* STEP内容
* 使用ブロック
* 完成条件

表記揺れを許容しない。

例：

Scratch側：

`スコア`

WEB側：

`得点`

のような言い換えは、原則行わない。

---

# 17. dictionary.json

プロジェクト全体で頻出する用語を、

`01_master/dictionary.json`

で管理することを検討する。

目的：

* 表記揺れ防止
* ScratchとWEBの表記統一
* 将来の検索
* ルビ・読み情報
* 用語説明

SC001段階では必須ではない。

---

# 18. 教材制作フロー

基本フローは以下とする。

```text
教材企画
↓
チャッピー
教材仕様作成
↓
lesson-spec.md確定
↓
実装前チェック
↓
┌───────────────┐
│               │
↓               ↓
Claude Code      Antigravity
Scratch制作      WEB制作
↓               ↓
manifest         WEB成果物
↓               ↓
REPORT           REPORT
└───────┬───────┘
        ↓
チャッピーレビュー
        ↓
review.md
        ↓
修正
        ↓
再レビュー
        ↓
承認
        ↓
公開
```

---

# 19. Claude Codeへの受け渡し

Claude Codeは、

```text
lesson-spec.md
claude-task.md
```

を読んで制作する。

制作終了後、

```text
lesson-manifest.json
claude-report.md
```

を更新する。

---

# 20. Claude Report

以下を記録する。

```text
教材ID
implemented_spec_version
実装完了項目
制作ファイル
manifest生成状況
仕様通り実装できなかった項目
仕様から変更を提案した項目
変更理由
技術上の注意
既知の問題
チャッピーへの確認事項
```

---

# 21. Antigravityへの受け渡し

Antigravityは、

```text
lesson-spec.md
lesson-manifest.json
antigravity-task.md
```

を確認して制作する。

Scratch作品が未完成の段階ではlesson-spec.mdをもとに先行制作してよい。

ただし、最終確認時にはlesson-manifest.jsonとの照合を必須とする。

---

# 22. Antigravity Report

以下を記録する。

```text
教材ID
implemented_spec_version
制作ページ
実装完了項目
STEP分割計画
UI上の改善
仕様変更提案
ルビ・漢字確認
半画面表示確認
PC表示確認
タブレット表示確認
スマホ表示確認
共通コンポーネント化メモ
既知の問題
チャッピーへの確認事項
```

---

# 23. review.md

チャッピーによるレビュー結果を記録する。

最低限、

```text
教材ID
reviewed_spec_version
レビュー日
Scratch確認
WEB確認
manifest整合確認
半画面表示確認
カリキュラム確認
修正依頼
再レビュー結果
最終承認
```

を含める。

---

# 24. 仕様変更時の同期ルール

lesson-spec.mdが変更された場合、チャッピーはClaude CodeとAntigravityの両方へ変更内容を通知する。

task.mdへ以下の形式で追記する。

```text
SPEC UPDATED: 1.0 → 1.1

変更内容：
- STEP 3を変更
- スコア変数の仕様変更
- 素材1点追加
```

Claude CodeとAntigravityは、作業開始時または再開時に必ずspec_versionを確認する。

---

# 25. 並行作業時のルール

Claude CodeとAntigravityは並行作業してよい。

ただし、仕様変更が入った場合は一度作業を停止し、最新spec_versionを確認する。

古いspec_versionのまま作業を継続しない。

---

# 26. 生徒向けWEB教材の基本構造

教材ページは原則として以下の順序とする。

```text
タイトル
完成イメージ
この作品でできること
今日使う技
必要素材
素材ダウンロード
STEP 1
STEP 2
STEP 3
...
完成！
チャレンジ
オリジナル改造
先生チェック
```

---

# 27. 学習順序とWEB表示の役割分担

教材として、

**何を・どの順番で学ぶか**

はlesson-spec.mdで決定する。

Antigravityは学習順序を独自変更しない。

ただし、

**どのように見せれば子どもが理解しやすいか**

はAntigravityが設計してよい。

---

# 28. STEP分割

Antigravityはlesson-spec上の1STEPを、WEB上で複数カード・複数画面へ分割してよい。

例：

```text
STEP 3 重力ジャンプ
```

を、

```text
3-1 ジャンプしよう
3-2 下に落ちるようにしよう
3-3 地面で止めよう
```

として表示してよい。

教材上はSTEP 3のままとする。

---

# 29. step_split_plan

Antigravityは必要に応じて、

**STEP分割計画**

をtask/reportに記録する。

例：

```text
STEP 3
↓
WEB 3-1
WEB 3-2
WEB 3-3
```

学習順序自体は変更しない。

---

# 30. STEPページのルール

原則として、

**1画面 / 1カード = 1つの主要アクション**

とする。

複数の重要操作を一度に指示しない。

各画面には最低限、

* 今からすること
* 使うブロック
* 組み方
* 動作確認
* できた確認

を含める。

---

# 31. WEB教材の標準利用環境

授業では、

**ScratchとWEB教材をPC上で同時表示する**

利用方法を標準とする。

想定例：

```text
左：Scratch
右：WEB教材
```

または左右逆。

WEB教材は狭いウィンドウでも利用可能にする。

---

# 32. 半画面表示

PCではWEB教材が、

**約380px〜450px程度の横幅**

でも主要操作が可能であることを目標とする。

最低限、

* 横スクロールが不要
* STEPタイトルが読める
* Scratchブロックを確認できる
* 前へ / 次へ操作ができる
* ダウンロード操作ができる

こと。

---

# 33. Split Screen View Check

AntigravityのREPORTおよびチャッピーのREVIEWでは、

**PC半画面表示確認**

を必須項目とする。

目安：

```text
約400px幅
```

で教材が実用可能か確認する。

---

# 34. ナビゲーション

生徒が迷子にならないことを最優先する。

最低限、

* 前のSTEP
* 次のSTEP
* 教材トップ
* 現在地表示

を用意する。

必要に応じて固定ナビゲーションを使用する。

---

# 35. 長い縦スクロールを避ける

1つのSTEPが極端に長い縦スクロールにならないようにする。

必要に応じて、

* カード
* アコーディオン
* スライド形式
* STEP内分割

を利用する。

---

# 36. 低学年向け文章

生徒向け文章は、

* 短い
* 分かりやすい
* 具体的
* 1文を短くする
* 専門用語を多用しない
* 次に何をすればよいか明確

ことを基本とする。

---

# 37. 漢字・ルビ

低学年向け教材では、難しい漢字を多用しない。

重要語や読みづらい漢字には、

`<ruby>`

等によるルビ表示を検討する。

すべての漢字へのルビ付与を必須とはしない。

将来的に、

**やさしい表示モード**

等の導入を検討してよい。

---

# 38. ボタンサイズ

低学年およびタッチ操作を考慮し、主要な操作ボタンは十分な大きさを確保する。

目安：

**44〜48px以上**

を推奨する。

---

# 39. 達成フィードバック

各STEPには、

**「できた！」**

などの達成確認を表示してよい。

達成感を演出することは歓迎する。

ただし、

* 過剰なアニメーション
* 大きな音
* 毎回長時間続く演出

は避ける。

演出は控えめにし、必要に応じてON/OFFできる構造を検討する。

---

# 40. Scratchブロック表示

Scratchブロックは、

**scratchblocks等を利用したSVG描画**

を第一候補とする。

目的：

* 量産性
* 修正容易性
* Scratchに近い見た目
* テキストベース管理
* Git差分管理

---

# 41. scratchblocks方針

scratchblocksを採用する場合、

* 日本語表示
* Scratch 3.0互換表示
* 狭い画面での表示
* SVGサイズ
* 数値や変数の強調表示

をSC001で検証する。

必要に応じて、補足用画像やHTML注釈を併用する。

---

# 42. Scratchカテゴリカラー

WEB側でScratchカテゴリを補助表示する場合は、Scratch本体の色との混同を避けるため、できる限りScratch標準カラーに準拠する。

ただし、公式カラーコードの扱いは実装時に確認し、独自に似た色を乱用しない。

---

# 43. Scratch画面位置ガイド

低学年向けには必要に応じて、

* ブロックパレット
* コードエリア
* スプライト一覧
* ステージ

などScratch画面の位置を示す簡易ガイドを用意してよい。

---

# 44. 動画について

Scratch教材では、動画を基本教材として使用しない。

生徒自身のペースで、

* 読む
* 見る
* 作る
* 戻る
* 修正する

ことを重視する。

必要な説明はWEBページ内で完結させる。

---

# 45. Scratchファイル管理

Scratchの`.sb3`はZIP形式のバイナリであり、Git上で差分確認しにくい。

そのため、将来的には、

```text
project.json + assets
↓
ビルド
↓
.sb3
```

の運用を目標とする。

---

# 46. Scratch source / dist

Scratch関連ファイルは、

```text
scratch/source/
scratch/dist/
```

に分ける。

## source

編集・差分管理に使用するデータ。

例：

```text
project.json
svg
png
wav
mp3
```

## dist

生徒・講師が実際に利用する配布成果物。

例：

```text
SC001_start.sb3
SC001_complete.sb3
```

---

# 47. SB3のGit管理

SC001パイロットでは、運用方法を検証するため、開始用・完成用SB3をdistに保存してよい。

リポジトリ肥大化が確認された場合は、

* Git LFS
* GitHub Releases
* ビルド成果物としてのみ保持

などへ変更を検討する。

---

# 48. 開始用 / 完成用Scratch作品

原則として、

```text
SC001_start.sb3
SC001_complete.sb3
```

の2種類を用意する。

SC001では手動制作を許可する。

SC001の運用結果を確認後、自動化方式を判断する。

---

# 49. WEBデータと共通コンポーネント

教材ごとにHTMLを完全手書きで複製する方式は避ける。

将来的には、

```text
lesson-spec.md
lesson-manifest.json
↓
共通WEBコンポーネント
↓
教材ページ
```

という構成を目標とする。

---

# 50. Scratch Design System for Web

WEB教材全体で共通利用するデザイン・UI基盤を、

**Scratch Design System for Web**

として管理してよい。

略称：

`SDSW`

---

# 51. SDSWの初期対象

SC001制作前に、必要最低限として以下を検討する。

1. `scratch-theme.css`
2. STEPカード
3. ナビゲーション
4. ダウンロードカード

scratchblocks表示部品は技術検証後に追加する。

達成モーダル等の演出部品は必要になった段階で追加する。

---

# 52. SDSWの作り込み禁止

SC001制作前にデザインシステムを過剰に作り込まない。

目的は、

**教材を作りやすくすること**

であり、

**デザインシステムそのものを完成させること**

ではない。

SC001で実際に必要となった部品から共通化する。

---

# 53. WEBアセット配置

教材固有のWEB用素材は、原則として教材ID単位で管理する。

例：

```text
/scratch/assets/SC001/
```

またはリポジトリ内では、

```text
02_lessons/SC001/web/assets/
```

等を利用する。

最終的な公開ディレクトリ構成は、サーバー構成確認後に固定する。

---

# 54. URL・パス規則

公開先が、

```text
https://school.kidsbughunter.com/scratch/
```

配下であることを前提とする。

ルート直下へ依存した固定パスを乱用しない。

ビルド・配布先変更にも対応しやすい、

* 相対パス
* base URL設定

を利用する。

---

# 55. 既存サイトとのCSS衝突防止

Scratch教材のCSSは、既存サイトへ影響しないようにする。

必要に応じて、

```text
.scratch-curriculum-app
```

等のルートnamespaceを利用する。

グローバルなHTML要素へ強いCSS指定を行わない。

---

# 56. JavaScriptの衝突防止

既存サイトへ影響しないよう、

* グローバル変数乱用禁止
* 名前空間利用
* ES Modules等の利用
* 共通ライブラリの二重読み込み回避

を意識する。

---

# 57. 公開先

Scratch教材の最終公開先は、原則として以下を想定する。

```text
https://school.kidsbughunter.com/scratch/
```

GitHubは制作・管理場所とし、公開WEBサイトとは分離して考える。

---

# 58. 端末対応方針

## PC

メイン制作環境。

ScratchとWEB教材を同時表示できることを重視する。

## タブレット

完全閲覧対応を目標とする。

タッチ操作に配慮する。

PCの横に置いて教材を見る用途も想定する。

## スマートフォン

教材閲覧、復習、保護者・講師確認を主用途とする。

スマートフォン単体でScratch制作まで完結することは必須条件としない。

---

# 59. 素材ライセンス管理

素材は、

```text
07_assets/ASSET_LICENSES.md
```

で管理する。

最低限、以下を記録する。

```text
asset_id
ファイル名
用途
制作方法
作者
出典
ライセンス
利用可能範囲
使用教材
```

AI生成素材の場合は、

```text
制作方法：AI生成
```

と記載する。

---

# 60. 有名作品を参考にする場合

ゲームの仕組みやジャンルを参考にすることはできる。

ただし、

* キャラクター
* ロゴ
* 音楽
* 画像
* 名称
* 固有素材

をそのまま流用しない。

教材独自の題材・素材へ置き換える。

---

# 61. オリジナル化

可能な教材では必ず、

**オリジナル改造**

を用意する。

例：

* キャラクター変更
* 背景変更
* スピード変更
* 敵追加
* 新ルール追加
* ステージ追加
* 得点ルール変更

---

# 62. スタンプ

スタンプは単なる作品完成記録としない。

最低限、

```text
作品完成
基礎習得
ギミック習得
検定
```

を区別する。

---

# 63. 講師チェック

生徒がSTEPを実施したかどうかは講師が確認する。

WEB上でスタンプ・チェックを記録できる仕組みを目標とする。

講師が見るべきものは、

* 完成したか
* 自分で操作できるか
* 何をしているブロックか説明できるか
* 改造できるか

とする。

---

# 64. 検定

カリキュラム途中にiTeenオリジナル検定を配置する。

例：

```text
Bronze
Silver
Gold
Master
```

検定は暗記問題だけにしない。

* プログラムを読む
* 間違いを探す
* 修正する
* 指定された動きを追加する
* 条件通り作品を完成させる

といった実践問題を中心とする。

---

# 65. 外部検定との関係

カリキュラムは、

* プログラミング能力検定
* ジュニア・プログラミング検定

で必要になる基礎能力も身につく構造を目指す。

ただし、外部検定専用教材にはしない。

通常の作品制作を通じて自然に能力を身につける。

---

# 66. LEVEL設計

教材にはLEVELを設定する。

初期案：

```text
LEVEL 1
Scratch操作と基本

LEVEL 2
条件・繰り返し

LEVEL 3
変数・乱数・ゲーム要素

LEVEL 4
クローン・複合ギミック

LEVEL 5
高度なゲーム制作・設計
```

LEVELの詳細はCURRICULUM_MASTER.mdで管理する。

---

# 67. 検索

最終的なWEBでは最低限、以下の3方向から教材検索できることを目標とする。

## 基礎から探す

例：

```text
変数
条件分岐
座標
乱数
クローン
```

## 技から探す

例：

```text
ジャンプ
重力
弾
スクロール
円運動
```

## 作品から探す

例：

```text
シューティング
アクション
迷路
クレーンゲーム
```

---

# 68. マスターデータ

教材検索・進捗管理・検定管理に使用するデータは、

```text
01_master/
```

に集約する。

lesson-spec.mdと同じ情報を手動で重複管理しない。

可能な限り、

```text
lesson-spec.md
↓
自動抽出
↓
01_master/*.json
```

とする。

---

# 69. STATUS.md

プロジェクト全体の制作状況を管理する。

例：

```text
| ID | 作品 | 仕様 | Scratch | WEB | Review | 公開 |
|---|---|---|---|---|---|---|
| SC001 | クレーンゲーム | ✅ | ✅ | ✅ | ✅ | ✅ |
| SC002 | 迷路ゲーム | ✅ | 🔨 | 🔨 | - | - |
```

状態は以下を基本とする。

```text
-
未着手

🔨
作業中

✅
完了

⚠️
要修正
```

---

# 70. CHANGELOG.md

重要な仕様変更を記録する。

最低限、

```text
日付
対象
変更内容
変更理由
```

を記載する。

細かな文章修正はGit commit履歴で管理する。

---

# 71. 教材単位の変更履歴

教材単位の細かな変更履歴は、lesson-spec.mdのGit commit履歴を基本とする。

spec_versionを変更した場合は、commit messageで分かるようにする。

例：

```text
docs: update SC001 spec to v1.1
```

---

# 72. GitHub Issuesの用途

GitHub Issuesは正式な教材指示書として使用しない。

Issuesは以下に限定する。

* バグ
* 改善候補
* 将来対応
* 技術課題
* 検討事項

正式な教材仕様はlesson-spec.md。

正式な実装指示はtask.md。

正式な作業報告はreport.md。

とする。

---

# 73. Git運用

基本的に、

```text
main
```

は承認済み・安定状態とする。

制作・修正は可能な限り別ブランチで行う。

例：

```text
lesson/SC001
fix/SC001-jump
web/SC001
```

SC001パイロット期間は、運用負荷を見ながら簡略化してよい。

---

# 74. Commitルール

何を変更したか分かるメッセージにする。

例：

```text
feat: add SC001 lesson specification
feat: create SC001 Scratch project
feat: create SC001 web lesson
fix: correct SC001 collision logic
docs: update SC001 spec to v1.1
```

---

# 75. ファイルを勝手に削除しない

既存教材や素材を削除する場合は、他教材から参照されていないことを確認する。

不明な場合は削除せず、確認事項としてREPORTへ記載する。

---

# 76. LICENSE

Publicリポジトリとして運用するため、教材・プログラム・素材の利用条件を別途決定する。

LICENSE未決定の間は、第三者が自由に再利用できることを前提としない。

素材ごとの条件はASSET_LICENSES.mdを優先する。

---

# 77. CI / 自動チェック

将来的にGitHub Actions等で以下を自動確認する。

* YAML frontmatter構文
* spec_version有無
* lesson_id重複
* basics / gimmicks ID存在確認
* JSON構文
* project.json構文
* lesson-manifest.json構文
* lesson-specとmanifestの整合
* WEB上の表記整合
* リンク切れ
* 必須ファイル有無
* STATUS生成

SC001では必須としない。

---

# 78. レビュー

教材完成後、チャッピーがレビューする。

最低限以下を確認する。

## Scratch

* 正常に動作するか
* lesson-specと一致しているか
* spec_versionが一致しているか
* lesson-manifest.jsonと一致しているか
* 不要な複雑化がないか
* 子どもが理解できる構造か

## WEB

* Scratch完成作品と説明が一致しているか
* STEP通りに作れば完成するか
* Scratch表記と完全一致しているか
* 説明不足がないか
* 説明過多になっていないか
* 読みやすいか
* 子どもが楽しめるか
* 半画面表示で使えるか
* スマホ・タブレット・PCで利用できるか

## カリキュラム

* 既存教材との重複
* 基礎スキルの不足
* ギミックの偏り
* LEVELの妥当性
* 検定とのつながり

---

# 79. Reviewerの最重要視点

レビューでは、

**「実際の授業で子どもが使えるか」**

を最優先する。

技術的に正しいだけでは合格としない。

次の視点を重視する。

```text
読めるか
迷わないか
楽しいか
完成できるか
達成感があるか
もっとやりたいと思えるか
```

---

# 80. SC001パイロット前のWEB準備

SC001に入る前に、Antigravity側で以下の最低限の共通部品を検討する。

* scratch-theme.css
* STEPカード
* ナビゲーション
* ダウンロードカード

必要以上に作り込まない。

SC001に必要な範囲で作成する。

---

# 81. SC001パイロットで検証するもの

SC001では以下を検証する。

* lesson-spec YAML運用
* spec_version運用
* lesson-manifest.json
* Claude Code / Antigravity連携
* source / dist構成
* SB3管理方法
* 開始用 / 完成用制作方法
* scratchblocks表示
* 半画面400px前後表示
* STEP分割
* WEB共通コンポーネント
* REPORT / REVIEW運用
* 素材ライセンス管理
* Scratch / WEB表記一致

---

# 82. SC001後の見直し

SC001完成後、実際の制作工程・可能であれば授業利用結果をもとに、

* PROJECT_RULES
* lesson-template
* task-template
* report-template
* review-template
* SDSW

を見直す。

SC001で作った仕組みを、そのまま無条件で大量展開しない。

---

# 83. プロジェクト成功のための最重要ルール

## Rule 1

**lesson-spec.mdを教材仕様の正本とする。**

## Rule 2

**lesson-manifest.jsonをScratch実装事実の基準データとする。**

## Rule 3

**チャットだけで仕様を確定しない。**

## Rule 4

**すべての実装はspec_versionを確認する。**

## Rule 5

**Scratch側とWEB側の名称・内容を一致させる。**

## Rule 6

**教材内容とWEB表示を分離して考える。**

## Rule 7

**学習順はlesson-spec、見せ方はAntigravityが担当する。**

## Rule 8

**変更は必ず仕様書へ戻す。**

## Rule 9

**技術的な問題は完成後ではなく着手前にエスカレーションする。**

## Rule 10

**PC半画面でも子どもが使えるWEBを目指す。**

## Rule 11

**子ども目線で最終レビューする。**

## Rule 12

**素材の権利情報を記録する。**

## Rule 13

**共通化は行うが、共通基盤を作り込みすぎない。**

## Rule 14

**作ること自体を目的にせず、学習体系全体とのつながりを確認する。**

---

# 84. プロジェクトの基本思想

このプロジェクトでは、

「Scratchで作品をたくさん作った」

だけではなく、

**何を学んだか**
**どんな技が使えるようになったか**
**次に何へ挑戦できるか**

が分かるカリキュラムを作る。

生徒にとっては、

**楽しい作品制作。**

講師にとっては、

**進捗が分かる教材。**

保護者にとっては、

**何を学んでいるか説明できるカリキュラム。**

運営側にとっては、

**継続的に追加・改善できる教材基盤。**

制作チームにとっては、

**誰が制作しても同じ品質基準で継続できる仕組み。**

そしてWEB教材としては、

**子どもが先生の説明を待たなくても、見て・作って・動かして・完成まで進める学習環境。**

これをScratch教材プロジェクトの最終目標とする。
