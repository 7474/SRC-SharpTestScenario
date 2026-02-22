# テストカバレッジ進捗

## イベントラベル

| カテゴリ | ラベル | カバー状況 |
|---------|--------|-----------|
| 基本 | プロローグ | ✅ 全ファイルで使用 |
| 基本 | スタート | ✅ 全ファイルで使用 |
| 基本 | エピローグ | ✅ 多くのファイルで使用 |
| 基本 | 全滅 味方 | ✅ 複数ファイルで使用 |
| 基本 | 全滅 敵 | ✅ 複数ファイルで使用 |
| 基本 | 勝利条件 | ✅ 001.eveで使用 |
| 戦闘 | ターン | ✅ 001.eveで使用 |
| 戦闘 | 会話 | ✅ gui-message.eveで使用 |
| 戦闘 | 収納 | ✅ 002.eveで使用 |
| 戦闘 | 進入 | ✅ 003.eveで使用 |
| カスタム | マップコマンド | ✅ 複数ファイルで使用 |
| カスタム | ユニットコマンド | ✅ 004.eveで使用 |
| 戦闘 | 損傷率 | ✅ evt-combat.eveで使用 |
| 戦闘 | 破壊 | ✅ evt-combat.eveで使用 |
| 戦闘 | 攻撃 | ✅ evt-combat.eveで使用 |
| 戦闘 | 攻撃後 | ✅ evt-combat.eveで使用 |
| 戦闘 | 接触 | ✅ evt-combat.eveで使用 |
| 戦闘 | 脱出 | ✅ evt-combat.eveで使用 |
| 戦闘 | 使用 | ✅ evt-combat.eveで使用 |
| 戦闘 | 使用後 | ✅ evt-combat.eveで使用 |
| 戦闘 | 変形 | ✅ evt-combat.eveで使用 |
| 戦闘 | 合体 | ✅ evt-combat.eveで使用 |
| 戦闘 | 分離 | ✅ evt-combat.eveで使用 |
| 戦闘 | 行動終了 | ✅ evt-combat.eveで使用 |
| 戦闘 | レベルアップ | ✅ evt-combat.eveで使用 |
| その他 | 再開 | ✅ evt-combat.eveで使用 |

## イベントコマンド

| カテゴリ | コマンド | カバー状況 |
|---------|---------|-----------|
| **ステージ制御** | | |
| | Continue | ✅ |
| | GameClear | ✅ |
| | GameOver | ✅ |
| | Exec | ❌ |
| | Quit | ❌ |
| **イベント制御** | | |
| | Exit | ✅ |
| | ClearEvent | ✅ evt-combat.eveで使用 |
| | RestoreEvent | ❌ |
| | Cancel | ❌ |
| **ユニット操作** | | |
| | Create | ✅ |
| | Unit | ✅ |
| | Launch | ✅ |
| | BossRank | ✅ |
| | ChangeArea | ✅ |
| | ChangeUnitBitmap | ✅ |
| | Charge | ✅ |
| | Transform | ✅ |
| | Split | ✅ |
| | Upgrade | ✅ |
| | UseAbility | ✅ |
| | Attack | ❌ |
| | ChangeMode | ❌ |
| | ChangeParty | ❌ |
| | ClearSpecialPower | ❌ |
| | ClearStatus | ❌ |
| | Combine | ❌ |
| | Destroy | ❌ |
| | Disable | ❌ |
| | Enable | ❌ |
| | Escape | ✅ evt-combat.eveで使用 |
| | ExchangeItem | ❌ |
| | Finish | ❌ |
| | Join | ❌ |
| | Land | ❌ |
| | Leave | ❌ |
| | MapAbility | ❌ |
| | MapAttack | ❌ |
| | Move | ❌ |
| | Organize | ❌ |
| | RankUp | ❌ |
| | RecoverEN | ❌ |
| | RecoverHP | ❌ |
| | RemoveUnit | ❌ |
| | Select | ❌ |
| | SelectTarget | ❌ |
| | SetBullet | ❌ |
| | SetMessage | ❌ |
| | SetStatus | ❌ |
| | SetStock | ❌ |
| | ShowUnitStatus | ❌ |
| | SpecialPower | ❌ |
| | StopSummoning | ❌ |
| | Supply | ❌ |
| **パイロット操作** | | |
| | Pilot | ✅ |
| | Ride | ✅ |
| | ReplacePilot | ✅ |
| | IncreaseMorale | ✅ |
| | ClearSkill | ❌ |
| | ExpUp | ❌ |
| | Fix | ❌ |
| | GetOff | ❌ |
| | LevelUp | ❌ |
| | RecoverPlana | ❌ |
| | RecoverSP | ❌ |
| | Release | ❌ |
| | RemovePilot | ❌ |
| | SetRelation | ❌ |
| | SetSkill | ❌ |
| **アイテム操作** | | |
| | Equip | ✅ |
| | Item | ✅ |
| | RemoveItem | ❌ |
| **会話** | | |
| | Talk | ✅ |
| | AutoTalk | ❌ |
| **選択肢入力** | | |
| | Ask | ✅ |
| | Confirm | ✅ |
| | Input | ✅ |
| | Question | ❌ |
| **実行制御** | | |
| | Break | ✅ |
| | Call | ✅ |
| | Do | ✅ |
| | For | ✅ |
| | ForEach | ✅ |
| | GoTo | ✅ |
| | If | ✅ |
| | Local | ✅ |
| | Return | ✅ |
| | Skip | ✅ |
| | Switch | ✅ |
| | UpVar | ❌ |
| **変数操作** | | |
| | Array | ✅ |
| | Set | ✅ |
| | Incr | ✅ |
| | CopyArray | ❌ |
| | Global | ❌ |
| | Sort | ❌ |
| | Swap | ❌ |
| | UnSet | ❌ |
| **画面操作** | | |
| | Arc | ✅ |
| | Circle | ✅ |
| | Cls | ✅ |
| | ClearObj | ✅ |
| | ClearPicture | ✅ |
| | Color | ✅ |
| | DrawOption | ✅ |
| | DrawWidth | ✅ |
| | FadeIn | ✅ |
| | FadeOut | ✅ |
| | Font | ✅ |
| | HotPoint | ✅ |
| | Line | ✅ |
| | Oval | ✅ |
| | PaintPicture | ✅ |
| | PaintString | ✅ |
| | Polygon | ✅ |
| | PSet | ✅ |
| | Redraw | ❌ |
| | Refresh | ✅ |
| | Telop | ✅ |
| | WhiteIn | ✅ |
| | WhiteOut | ✅ |
| | Center | ❌ |
| | Explode | ❌ |
| | FillColor | ❌ |
| | FillStyle | ❌ |
| | Hide | ❌ |
| | PaintSysString | ❌ |
| | Show | ❌ |
| **サウンド** | | |
| | PlaySound | ✅ |
| | StartBGM | ❌ |
| | StopBGM | ❌ |
| | KeepBGM | ❌ |
| | PlayMIDI | ❌ |
| | RenameBGM | ❌ |
| **マップ操作** | | |
| | ChangeMap | ✅ |
| | ChangeTerrain | ✅ |
| | ColorFilter | ✅ |
| | Monotone | ✅ |
| | Night | ✅ |
| | Noon | ✅ |
| | Sepia | ✅ |
| | Sunset | ✅ |
| | Water | ✅ |
| **ファイル操作** | | |
| | Open | ✅ |
| | Close | ✅ |
| | Print | ✅ |
| | LineRead | ✅ |
| | CopyFile | ✅ |
| | RemoveFile | ✅ |
| | RenameFile | ✅ |
| | CreateFolder | ✅ |
| | RemoveFolder | ✅ |
| **その他** | | |
| | Debug | ✅ |
| | IntermissionCommand | ✅ |
| | Option | ✅ |
| | Wait | ✅ |
| | Suspend | ✅ |
| | CallIntermissionCommand | ❌ |
| | Forget | ❌ |
| | FreeMemory | ❌ |
| | Load | ❌ |
| | MakePilotList | ❌ |
| | MakeUnitList | ❌ |
| | Money | ❌ |
| | QuickLoad | ❌ |
| | RenameTerm | ❌ |
| | Require | ❌ |
| | SaveData | ❌ |

## 関数のテストカバレッジ

### カバー済みの関数
- ユニット情報: `X()`, `Y()`, `Unit()`, `Status()`
- その他: `Random()`, `EOF()`
- リスト: `ユニット一覧()`, `パイロット一覧()`
- 文字列: 変数展開 `$(変数名)`

### 未カバーの主要な関数
- ユニット情報: `Action()`, `Area()`, `Condition()`, `CountItem()`, `CountPilot()`, `Damage()`, `EN()`, `HP()`, `IsAvailable()`, `IsEquiped()`, `Item()`, `Party()`, `Pilot()`, `PilotID()`, `Rank()`, `SpecialPower()`, `UnitID()`, `WX()`, `WY()`
- パイロット情報: `Level()`, `Morale()`, `Plana()`, `Relation()`, `Skill()`, `SP()`
- Info関数: `Info()`（各種データ参照）
- 文字列処理: `Format()`, `InStr()`, `Len()`, `Left()`, `Mid()`, `Right()`, `Replace()`, `IsNumeric()`, `StrComp()`, `Wide()`
- リスト処理: `List()`, `LLength()`, `LIndex()`, `LSearch()`
- 算術処理: `Abs()`, `Int()`, `Max()`, `Min()`, `Round()`
- ファイル処理: `Dir()`（一部カバー済み）
- その他: `Args()`, `Call()`, `Count()`, `Eval()`, `IIf()`, `IsDefined()`, `IsVarDefined()`, `KeyState()`, `Nickname()`, `Term()`
