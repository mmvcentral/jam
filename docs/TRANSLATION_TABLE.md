# Japanese Translation Table

Translation reference for Japanese comments in CNS and CMD files (Shift-JIS encoding).

## Command Names (jam.cmd)

| Japanese | Romaji | English |
|----------|--------|---------|
| 兆脚鳳凰昇 | Choukyaku Houou Shou | Phoenix Rising Super |
| 浄 | Jou | Purification Super |
| 雅閃 | Gasen | Elegant Flash Super |
| 恋崩嬢 | Musume | Daughter (unused) |
| 兆脚 | Baku | Forward dash |
| 鳳翼 | Houchifu | Phoenix Wing |
| 踏み踏み | Fumifumi | Stomp |
| 堅牢 | Kenrou | Solid Wall |
| 撃 | Geki | Strike |
| 龍神 | Ryujin | Dragon God |
| 拳の構え | Asanagi | Fist stance |
| 万里証明 | Banri Shoumei | Ten Thousand Miles Proof |
| 兆脚蹴り | Baku Ashi | Baku Kick |
| 兆脚100% | Baku 100 | Baku 100% |
| 兆脚1000% | Baku 1000 | Baku 1000% |
| 兆脚回り | Baku Mawa | Baku Spin |
| コマンド参照 | Command reference | — |
| 準備 | Junbi | Ready |
| ダスト | Dasuto | Dust |
| ハイジャンプ | High Jump | High Jump |

## State Comments (CNS)

| Japanese | English |
|----------|---------|
| 立ち | Stand |
| しゃがみ | Crouch |
| ジャンプ | Jump |
| 攻撃 | Attack |
| 必殺 | Special |
| 超必殺 | Super/Hyper |
| 当たり | Hit |
| ガード | Guard |
| 投げ | Throw |
| 無敵 | Invincible |
| 覚醒 | Awakening |
| テンションゲージ | Tension gauge |
| 可否 | Availability |
| 連続 | Chain |
| 発生 | Startup |
| 持続 | Active |
| 硬直 | Recovery |
| 勝ち | Win |
| 負け | Lose |
| 導入 | Intro |
| 勝利 | Victory |

## Palette Comments (jam.def)

| Japanese | English |
|----------|---------|
| 赤 | Red |
| 緑 | Green |
| デフォ | Default |
| 青 | Blue |
| 紫 | Purple |
| EXパレット | EX Palette |
| ビギナーズ | Beginners |
| 大会用 | Tournament |
| 選抜 | Selection |
| 隠し | Hidden |
| 対戦で見たカラー | Color seen in versus |

## jam.def [Files] Section Comments

| Japanese | English |
|----------|---------|
| コマンド指定 | Command specification |
| お | Default |
| おり | Original 5 |
| デフォルト | Default |
| じ | Original 3 |
| る | 5 |
| コスプレ | Cosplay |
| ＸＥ版 | EX version |
| バリエーションの一つめ | First variation |
| 投票選出 | Voted/selected palette |
| 色選専用 | Color selection exclusive |
| 組替 | Combination/rearranged |
| ギルのおかわり | Gill's second helping palette |
| 元のコスプレで作ったコスプレ | Cosplay made from original cosplay |

## Var/Purpose Comments

| Japanese | English |
|----------|---------|
| 標準 | Normal |
| 何でもアリモード | Anything-goes mode |
| ＥＸ・何でもアリモード | EX Anything-goes mode |
| スーパー・何でもアリモード | Super Anything-goes mode |
| RC可否 | Roman Cancel availability |
| 連続ヒット | Chain hit |
| 子連れ回数 | Child-attack count |
| 拳の構え 龍神 | Asanagi Ryujin stock |
| 拳の構え 撃 | Asanagi Geki stock |
| 拳の構え 堅牢 | Asanagi Kenrou stock |
| 浄浄 1撃目〜9撃目 | Jou hit 1–9 |
| 覚醒準備 | Awakening prep |
| 恋崩嬢 | Musume |
| 前ダッシュ | Forward dash |
| 強制 | Force |
| フォース | Force |

## Attackhyper.cns (Chokyaku Hououshou / Phoenix Rising Super)

| Japanese | English |
|----------|---------|
| 兆脚鳳凰昇　開始 | Chokyaku Hououshou Start |
| ＥＸ・何でもアリモード | EX Anything-goes mode |
| ロマンキャンセル解除ガトリング暴発防止 | Roman Cancel release – prevent Gatling runaway |
| 兆脚鳳凰昇　最初の一撃 | Chokyaku Hououshou first hit |
| fall = 1;落下させる | fall = 1; knock down |
| fall.recover = 0;受身可否 | fall.recover = 0; tech roll availability |
| fall.recovertime = 30;受身出来るまでの時間 | fall.recovertime = 30; time until tech possible |
| ＨＩＴ炎エフェクトのヘルパー強制消去用 | For HIT flame effect helper force removal |
| ロマンキャンセル許可 | Roman Cancel permission |
| 兆脚鳳凰昇　立ちＳ近距離 | Chokyaku Hououshou standing S close |
| 兆脚鳳凰昇　立ちＫ | Chokyaku Hououshou standing K |
| 兆脚鳳凰昇　立ちＫ２撃目 | Chokyaku Hououshou standing K 2nd hit |
| 兆脚鳳凰昇　立ちＫ３撃目 | Chokyaku Hououshou standing K 3rd hit |
| 兆脚鳳凰昇　バックダッシュ１撃目 | Chokyaku Hououshou back dash 1st hit |
| 兆脚鳳凰昇　バックダッシュ２撃目 | Chokyaku Hououshou back dash 2nd hit |
| 兆脚鳳凰昇　バックダッシュ３撃目 | Chokyaku Hououshou back dash 3rd hit |
| 兆脚鳳凰昇　バックダッシュ４撃目 | Chokyaku Hououshou back dash 4th hit |
| 兆脚鳳凰昇　バックダッシュ５撃目 | Chokyaku Hououshou back dash 5th hit |
| 兆脚鳳凰昇　バックダッシュ６撃目 | Chokyaku Hououshou back dash 6th hit |
| 兆脚鳳凰昇　浮かし蹴り | Chokyaku Hououshou launcher kick |
| 兆脚鳳凰昇　浮かし蹴り着地 | Chokyaku Hououshou launcher kick landing |
| 兆脚鳳凰昇　上昇体当たり | Chokyaku Hououshou rising tackle |
| 兆脚鳳凰昇　体当たり終了下降 | Chokyaku Hououshou tackle end descent |
| 体当たり上昇相手側 | Rising tackle opponent side |
| 蹴り上げ相手側 | Kick-up opponent side |
| 鳳凰エフェクト | Phoenix effect |
| ＥＸ　兆脚鳳凰昇　移動攻撃 | EX Chokyaku Hououshou moving attack |
| 戀崩嬢 １撃目〜９撃目までのカウントとＥＸ 兆脚鳳凰昇回数カウント | Musume hit 1-9 count and EX Chokyaku Hououshou count |
| テンションゲージ減らし | Reduce tension gauge |
| 覚醒時間停止 | Awakening time stop |
| 覚醒開始光の斜め線　上方向 | Awakening start diagonal light lines upward |
| 覚醒開始光の斜め線　下方向 | Awakening start diagonal light lines downward |
| 覚醒開始 光の粒　上/下/前/後/右上/左上/右下/左下 | Awakening start light particles (direction) |
| 覚醒開始光のオーラ呼び出し | Awakening start aura call |
| コレが無いとヘルパーの色変化が出来ない | Required for helper color change |
| 覚醒開始　効果音 | Awakening start sound effect |
| 声 | Voice |
| 行くよ | Let's go |
| 行くあるよ | Here I come |
| 一点集中 | Focus |
| 通常・ゴールドモード | Normal / Gold mode |
| ピンクの煙 | Pink smoke |
| 相手が空中時のみ落下させる | Knock down only when opponent is airborne |
| 攻撃力補正用ＶＡＲ | Attack power correction VAR |
| カウンターヒット時 | On counter hit |
| ガードレベル増加 | Guard level increase |
| ガードレベル減少 | Guard level decrease |
| 必殺系ＨＩＴマーク | Special move HIT mark |
| 必殺系ガードマーク | Special move guard mark |
| ＨＩＴエフェクト　白いフラッシュ | HIT effect white flash |
| ＨＩＴ時 | On HIT |
| 兆脚ぅぅぅぅ | Chokyaku (voice) |
