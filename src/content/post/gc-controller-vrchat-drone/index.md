---
title: "GCコントローラーでVRChat上のドローンを操作するまで"
description: "GCコンをXinput化してVRChatのドローンを動かすまでのセットアップ手順"
publishDate: "2026-03-22"
updatedDate: "2026-03-22T00:00:00+09:00"
tags: ["vrchat"]
draft: false
---

GCコントローラーをXinput化することで、VRChat上のドローンをGCコンで操作できるようにするまでの手順。
GCコントローラーをVRChat以外のSteamゲームという場合においてもセットアップ手順の4.までは共通。
Windows11での動作を確認。

## 必要なもの

- ゲームキューブコントローラー
- GCコントローラーハブ（WUP-028）
- VRChat+（ドローン機能はVRC+限定）
- [ViGEmBus](https://github.com/nefarius/ViGEmBus/releases)
- [Zadig](https://zadig.akeo.ie/)
- [Delfinovin](https://github.com/Struggleton/Delfinovin)

## セットアップ手順

### 1. ViGEmBus のインストール

[ViGEmBus リリースページ](https://github.com/nefarius/ViGEmBus/releases) から最新のインストーラーをダウンロードしてインストール。インストール設定はデフォルトのままでOK。

### 2. Zadig でドライバーを変換する

[Zadig](https://zadig.akeo.ie/) をダウンロードして起動する（インストール不要、設定変更も不要）。GCコントローラーハブの少なくとも黒色のUSBをPCに接続した状態で起動。

1. **Options → List All Devices** にチェックを入れる
2. プルダウンから **WUP-028** を選択
3. 右のボックスで **WinUSB** を選択
4. **Install Driver** を実行

### 3. Delfinovin の起動

[Delfinovin](https://github.com/Struggleton/Delfinovin) をダウンロードし、任意の場所に配置する（インストール先はデフォルトのままでOK）。

GCコントローラーハブを接続した状態で `Delfinovin.exe` を起動し、コントローラーが認識されているか確認する。

**Delfinovin を起動したままにしておかないと、Steam はコントローラーを認識しないことに注意。**

私の場合では1番左のポートで認識が不安定だったため、**4番目（一番右）のポート**を使用。Delfinovinの下のタブのControllerが点滅しているようであれば認識が不安定。

### 4. Steam でコントローラーの認識を確認する

Steamを起動後、左上の**Steam → 設定 → コントローラー** を開き、`Xbox 360 Controller` のようなコントローラー情報が表示されていれば認識成功。

## VRChat でドローンを起動する

任意のワールドに入り、**ESC → 歯車マーク（設定） → ドローン** を選択する。

ドローン機能には **VRChat+（有料サブスクリプション）** が必要。月額価格は9.99$（更新日時点）。

## ドローンの設定と操作

### Dead Zone の調整

デフォルト（0.10）のままだと、GCコンのわずかな動きにも反応してドローンが大きく動いてしまう。**まず0.15に上げて様子を見て、それでも動きすぎるなら0.25まで上げる**のがよい。コントローラー個体差があるため、この範囲で各自調整を。

### 設定項目の意味

| 設定名 | 意味 |
|---|---|
| Take Photo | 写真撮影 |
| Enable FPV | FPV視点（ドローン目線）に切替 |
| Self Leveling | 自動水平維持 |
| Flight Presets | 飛行モード切替（Cinematic / Angle 等） |
| Respawn | ドローンを自分の元に呼び戻す |

### 操作

- **左スティック**：上昇・下降・回転
- **右スティック**：前後左右移動

### 練習におすすめの設定

**Cinematic モード + Self Leveling ON** でまず浮かせる練習からはじめるのがおすすめ。なれたら、Self LevelingをOFFにしたり、モードをRacingにするなどして、よりリアルなドローン操縦に近づく。
