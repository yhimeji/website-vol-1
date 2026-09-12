# 「次の一歩」スキル診断サイト｜index.html 引き継ぎメモ

このメモは、`index.html` をClaude Codeで修正する際に、これまでの検討経緯と仕様を伝えるためのものです。

---

## 1. 背景・目的

- 生成AI推進委員会 第1弾企画（静的Webサイト構築体験）の一環として、委員会メンバー自身が作成する見本サイト
- 目的：部内メンバーの作成意欲を高めること。あわせて、生成AIを日常から活用しAIリテラシーを高めること
- 提出期限：2026年9月17日(木)
- 動きのあるJavaScript、デザイン性の高いUI(アニメーション・複雑なレイアウト)を意識して作成

## 2. サイトコンセプト

**「ITエンジニアのスキル診断 → おすすめ資格レコメンド」**

- 体験の核：診断形式（技術・業務スキルを選ぶ → アニメーションでおすすめ資格を提示）
- デザインの方向性：ミニマル×グラデーション（洗練された印象）
  - 背景は淡いグレー(#f7f7fa)、アクセントはインディゴ→バイオレット→シアンの3色グラデーション
  - 見出し書体：Space Grotesk／本文書体：Inter
  - カードの左端にカテゴリ別グラデーションのアクセントバー（技術／証券／AML で色味を変える）

## 3. 画面構成（3ステップ）

1. **スキル選択画面**：技術スキル・業務スキルをチップ(ボタン)で複数選択
2. **診断中画面**：グラデーションのリングアニメーション＋切り替わるメッセージ（約1.5秒）
3. **結果画面**：選んだスキルに合致する資格をカードでスタッガー表示（アニメーション遅延つき）。「スキルを選び直す」で画面1に戻る

## 4. 対象スキル一覧

**技術スキル**：Oracle／SQL Server／GitHub・Copilot／JAVA／C#／React／JavaScript／Node.js
**業務スキル**：証券／AML(マネロン対策)

## 5. 確定済みの資格リスト（全21件）

### 技術スキル紐づけ
| 資格 | 紐づくスキル |
|---|---|
| ORACLE MASTER Bronze / Silver / Gold DBA、Silver SQL | Oracle |
| DP-900(Azure Data Fundamentals)、DP-300(Azure Database Administrator Associate) | SQL Server |
| GH-900(GitHub Foundations)、GH-300(GitHub Copilot Certification) | GitHub |
| Oracle Certified Java Programmer, Silver SE / Gold SE | JAVA |
| AZ-204(Azure Developer Associate) | C# |
| JSNAD(OpenJS Node.js Application Developer) | Node.js／JavaScript |
| Meta Front-End Developer Professional Certificate | React／JavaScript |

### 業務スキル紐づけ
| 資格 | 紐づくスキル |
|---|---|
| 証券外務員一種／二種、フィナンシャル・プランナー(FP)、証券アナリスト(CMA) | 証券 |
| AML/CFTスタンダードコース、AML/CFTオフィサー、AML/CFTオーディター、CAMS(公認AMLスペシャリスト) | AML |

各資格に「受験料」「受験方法」「難易度(5段階)」「学習時間の目安」「市場価値(説明＋5段階)」の情報を持たせている。

## 6. 既知の注意点・要フォロー事項

- **受験料の一部は未確認・変動あり**：コード内で `要確認` `目安` と明記している箇所は、公開前に最新の公式情報での確認・修正が必要
- 資格の追加・入れ替えを行う場合は、`CERTS` 配列（資格データ）と `SKILLS` 配列（選択肢）の両方に対応が必要
- モーション(アニメーション)は `prefers-reduced-motion` に対応済み。動きを追加する場合もこの配慮を維持すること

## 7. ファイル構成

- `index.html` 1ファイルにHTML／CSS／JavaScriptをすべて内包（外部ファイル依存なし。Google Fontsのみ外部CDN読み込み）
- 主なJS構造：`SKILLS`(選択肢データ)／`CERTS`(資格データ)／画面遷移用の`showScreen()`／結果描画用の`renderResults()`・`buildCard()`

---

このメモと `index.html` をあわせてClaude Codeに渡すことで、これまでの検討経緯・デザイン意図・データ構造を踏まえた修正依頼が可能になります。
