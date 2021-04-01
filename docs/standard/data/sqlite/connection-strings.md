---
title: 接続文字列
ms.date: 12/08/2020
description: 接続文字列でサポートされているキーワードと値です。
ms.openlocfilehash: 35283664c4ac3985d4f517fde77644ab2a891120
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110742"
---
# <a name="connection-strings"></a>接続文字列

接続文字列は、データベースへの接続方法を指定するために使用されます。 Microsoft.Data.Sqlite の接続文字列は、セミコロンで区切られたキーワードと値のリストとして、標準の [ADO.NET 構文](../../../framework/data/adonet/connection-strings.md)に従っています。

## <a name="keywords"></a>キーワード

Microsoft.Data.Sqlite では次の接続文字列キーワードを使用できます。

### <a name="data-source"></a>データ ソース

データベース ファイルのパス。 *DataSource* (スペースなし) と *Filename* はこのキーワードの別名です。

SQLite では、パスは現在の作業ディレクトリからの相対パスとして扱われます。 絶対パスも指定できます。

**空** の場合、一時的なディスク上のデータベースが作成されます。このデータベースは接続が閉じられるときに削除されます。

`:memory:` の場合、インメモリ データベースが使用されます。 詳細については、「[インメモリ データベース](in-memory-databases.md)」を参照してください。

`|DataDirectory|` 置換文字列で始まるパスは、相対パスと同じように扱われます。 設定すると、パスは DataDirectory アプリケーション ドメイン プロパティ値を基準とした相対パスになります。

このキーワードでは、[URI ファイル名](https://www.sqlite.org/uri.html)もサポートされます。

### <a name="mode"></a>モード

接続モード。

| [値]           | 説明                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | 読み取りと書き込みを行うデータベースを開きます。データベースが存在しない場合は作成します。 既定値です。 |
| ReadWrite       | 読み取りと書き込みを行うデータベースを開きます。                                                        |
| ReadOnly        | データベースを読み取り専用モードで開きます。                                                              |
| メモリ          | インメモリ データベースを開きます。                                                                       |

### <a name="cache"></a>キャッシュ

接続で使用されるキャッシュ モード。

| [値]   | 説明                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Default | 基になる SQLite ライブラリの既定のモードを使用します。 既定値です。                   |
| Private | 各接続で、プライベート キャッシュを使用します。                                                          |
| Shared  | 接続でキャッシュを共有します。 このモードでは、トランザクションとテーブル ロックの動作が変更される場合があります。 |

### <a name="password"></a>パスワード

暗号化キー。 指定した場合、接続を開いた直後に `PRAGMA key` が送信されます。

> [!WARNING]
> 暗号化がネイティブ SQLite ライブラリでサポートされていない場合、パスワードの効果はありません。

> [!NOTE]
> パスワード キーワードは、バージョン 3.0 で追加されました。

### <a name="foreign-keys"></a>外部キー

外部キー制約を有効にするかどうかを示す値です。

> [!NOTE]
> 外部キー キーワードは、バージョン 3.0 で追加されました。

| 値   | 説明
| ------- | --- |
| True    | 接続を開いた直後に `PRAGMA foreign_keys = 1` を送信します。
| False   | 接続を開いた直後に `PRAGMA foreign_keys = 0` を送信します。
| (空) | `PRAGMA foreign_keys` を送信しません。 既定値です。 |

e_sqlite3 の場合のように、ネイティブ SQLite ライブラリをコンパイルするために SQLITE_DEFAULT_FOREIGN_KEYS が使用された場合は、外部キーを有効にする必要はありません。

### <a name="recursive-triggers"></a>再帰トリガー

再帰トリガーを有効にするかどうかを示す値です。

> [!NOTE]
> 再帰トリガー キーワードは、バージョン 3.0 で追加されました。

| 値 | 説明                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | 接続を開いた直後に `PRAGMA recursive_triggers` を送信します。 |
| False | `PRAGMA recursive_triggers` を送信しません。 既定値です。              |

## <a name="connection-string-builder"></a>接続文字列ビルダー

<xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> は、厳密に型指定された方法で接続文字列を作成する際に使用できます。 接続文字列のインジェクション攻撃を防止するためにも使用できます。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>使用例

### <a name="basic"></a>Basic

コンカレンシーを向上させるために共有キャッシュを使用する基本的な接続文字列。

```connectionstring
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Encrypted

暗号化されたデータベース。

```connectionstring
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>読み取り専用

アプリによって変更できない読み取り専用のデータベース。

```connectionstring
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>メモリ内

非公開のインメモリ データベース。

```connectionstring
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>共有可能なインメモリ

*Sharable* という名前で識別される、共有可能なインメモリ データベース。

```connectionstring
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>関連項目

* [ADO.NET での接続文字列](../../../framework/data/adonet/connection-strings.md)
* [インメモリ データベース](in-memory-databases.md)
* [トランザクション](transactions.md)
