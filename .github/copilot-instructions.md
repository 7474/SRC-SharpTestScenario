# SRC# E2Eテストシナリオ Copilotインストラクション

このリポジトリはSRC#（[7474/SRC](https://github.com/7474/SRC)）のE2E動作確認用テストシナリオを管理しています。
SRC#はSRC（Super Robot Wars風シミュレーションRPGエンジン）のC#移植版であり、`.eve`ファイルで記述されたシナリオを実行することで動作を検証します。

## 基本方針

- **ヘルプドキュメント**: https://github.com/7474/SRC/tree/master/SRC.Sharp.Help/src にあるコマンド・イベント・関数のドキュメントが仕様の正式な情報源です。
- **文字コード**: すべてのファイルは`UTF-8`で記述します（オリジナルSRCのShift_JISとは異なります）。
- **テストの目的**: SRC#のゲームエンジンとしての動作を`.eve`シナリオで網羅的にテストすることが最終目標です。
- **データの参照**: `data/`フォルダ配下のデータパックを利用します。新しい作品データが必要な場合はSRC総合支援センターのデータパックから取得できますが、既存のデータで代用できる場合はそちらを優先します。

## リポジトリ構成

```
├── SRCSharpTest.eve          # メインエントリポイント（インターミッション→001.eveの流れ）
├── 001.eve ～ 004.eve        # ステージ連結テスト（攻撃、着艦、変形、合体等）
├── t001.eve                  # 等身大ユニットの動作確認
├── cmd-control.eve           # 制御構文テスト（For, ForEach, Call, Local等）
├── cmd-file.eve              # ファイルI/Oテスト（Open, Print, LineRead等）
├── cmd-paint.eve             # 描画テスト（PaintPicture, HotPoint等）
├── cmd-telop.eve             # テロップテスト
├── cmd-unit.eve              # ユニット操作テスト（ReplacePilot, Upgrade, Transform, Split等）
├── cmd-use.eve               # アビリティ使用テスト（UseAbility等）
├── gui-message.eve           # メッセージ表示テスト（Talk書式、BossRank、ForEach陣営等）
├── gui-screan.eve            # 画面描画テスト（Arc, Circle, Line, Oval, PSet, Polygon等）
├── intermission.eve          # インターミッション動作テスト
├── intermission-cmd.eve      # インターミッションコマンドテスト
├── Map/                      # マップデータファイル（.map）
└── data/                     # ゲームデータ（パイロット、ユニット、アイテム等）
    ├── System/               # システムデータ（alias.txt, item.txt, sp.txt等）
    ├── 疎通/                 # テスト専用データ（マップマン、チャージマン等）
    └── [作品名]/             # 各作品のデータパック
```

## .eveファイルの基本構文

### イベントラベル

イベントラベルはイベントの発生条件を定義します。末尾に`:`をつけます。

```
プロローグ:
# ステージ開始時の処理
Exit

スタート:
# マップ表示後の戦闘開始時処理
Exit

エピローグ:
# ステージクリア後の処理
Exit

全滅 味方:
# 味方全滅時（通常はGameOver）
GameOver
Exit

全滅 敵:
# 敵全滅時（通常は次ステージへ）
Continue 次のステージ.eve
Exit
```

### 作品データのインクルード

ステージで使用する作品データは`@作品名`で指定します。

```
@機動戦士ガンダム
@ドラゴンクエスト５
```

### 主要なイベントコマンド

#### ユニット作成・配置
```
# Create 陣営 ユニット名 レベル パイロット名 気力 X Y [ユニットID]
Create 味方 ガンダム 10 アムロ＝レイ 1 12 12
Create 敵 ザクⅡ 0 デニム(0079) 5 8 8

# Unit ユニット名 レベル （パイロットなしのユニット在庫作成）
Unit νガンダム 0

# Pilot パイロット名 レベル
Pilot 流竜馬 50

# Ride パイロット名 [ユニット名]
Ride 流竜馬

# Launch パイロット名 X Y
Launch 流竜馬 12 12
```

#### 会話表示
```
Talk パイロット名
メッセージ内容（複数行可）
セミコロン(;)で同一メッセージ内改行
End

# HTMLライクなタグで書式設定
Talk パイロット名
<B><BIG><COLOR=RED>強調テキスト</COLOR></BIG></B>
End
```

#### 制御構文
```
# 条件分岐
If 条件式 Then
    # 処理
ElseIf 別の条件 Then
    # 処理
Else
    # 処理
EndIf

# ループ
For i = 1 To 10 Step 2
    # 処理
Next

ForEach v In 配列名
    # 処理
Next

Do While 条件式
    # 処理
Loop

# サブルーチン
Call サブルーチン名
# ...
サブルーチン名:
# 処理
Return

# 選択肢
Confirm テキスト
# 選択 = 1(はい) or 0(いいえ)

Ask タイトル
選択肢1
選択肢2
選択肢3
End
# 選択 = 1, 2, 3...
```

## 現在のテストカバレッジ

最新のカバレッジ状況は [COVERAGE.md](../COVERAGE.md) を参照してください。

テストシナリオを追加・変更してカバレッジが変化した場合は、必ず `COVERAGE.md` の該当項目を更新してください。

## マイルストーン

テストカバレッジを段階的に向上させるため、以下のマイルストーンを設定します。

### マイルストーン1: 基本的なゲーム進行（優先度：最高）

ゲームの基本フローを網羅する最重要シナリオ群です。

**対象コマンド・イベント:**
- ユニット操作: `Move`, `Attack`, `Destroy`, `Escape`, `Finish`, `RecoverHP`, `RecoverEN`, `Supply`
- パイロット操作: `LevelUp`, `ExpUp`, `GetOff`, `RecoverSP`
- イベントラベル: `破壊`, `攻撃`, `攻撃後`, `損傷率`, `行動終了`, `レベルアップ`
- その他: `Money`, `Redraw`, `Center`

**推奨ファイル:** 新規 `cmd-battle.eve` を作成し、戦闘フロー関連のコマンドをテストする。

### マイルストーン2: 部隊管理とインターミッション（優先度：高）

インターミッションと部隊編成に関わる機能をテストします。

**対象コマンド・イベント:**
- ユニット操作: `Join`, `Leave`, `Organize`, `Land`, `ChangeParty`, `ChangeMode`, `RankUp`, `RemoveUnit`
- パイロット操作: `SetSkill`, `ClearSkill`, `SetRelation`, `Fix`, `Release`, `RemovePilot`
- アイテム操作: `RemoveItem`, `ExchangeItem`
- その他: `MakeUnitList`, `MakePilotList`, `CallIntermissionCommand`, `SaveData`, `Load`

**推奨ファイル:** 新規 `cmd-party.eve` を作成する。

### マイルストーン3: 高度なユニット操作（優先度：中）

特殊なユニット操作とステータス管理をテストします。

**対象コマンド・イベント:**
- ユニット操作: `Combine`, `Select`, `SelectTarget`, `SetStatus`, `ClearStatus`, `SetBullet`, `SetStock`, `SetMessage`, `ShowUnitStatus`, `SpecialPower`, `ClearSpecialPower`, `Disable`, `Enable`, `MapAttack`, `MapAbility`, `StopSummoning`
- パイロット操作: `RecoverPlana`
- その他: `AutoTalk`, `Question`, `Explode`
- イベントラベル: `接触`, `脱出`, `使用`, `使用後`, `変形`, `合体`, `分離`

**推奨ファイル:** 新規 `cmd-status.eve`, `evt-combat.eve` を作成する。

### マイルストーン4: イベント制御と高度な機能（優先度：低）

あまり使用頻度の高くない機能をカバーします。

**対象コマンド・イベント:**
- イベント制御: `ClearEvent`, `RestoreEvent`, `Cancel`
- 変数操作: `CopyArray`, `Global`, `Sort`, `Swap`, `UnSet`, `UpVar`
- 画面操作: `FillColor`, `FillStyle`, `Hide`, `Show`, `PaintSysString`
- サウンド: `StartBGM`, `StopBGM`, `KeepBGM`, `PlayMIDI`, `RenameBGM`
- ステージ制御: `Exec`, `Quit`
- その他: `Forget`, `FreeMemory`, `Require`, `RenameTerm`, `QuickLoad`
- イベントラベル: `再開`

**推奨ファイル:** 新規 `cmd-advanced.eve`, `cmd-sound.eve` を作成する。

## テストシナリオ作成ガイドライン

### 1. ファイル命名規則

- **コマンドテスト**: `cmd-{カテゴリ名}.eve`（例: `cmd-battle.eve`, `cmd-party.eve`）
- **イベントラベルテスト**: `evt-{カテゴリ名}.eve`（例: `evt-combat.eve`）
- **ステージ連結テスト**: `NNN.eve`の連番（例: `005.eve`）
- **個別機能テスト**: `t{NNN}.eve`（例: `t002.eve`）

### 2. テストシナリオの基本構造

各テストシナリオは以下の構造に従います。

```
# ファイル先頭にテスト概要のコメント

@使用する作品名

プロローグ:
# 必要なオプション設定
Exit

スタート:
# マップの読み込み
ChangeMap Map/001.map

# テスト用ユニットの配置
Create 味方 ユニット名 レベル パイロット名 気力 X Y
Create 敵 ユニット名 レベル パイロット名 気力 X Y

# テスト対象コマンドの実行
# Talk等で実行結果を表示し、目視確認できるようにする

Exit

エピローグ:
Exit

全滅 味方:
GameOver
Exit

全滅 敵:
GameClear
Exit
```

### 3. テスト設計の原則

- **各コマンドの基本動作を確認**: まずコマンドの最小限の引数での動作を確認し、次にオプション引数を含む動作を確認します。
- **目視確認可能にする**: `Talk`コマンドでコマンド実行前後の状態を表示し、動作が確認できるようにします。
- **マップコマンドで個別テスト**: 手動で何度も実行できるよう`マップコマンド`イベントに個別テストを配置することを推奨します。
- **既存データの活用**: `data/疎通/`にあるテスト専用データ（マップマン、チャージマン）や、各作品のデータパックを活用します。
- **関連コマンドのグループ化**: 関連するコマンドは同じファイルにまとめてテストの文脈を明確にします。

### 4. テスト用データの作成

テスト専用のユニット・パイロットデータが必要な場合は`data/疎通/`配下に追加します。

**パイロットデータ（Pilot.txt）の書式:**
```
パイロット名
愛称, -, 作品名, 地形適応(空陸海宇), ランク
特殊能力
特殊能力1, レベル1, ...
能力値（格闘, 射撃, 命中, 回避, 技量, 反応）, 性格
ＳＰ, SP値, SP名1, レベル1, ...
パイロット画像, BGMファイル
```

**ユニットデータ（Unit.txt）の書式:**
```
ユニット名
ユニット名, 愛称, (作品名), サイズ, 移動タイプ
移動エリア, 移動力, タイプ, HP, EN
特殊能力
特殊能力1
HP, EN, 装甲, 運動性
地形適応(空陸海宇), ユニット画像
武器名, 攻撃力, 射程下限, 射程上限, 命中補正, クリ補正, 弾数, EN, 地形適応, 気力, 属性
```

### 5. マップデータ

新しいマップが必要な場合は`Map/`ディレクトリに`.map`ファイルを追加します。
基本的には既存の`Map/001.map`～`Map/004.map`を再利用してください。

### 6. メインシナリオへの組み込み

新しいテストシナリオをステージ連結フローに組み込む場合は、`SRCSharpTest.eve`からの`Continue`チェーンの適切な位置に挿入するか、`intermission.eve`のインターミッションフローからアクセスできるようにします。

独立したテストシナリオ（`cmd-*.eve`等）は`SRCSharpTest.eve`のエントリポイントを変更して個別に実行できます。

## 関数のテストカバレッジ

最新のカバレッジ状況は [COVERAGE.md](../COVERAGE.md) を参照してください。

## 特殊能力と武器属性のテスト

SRC#のゲームエンジンでは多数の特殊能力と武器属性をサポートしています。これらの動作確認にはユニットデータの作成が必要になる場合があります。

### テスト用データ作成時の注意
- `data/疎通/`に新しいデータを追加する場合は、最小限のデータで特定の機能をテストできるようにします。
- 既存作品データ（ガンダム、ドラクエ等）のユニットが該当する特殊能力を持っている場合は、そちらを利用します。

## 注意事項

- ビットマップ、MIDI、サウンドファイルは`.gitignore`で除外されています（`bitmap/`, `MIDI/`, `sound/`）。これらのリソースが必要なテストは、リソースが存在しない場合でもエラーにならない（スキップされる）ように設計してください。
- テスト結果の確認は目視で行います。自動化テストフレームワークは現時点では使用していません。`Talk`コマンドや`Debug`コマンドを活用して実行結果を画面に表示してください。
- `Suspend`コマンドを使うと`Talk`の後にイベントを一時停止でき、手動操作で戦闘やコマンドを実行してから次のイベントに進むことができます。これはプレイヤー操作を伴うテストに有用です。
