---
title: "競馬予測AI"
emoji: "🐴"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["python", "ai"]
published: false
---

## Input data

### data source

- [netkeiba](https://db.netkeiba.com/)

### 前処理後の特徴量一覧

説明変数:

| Physical            | Logical     | Note                  |
|---------------------|-------------|-----------------------|
| horse_id            | 馬ID         |
| jockey_id           | 騎手ID        |
| trainer_id          | 調教師ID       |
| entry_number        | 馬番          |
| entry_group_number  | 枠番          |
| win_odds            | 単勝odds      |
| popularity          | 人気          |
| total_weight        | 斤量          | ジョッキーの体重や鞍などを含めた重量のこと |
| sex                 | 性別          |
| age                 | 馬齢          |
| weight              | 馬体重         |
| weight_diff         | 馬体重差        |
| ground_type         | 地面の種類       | 芝やダート                 |
| ground_state        | 地面の状態       |
| rank_last_{n}races  | 直近{n}レースの順位 | n = 3, 5, 10, 1000    |
| prize_last_{n}races | 直近{n}レースの賞金 | n = 3, 5, 10, 1000    |
| race_class          | レースのクラス     | 2歳新馬 等                |
| weather             | 天候          |
| circuit_direction   | コースの方向      | 右回りや左回り               |
| circuit_distance    | コースの距離      |
| place               | 開催場所        | 

目的変数: first_rank_flag
