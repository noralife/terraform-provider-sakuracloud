# データベース(sakuracloud_database)

### 設定例

```tf:データベース設定サンプル.tf
# データベースの定義
resource "sakuracloud_database" "foobar" {

    admin_password = "DatabasePasswordAdmin397"
    user_name = "defuser"
    user_password = "DatabasePasswordUser397"

    allow_networks = ["192.168.11.0/24","192.168.12.0/24"]

    port = 54321

    backup_rotate = 8
    backup_time = "00:00"


    # 接続先スイッチが共有セグメント以外の場合、以下の項目を設定する
    # switch_id = "${sakuracloud_switch.sw.id}"
    # ipaddress1 = "192.168.11.101"
    # nw_mask_len = 24
    # default_route = "192.168.11.1"

    name = "name_before"
    description = "description_before"
    tags = ["hoge1" , "hoge2"]

    zone = "tk1a"
}
```

## `sakuracloud_database`

データベースアプライアンスを表します。

### パラメーター

|パラメーター       |必須  |名称           |初期値     |設定値                         |補足                                          |
|-----------------|:---:|----------------|:--------:|-------------------------------|----------------------------------------------|
| `name`          | ◯   | データベース名   | -        | 文字列                         | - |
| `admin_password`| ◯   | 管理者パスワード  | -        | 文字列                         | - |
| `user_name`     | ◯   | ユーザー名       | -        | 文字列                         | - |
| `user_password` | ◯   | パスワード       | -        | 文字列                         | - |
| `allow_networks`| -   | 送信元ネットワーク | -        | リスト(文字列)、`xxx.xxx.xxx.xxx`、または`xxx.xxx.xxx.xxx/nn`形式 | 接続を許可するネットワークアドレスを指定する |
| `port`          | -   | ポート番号       | `5432`   | `1024`〜`65525`の範囲の整数     | - |
| `backup_rotate` | ◯   | バックアップ世代数    | `8`   | `1`〜`8`の範囲の整数     | - |
| `backup_time`   | ◯   | バックアップ開始時刻   | -   | `hh:mm`形式の時刻文字列     | `hh`部分は`00`〜`23`、`mm`部分は`00`/`15`/`30`/`45`のいずれかを指定 |
| `switch_id`     | -   | スイッチID      | `shared` | 文字列                         | 共有セグメントに接続する場合は`shared`<br />以外の場合はスイッチのIDを指定する |
| `ipaddress1`    | △   | IPアドレス1     | -        | 文字列                         | `switch_id`が`shared`以外の場合のみ有効、かつ必須 |
| `nw_mask_len`   | △   | ネットマスク     | -        | 数値                          | `switch_id`が`shared`以外の場合のみ有効、かつ必須 |
| `default_route` | -   | ゲートウェイ     | -        | 文字列                        | `switch_id`が`shared`以外の場合のみ有効 |
| `description`   | -   | 説明           | -        | 文字列                         | - |
| `tags`          | -   | タグ           | -        | リスト(文字列)                  | - |
| `zone`          | -   | ゾーン          | -        | `tk1a` | - |


### 属性

|属性名          | 名称             | 補足                  |
|---------------|------------------|----------------------|
| `id`            | データベースID | -                    |
| `name`          | データベース名 | -                    |
| `admin_password`| 管理者パスワード | -                    |
| `user_name`     | ユーザー名       | -                    |
| `user_password` | パスワード       | -                    |
| `allow_networks`| 送信元ネットワーク       | -                    |
| `port`          | ポート番号       | -                    |
| `backup_rotate` | バックアップ世代数       | -                    |
| `backup_time`   | バックアップ開始時刻       | -                    |
| `switch_id`     | スイッチID      | -                    |
| `ipaddress1`    | IPアドレス1      | -                    |
| `nw_mask_len`   | ネットマスク      | -                   |
| `default_route` | ゲートウェイ      | -                   |
| `description`   | 説明             | -                   |
| `tags`          | タグ             | -                  |
| `zone`          | ゾーン           | -                   |

