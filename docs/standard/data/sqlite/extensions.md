---
title: 拡張機能
ms.date: 12/08/2020
description: SQLite 拡張機能を読み込む方法について説明します。
ms.openlocfilehash: 45ef5d2e5e8ea1f25866d3239e06fc87d8a91d44
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190048"
---
# <a name="extensions"></a><span data-ttu-id="d0a7d-103">拡張機能</span><span class="sxs-lookup"><span data-stu-id="d0a7d-103">Extensions</span></span>

<span data-ttu-id="d0a7d-104">SQLite では、実行時の拡張機能の読み込みがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="d0a7d-105">拡張機能には、追加の SQL 関数、照合順序、仮想テーブルなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="d0a7d-106">.NET Core には、参照されている NuGet パッケージなどの追加の場所でネイティブ ライブラリを見つけるための、追加のロジックがあります。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="d0a7d-107">ただし、SQLite ではこのロジックを利用できません。プラットフォーム API を直接呼び出して、ライブラリが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="d0a7d-108">このため、SQLite 拡張機能を読み込む前に、PATH、LD_LIBRARY_PATH、または DYLD_LIBRARY_PATH の各環境変数の変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-108">Because of this, you may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="d0a7d-109">GitHub には、参照されている NuGet パッケージ内の現在のランタイムのバイナリの検索方法を示す[サンプル](https://github.com/dotnet/docs/blob/main/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs)があります。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-109">There's [a sample](https://github.com/dotnet/docs/blob/main/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="d0a7d-110">拡張機能を読み込むには、<xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="d0a7d-111">Microsoft.Data.Sqlite を使用すると、接続をいったん閉じて再び開いた場合でも、拡張機能は読み込まれたままになります。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

> [!NOTE]
> <span data-ttu-id="d0a7d-112">LoadExtension メソッドはバージョン 3.0 で追加されました。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-112">The LoadExtension method was added in version 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0a7d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0a7d-113">See also</span></span>

* [<span data-ttu-id="d0a7d-114">実行時に読み込み可能な拡張機能</span><span class="sxs-lookup"><span data-stu-id="d0a7d-114">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
