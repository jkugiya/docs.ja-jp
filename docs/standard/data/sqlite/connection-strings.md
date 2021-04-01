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
# <a name="connection-strings"></a><span data-ttu-id="854fd-103">接続文字列</span><span class="sxs-lookup"><span data-stu-id="854fd-103">Connection strings</span></span>

<span data-ttu-id="854fd-104">接続文字列は、データベースへの接続方法を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="854fd-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="854fd-105">Microsoft.Data.Sqlite の接続文字列は、セミコロンで区切られたキーワードと値のリストとして、標準の [ADO.NET 構文](../../../framework/data/adonet/connection-strings.md)に従っています。</span><span class="sxs-lookup"><span data-stu-id="854fd-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="854fd-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="854fd-106">Keywords</span></span>

<span data-ttu-id="854fd-107">Microsoft.Data.Sqlite では次の接続文字列キーワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="854fd-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="854fd-108">データ ソース</span><span class="sxs-lookup"><span data-stu-id="854fd-108">Data source</span></span>

<span data-ttu-id="854fd-109">データベース ファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="854fd-109">The path to the database file.</span></span> <span data-ttu-id="854fd-110">*DataSource* (スペースなし) と *Filename* はこのキーワードの別名です。</span><span class="sxs-lookup"><span data-stu-id="854fd-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="854fd-111">SQLite では、パスは現在の作業ディレクトリからの相対パスとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="854fd-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="854fd-112">絶対パスも指定できます。</span><span class="sxs-lookup"><span data-stu-id="854fd-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="854fd-113">**空** の場合、一時的なディスク上のデータベースが作成されます。このデータベースは接続が閉じられるときに削除されます。</span><span class="sxs-lookup"><span data-stu-id="854fd-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="854fd-114">`:memory:` の場合、インメモリ データベースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="854fd-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="854fd-115">詳細については、「[インメモリ データベース](in-memory-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="854fd-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="854fd-116">`|DataDirectory|` 置換文字列で始まるパスは、相対パスと同じように扱われます。</span><span class="sxs-lookup"><span data-stu-id="854fd-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="854fd-117">設定すると、パスは DataDirectory アプリケーション ドメイン プロパティ値を基準とした相対パスになります。</span><span class="sxs-lookup"><span data-stu-id="854fd-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="854fd-118">このキーワードでは、[URI ファイル名](https://www.sqlite.org/uri.html)もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="854fd-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="854fd-119">モード</span><span class="sxs-lookup"><span data-stu-id="854fd-119">Mode</span></span>

<span data-ttu-id="854fd-120">接続モード。</span><span class="sxs-lookup"><span data-stu-id="854fd-120">The connection mode.</span></span>

| <span data-ttu-id="854fd-121">[値]</span><span class="sxs-lookup"><span data-stu-id="854fd-121">Value</span></span>           | <span data-ttu-id="854fd-122">説明</span><span class="sxs-lookup"><span data-stu-id="854fd-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="854fd-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="854fd-123">ReadWriteCreate</span></span> | <span data-ttu-id="854fd-124">読み取りと書き込みを行うデータベースを開きます。データベースが存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="854fd-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="854fd-125">既定値です。</span><span class="sxs-lookup"><span data-stu-id="854fd-125">This is the default.</span></span> |
| <span data-ttu-id="854fd-126">ReadWrite</span><span class="sxs-lookup"><span data-stu-id="854fd-126">ReadWrite</span></span>       | <span data-ttu-id="854fd-127">読み取りと書き込みを行うデータベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="854fd-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="854fd-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="854fd-128">ReadOnly</span></span>        | <span data-ttu-id="854fd-129">データベースを読み取り専用モードで開きます。</span><span class="sxs-lookup"><span data-stu-id="854fd-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="854fd-130">メモリ</span><span class="sxs-lookup"><span data-stu-id="854fd-130">Memory</span></span>          | <span data-ttu-id="854fd-131">インメモリ データベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="854fd-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="854fd-132">キャッシュ</span><span class="sxs-lookup"><span data-stu-id="854fd-132">Cache</span></span>

<span data-ttu-id="854fd-133">接続で使用されるキャッシュ モード。</span><span class="sxs-lookup"><span data-stu-id="854fd-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="854fd-134">[値]</span><span class="sxs-lookup"><span data-stu-id="854fd-134">Value</span></span>   | <span data-ttu-id="854fd-135">説明</span><span class="sxs-lookup"><span data-stu-id="854fd-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="854fd-136">Default</span><span class="sxs-lookup"><span data-stu-id="854fd-136">Default</span></span> | <span data-ttu-id="854fd-137">基になる SQLite ライブラリの既定のモードを使用します。</span><span class="sxs-lookup"><span data-stu-id="854fd-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="854fd-138">既定値です。</span><span class="sxs-lookup"><span data-stu-id="854fd-138">This is the default.</span></span>                   |
| <span data-ttu-id="854fd-139">Private</span><span class="sxs-lookup"><span data-stu-id="854fd-139">Private</span></span> | <span data-ttu-id="854fd-140">各接続で、プライベート キャッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="854fd-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="854fd-141">Shared</span><span class="sxs-lookup"><span data-stu-id="854fd-141">Shared</span></span>  | <span data-ttu-id="854fd-142">接続でキャッシュを共有します。</span><span class="sxs-lookup"><span data-stu-id="854fd-142">Connections share a cache.</span></span> <span data-ttu-id="854fd-143">このモードでは、トランザクションとテーブル ロックの動作が変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="854fd-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="854fd-144">パスワード</span><span class="sxs-lookup"><span data-stu-id="854fd-144">Password</span></span>

<span data-ttu-id="854fd-145">暗号化キー。</span><span class="sxs-lookup"><span data-stu-id="854fd-145">The encryption key.</span></span> <span data-ttu-id="854fd-146">指定した場合、接続を開いた直後に `PRAGMA key` が送信されます。</span><span class="sxs-lookup"><span data-stu-id="854fd-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="854fd-147">暗号化がネイティブ SQLite ライブラリでサポートされていない場合、パスワードの効果はありません。</span><span class="sxs-lookup"><span data-stu-id="854fd-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

> [!NOTE]
> <span data-ttu-id="854fd-148">パスワード キーワードは、バージョン 3.0 で追加されました。</span><span class="sxs-lookup"><span data-stu-id="854fd-148">The Password keyword was added in version 3.0.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="854fd-149">外部キー</span><span class="sxs-lookup"><span data-stu-id="854fd-149">Foreign Keys</span></span>

<span data-ttu-id="854fd-150">外部キー制約を有効にするかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="854fd-150">A value indicating whether to enable foreign key constraints.</span></span>

> [!NOTE]
> <span data-ttu-id="854fd-151">外部キー キーワードは、バージョン 3.0 で追加されました。</span><span class="sxs-lookup"><span data-stu-id="854fd-151">The Foreign Keys keyword was added in version 3.0.</span></span>

| <span data-ttu-id="854fd-152">値</span><span class="sxs-lookup"><span data-stu-id="854fd-152">Value</span></span>   | <span data-ttu-id="854fd-153">説明</span><span class="sxs-lookup"><span data-stu-id="854fd-153">Description</span></span>
| ------- | --- |
| <span data-ttu-id="854fd-154">True</span><span class="sxs-lookup"><span data-stu-id="854fd-154">True</span></span>    | <span data-ttu-id="854fd-155">接続を開いた直後に `PRAGMA foreign_keys = 1` を送信します。</span><span class="sxs-lookup"><span data-stu-id="854fd-155">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="854fd-156">False</span><span class="sxs-lookup"><span data-stu-id="854fd-156">False</span></span>   | <span data-ttu-id="854fd-157">接続を開いた直後に `PRAGMA foreign_keys = 0` を送信します。</span><span class="sxs-lookup"><span data-stu-id="854fd-157">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="854fd-158">(空)</span><span class="sxs-lookup"><span data-stu-id="854fd-158">(empty)</span></span> | <span data-ttu-id="854fd-159">`PRAGMA foreign_keys` を送信しません。</span><span class="sxs-lookup"><span data-stu-id="854fd-159">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="854fd-160">既定値です。</span><span class="sxs-lookup"><span data-stu-id="854fd-160">This is the default.</span></span> |

<span data-ttu-id="854fd-161">e_sqlite3 の場合のように、ネイティブ SQLite ライブラリをコンパイルするために SQLITE_DEFAULT_FOREIGN_KEYS が使用された場合は、外部キーを有効にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="854fd-161">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="854fd-162">再帰トリガー</span><span class="sxs-lookup"><span data-stu-id="854fd-162">Recursive triggers</span></span>

<span data-ttu-id="854fd-163">再帰トリガーを有効にするかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="854fd-163">A value that indicates whether to enable recursive triggers.</span></span>

> [!NOTE]
> <span data-ttu-id="854fd-164">再帰トリガー キーワードは、バージョン 3.0 で追加されました。</span><span class="sxs-lookup"><span data-stu-id="854fd-164">The Recursive Triggers keyword was added in version 3.0.</span></span>

| <span data-ttu-id="854fd-165">値</span><span class="sxs-lookup"><span data-stu-id="854fd-165">Value</span></span> | <span data-ttu-id="854fd-166">説明</span><span class="sxs-lookup"><span data-stu-id="854fd-166">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="854fd-167">True</span><span class="sxs-lookup"><span data-stu-id="854fd-167">True</span></span>  | <span data-ttu-id="854fd-168">接続を開いた直後に `PRAGMA recursive_triggers` を送信します。</span><span class="sxs-lookup"><span data-stu-id="854fd-168">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="854fd-169">False</span><span class="sxs-lookup"><span data-stu-id="854fd-169">False</span></span> | <span data-ttu-id="854fd-170">`PRAGMA recursive_triggers` を送信しません。</span><span class="sxs-lookup"><span data-stu-id="854fd-170">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="854fd-171">既定値です。</span><span class="sxs-lookup"><span data-stu-id="854fd-171">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="854fd-172">接続文字列ビルダー</span><span class="sxs-lookup"><span data-stu-id="854fd-172">Connection string builder</span></span>

<span data-ttu-id="854fd-173"><xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> は、厳密に型指定された方法で接続文字列を作成する際に使用できます。</span><span class="sxs-lookup"><span data-stu-id="854fd-173">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="854fd-174">接続文字列のインジェクション攻撃を防止するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="854fd-174">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="854fd-175">使用例</span><span class="sxs-lookup"><span data-stu-id="854fd-175">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="854fd-176">Basic</span><span class="sxs-lookup"><span data-stu-id="854fd-176">Basic</span></span>

<span data-ttu-id="854fd-177">コンカレンシーを向上させるために共有キャッシュを使用する基本的な接続文字列。</span><span class="sxs-lookup"><span data-stu-id="854fd-177">A basic connection string with a shared cache for improved concurrency.</span></span>

```connectionstring
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="854fd-178">Encrypted</span><span class="sxs-lookup"><span data-stu-id="854fd-178">Encrypted</span></span>

<span data-ttu-id="854fd-179">暗号化されたデータベース。</span><span class="sxs-lookup"><span data-stu-id="854fd-179">An encrypted database.</span></span>

```connectionstring
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="854fd-180">読み取り専用</span><span class="sxs-lookup"><span data-stu-id="854fd-180">Read-only</span></span>

<span data-ttu-id="854fd-181">アプリによって変更できない読み取り専用のデータベース。</span><span class="sxs-lookup"><span data-stu-id="854fd-181">A read-only database that cannot be modified by the app.</span></span>

```connectionstring
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="854fd-182">メモリ内</span><span class="sxs-lookup"><span data-stu-id="854fd-182">In-memory</span></span>

<span data-ttu-id="854fd-183">非公開のインメモリ データベース。</span><span class="sxs-lookup"><span data-stu-id="854fd-183">A private, in-memory database.</span></span>

```connectionstring
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="854fd-184">共有可能なインメモリ</span><span class="sxs-lookup"><span data-stu-id="854fd-184">Sharable in-memory</span></span>

<span data-ttu-id="854fd-185">*Sharable* という名前で識別される、共有可能なインメモリ データベース。</span><span class="sxs-lookup"><span data-stu-id="854fd-185">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```connectionstring
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="854fd-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="854fd-186">See also</span></span>

* [<span data-ttu-id="854fd-187">ADO.NET での接続文字列</span><span class="sxs-lookup"><span data-stu-id="854fd-187">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="854fd-188">インメモリ データベース</span><span class="sxs-lookup"><span data-stu-id="854fd-188">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="854fd-189">トランザクション</span><span class="sxs-lookup"><span data-stu-id="854fd-189">Transactions</span></span>](transactions.md)
