# Decision Modelは判断を控えられるか

判断に特化したAI（Decision Model）7つを、AIパートナー／キャラクターAIで必要になる4種類の判断タスクで評価した技術レポートです。前回の報告「[AIパートナーの判断層としてDecision Modelは使えるか](https://github.com/whitelabel1940/jev-ai-partner-decision-eval)」と同じholdout（260問）・同じ採点で比較しています。

評価したモデルは次の7つです。

- Jev 1.13.0（TypeSafe AI）
- OpenAI Decisions（`gpt-6-luna`）
- Cloudflare Clef 27B
- Clef-Flash 9B
- StartLux-Decision 4B（Q8_0）
- StartLux-Decision 2B（Q8_0）
- Liquid AI d1-3B（Q8_0）

- **本文（技術版）**：[index.html](index.html)（GitHub Pages: https://whitelabel1940.github.io/decision-model-comparison-v1/ ）
- **一般向けの解説記事（note）**：公開後にリンクを追記します

## 概要

- 総合の完全正解数は、Jev 166、Clef 27B 163、OpenAI Decisions 160（/260）。上位3つの差の95%区間はいずれも0を跨ぎ、順位は主張できない。
- 最上位はテストごとに入れ替わった。対象の特定と表現チェックはJev、根拠チェックはOpenAI、記憶の使いどころはClef 27B。
- 最も大きな差は、判断を控えるべき場面の扱いに出た。記憶の本文が空で正解が「材料不足」になる39問では、正解数が39から0まで分かれた。
- 同じシリーズを小さい版に替えると（Clef 27B→9B、StartLux 4B→2B）、判断を控える指標の多くが全体の正答率より大きく低下し、答えを言い切る方向の出力が増えた。2シリーズでの観測であり、一般法則とはしない。
- 確率の質（ECE）の順位は正答率の順位と一致しなかった。小数2桁で確率を返すモデルでは、対数損失が+∞になる。
- 前回の汎用LLM 4モデル（180〜194/260）には、今回のどのモデルも届かなかった。前回の実務的な結論は変わらない。

詳細、事前登録した仮説と判定、限界は本文を参照してください。

## このリポジトリに含まれないもの

- holdoutの問題・正解（Gold）・実行ログは公開していません。将来、別のDecision Modelを同じ条件で比較するときに再利用するためです。問題と正解は、正当な再現目的の要請に応えられる形で保持しています。
- 本文中の例は、すべて説明用に作った架空例です。
- StartLux-Decision は CC BY-NC 4.0 のモデルで、本評価は非商用の研究として行いました。

## 改訂履歴

改訂の履歴はこのリポジトリのコミット履歴で確認できます。誤りの指摘はIssueで受け付けています。

## ライセンス

本文と図は [CC BY 4.0](LICENSE) で公開しています。出典（著者名とこのリポジトリのURL）を明記すれば、改変・再配布できます。評価したモデルそれぞれのライセンスは、本文の表5を参照してください。

## 引用

```
whitelabel1940. Decision Modelは判断を控えられるか：7つのDecision Modelによるholdout-exp-2横断評価. 2026.
https://github.com/whitelabel1940/decision-model-comparison-v1
```
