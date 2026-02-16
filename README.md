# Jam Kuradoberi (M.U.G.E.N Character)

## Character Introduction

**Character Name:** Jam Kuradoberi (ジャム・クラドベリ)  
**Display Name:** Jam  
**Original Source:** Guilty Gear series (Arc System Works)  
**M.U.G.E.N Author:** AOAO  
**Version Date:** April 14, 2001  
**MUGEN Version:** 1.0  

---

## Character Storyline (Guilty Gear Lore)

Jam Kuradoberi is a martial artist and chef who runs a Chinese restaurant called "Yen" in the Guilty Gear universe. She is known for her energetic personality, love of fighting, and exceptional kung fu skills. Jam uses a fighting style based on Chinese martial arts combined with ki manipulation, featuring powerful kicks and acrobatic techniques.

**Key Story Elements:**
- She seeks to become the strongest martial artist and often challenges other fighters
- Her fighting style incorporates "Tension" (ki) energy, similar to the game's mechanics
- She has a rivalry with other martial artists and enjoys testing her skills in combat
- Her special moves are named after Chinese martial arts techniques and mythological creatures (e.g., Phoenix, Dragon God)

---

## File Structure & Index

| File | Purpose |
|------|---------|
| [jam.def](jam.def) | Character definition, palette references, file paths |
| [jam.cmd](jam.cmd) | Command/input definitions, state triggers |
| [jam.air](jam.air) | Animation definitions |
| [Constant.cns](Constant.cns) | Core constants, win poses, intro/outro states |
| [Jam.cns](Jam.cns) | Main character logic (includes Constant.cns) |
| [common1.cns](common1.cns) | Common states (stand, crouch, jump, hit, etc.) |
| [State-2.cns](State-2.cns) | State controller (st2) |
| [State-3.cns](State-3.cns) | State controller (st3) |
| [AttackNormal.cns](AttackNormal.cns) | Normal attack states |
| [AttackSpecial.cns](AttackSpecial.cns) | Special move states |
| [AttackEX.cns](AttackEX.cns) | EX/Overdrive special moves |
| [Attackhyper.cns](Attackhyper.cns) | Hyper/Super move states |
| [hyper.cns](hyper.cns) | Super move: Choukyaku Houou Shou (兆脚鳳凰昇) |
| [Effect.cns](Effect.cns) | Visual/audio effects |
| [Extra.cns](Extra.cns) | Extra mechanics |
| [GUARD.cns](GUARD.cns) | Guard/block states |
| [helpers.cns](helpers.cns) | Helper/projectile definitions |

### Related Documentation

| Document | Description |
|----------|-------------|
| [README.md](README.md) | This file – main character documentation |
| [docs/TRANSLATION_TABLE.md](docs/TRANSLATION_TABLE.md) | Japanese→English translation for CNS/CMD comments |
| [CHANGELOG.md](CHANGELOG.md) | Version history and modifications |
| [docs/INDEX.md](docs/INDEX.md) | Documentation index and planned docs |

---

## System Architecture Analysis

### 1. Fight Mode Architecture

#### State Type Classification
- **S (Stand)**: Ground standing states (0, 100, 195, 196, etc.)
- **C (Crouch)**: Crouching states (11, 400–444)
- **A (Air)**: Aerial states (40, 45, 600–640)
- **L (Liedown)**: Knockdown/ground states (5100, 5110, etc.)

#### Movement States
| StateNo | Name | Description |
|---------|------|-------------|
| 0 | Stand | Idle standing |
| 10–11 | Crouch | Crouch transition & hold |
| 100 | Run Forward | Ground dash forward |
| 105 | Run Backward | Ground dash backward |
| 2005–2006 | Air Run | Aerial dash forward/backward |
| 991–994 | Evasion | Dodge, roll forward, roll back, power charge |

#### Var(43) – Mode Flags
- **0**: Normal mode (標準)
- **5**: Super/Arcade mode (スーパー・何でもアリモード)
- **10**: EX mode (ＥＸ・何でもアリモード)
- **15**: Both EX + Super mode

### 2. Skill System Architecture

#### Special Moves (Command → StateNo)

| Command Name | Input | StateNo | Description |
|--------------|-------|---------|-------------|
| **baku** | D,DF,F + P | 1000 | Choukyaku (兆脚) – Forward dash kick |
| **baku ashi** | B,D,DB + K | 1040 | Choukyaku Kick – Back step kick |
| **baku 100** | D,DF,F + Z | 1131 | Choukyaku 100% – Full power version |
| **baku 1000** | D,DF,F + B | 1130 | Choukyaku 1000% – Heavy version |
| **baku mawa** | D,DB,B + X | 1010 | Choukyaku Spin – Spinning kick |
| **hochifu** | D,DB,B + P | 1020 | Houchifu (鳳翼) – Back step |
| **fumifumi** | /D + A | 1030 | Fumifumi (踏み踏み) – Stomp |
| **kenrou** | F,D,DF + P | 1050–1067 | Kenrou (堅牢) – Wall/defensive stance |
| **geki** | D,DB,B + P | 1070–1082 | Geki (撃) – Reverse strike |
| **ryujin** | D,DF,F + P | 1090–1096 | Ryujin (龍神) – Dragon God strike |
| **asanagi K/S/HS** | D,D + P | 1100–1110 | Asanagi – Quick down attacks |
| **banri** | D,DF,F + X/Y | 6550 | Banri Shoumei (万里証明) – Long-range palm |
| **atatatata** | F,D,DF + P | 6500 | Kung Fu Rush – Rapid punches |
| **dasuto** | C+Z | 2700 | Dust Attack – Launcher |
| **412p/412k** | B,DB,D + P/K | — | Quarter-circle back attacks |

#### Super Moves (Hyper)

| Command Name | Input | StateNo | Power Cost | Description |
|--------------|-------|---------|------------|-------------|
| **houou** | F,DF,D,DB,B,F + P | 3000–3031 | 2000 | Choukyaku Houou Shou (兆脚鳳凰昇) – Phoenix super |
| **jou** | F,DF,D,DB,B,F + K | 3100 | 1000 | Jou (浄) – Purification super |
| **gasen** | D,DF,F,D,DF,F + 2 buttons | 3300 | 3000 | Gasen (雅閃) – Elegant flash |
| **musume** | D,DF,F,D,DF,F + X+Y | 6000 | 3000 | Musume (娘) – Daughter technique (commented out) |

#### Roman Cancel (RC)
- **rc** (a+b+x, a+b+y, etc.): State 2030/2031 – Cancels current move into neutral, costs 1000 power

#### Dead Angle Attack (DAA)
- **fwd_xa** (F + C+Z): State 2040 – Counter during block, costs 1000 power

### 3. Animation & State Counterpart Mapping

#### Normal Attacks → State Numbers

| Attack | Standing | Crouching | Jumping |
|--------|----------|-----------|----------|
| Light Punch (P) | 200, 260 | 400 | 600 |
| Strong Punch (K) | 210, 250 | 410 | 610 |
| Light Kick | 230–232 | 430 | 630 |
| Strong Kick | 240–242, 270 | 440–444, 450 | 640 |

#### Chain Combo (MoveContact) Logic
- **var(3)**: Roman Cancel flag (RC可否)
- **movecontact = 1**: Enables cancel into next move during hit
- Chain rules: LP→MP→HP, LK→MK→HK, with RC allowing special cancels

#### Statedef Ranges by Category
- **200–272**: Standing normals
- **400–450**: Crouching normals
- **600–640**: Jump normals
- **1000–1131**: Choukyaku (Baku) specials
- **1020–1025**: Houchifu, Asanagi
- **1030–1033**: Fumifumi
- **1050–1096**: Kenrou, Geki, Ryujin
- **1100–1110**: Asanagi K/S/HS
- **2000–2062**: Throws, DAA, RC, intro
- **2700**: Dust Attack
- **3000–3108**: Hyper moves (Houou, Jou, Gasen)
- **3300–3310**: Gasen super
- **6500, 6550**: EX-mode Kung Fu Rush, Banri

### 4. Variable (Var) Reference

| Var | Purpose (from Jam.cns comments) |
|-----|----------------------------------|
| 0–2 | General/temp |
| 3 | Roman Cancel availability |
| 4 | — |
| 5 | Combo hit count (for RC) |
| 6 | Cancel chain from hit |
| 8 | Double jump (0=unused, 1=available, 2=used) |
| 10 | Air run count |
| 13 | High jump flag |
| 20 | Ryujin/Geki/Kenrou air run cancel |
| 21 | Chain hit count (max 3 for RC) |
| 22 | Asanagi Ryujin stock |
| 23 | Asanagi Geki stock |
| 24 | Asanagi Kenrou stock |
| 25 | Jou / Houou hit count |
| 31 | Win pose camera |
| 35 | Force Roman Cancel var |
| 43 | Mode (0=Normal, 5=Super, 10=EX, 15=Both) |
| 45 | Dust Attack jump cancel |
| 50 | Force Roman Cancel block |

---

## Japanese Translation Table

*CNS and CMD files contain Shift-JIS encoded Japanese comments. Below is a translation reference.*

### Command Names (jam.cmd)

| Japanese (Codex) | Romaji | English |
|------------------|--------|---------|
| 兆脚鳳凰昇 | Choukyaku Houou Shou | Phoenix Rising (Super) |
| 浄 | Jou | Purification (Super) |
| 雅閃 | Gasen | Elegant Flash (Super) |
| 恋崩嬢 | Musume | Daughter (Super, unused) |
| 兆脚 | Baku | Forward dash |
| 鳳翼 | Houchifu | Phoenix Wing (back step) |
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
| 羅刹 | — | — |
| 準備 | Junbi | Ready/Preparation |
| ダスト | Dasuto | Dust |
| RC | Roman Cancel | Roman Cancel |
| フォース | Force | Force |
| ハイジャンプ | High Jump | High Jump |

### State Comments (CNS)

| Japanese (Codex) | English |
|------------------|--------|
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
| カウント | Count |
| 可否 | Availability |
| 連続 | Chain/Combo |
| 発生 | Startup |
| 持続 | Active |
| 硬直 | Recovery |
| 画面 | Screen |
| 演出 | Effect |
| 勝ち | Win |
| 負け | Lose |
| 導入 | Intro |
| 勝利 | Victory |

### Palette Comments (jam.def)

| Japanese (Codex) | English |
|------------------|--------|
| 赤 | Red |
| 緑 | Green |
| デフォ | Default |
| 青 | Blue |
| 紫 | Purple |
| カラー | Color |
| EXパレット | EX Palette |
| ビギナーズ | Beginners |
| 大会用 | Tournament |
| 選抜 | Selection |
| 隠し | Hidden |
| 対戦で見たカラー | Color seen in versus |

---

## Changelog & History

### Version Tracking

| Date | Version | Author | Notes |
|------|---------|--------|-------|
| 2001-04-14 | 1.0 | AOAO | Initial release (from jam.def) |

*Note: Git history is not available in this repository. For detailed change history, run `git log` in the project root if the character is part of a versioned repository.*

### Files Modified by Original Creator

Based on file headers and structure, the following files were authored by **AOAO**:

- `jam.def` – Character definition
- `jam.cmd` – Command set
- `jam.air` – Animations
- `Constant.cns` – Constants, win/lose, intro
- `Jam.cns` – Main CNS
- `common1.cns` – Common states (possibly derived from kfm)
- `AttackNormal.cns`, `AttackSpecial.cns`, `AttackEX.cns`, `Attackhyper.cns`
- `hyper.cns` – Houou super
- `State-2.cns`, `State-3.cns`
- `Effect.cns`, `Extra.cns`, `GUARD.cns`, `helpers.cns`

---

## Quick Reference: Button Layout

| Button | Punch | Kick |
|--------|-------|------|
| X / a | Light | Light |
| Y / b | Medium | Medium |
| Z / c | Heavy | Heavy |

- **Recovery**: X+A, Y+B, X+Y, A+B
- **Roman Cancel**: A+B+X, A+B+Y, A+X+Y, B+X+Y
- **Dust**: C+Z

---

## Related Documentation Files

- [docs/TRANSLATION_TABLE.md](docs/TRANSLATION_TABLE.md) – Full Japanese→English glossary
- [CHANGELOG.md](CHANGELOG.md) – Version history
- [docs/](docs/) – Additional technical notes (if created)
