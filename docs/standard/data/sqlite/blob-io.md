---
title: BLOB の I/O
ms.date: 12/08/2020
description: SQLite の BLOB I/O 機能の使用方法について説明します。
ms.openlocfilehash: 8b305669f3155d2366215e9a05beb5ed51533d81
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110046"
---
# <a name="blob-io"></a><span data-ttu-id="a35d3-103">BLOB の I/O</span><span class="sxs-lookup"><span data-stu-id="a35d3-103">Blob I/O</span></span>

> [!NOTE]
> <span data-ttu-id="a35d3-104">SqliteBlob クラスは、バージョン 3.0 で追加されました。</span><span class="sxs-lookup"><span data-stu-id="a35d3-104">The SqliteBlob class was added in version 3.0.</span></span>

<span data-ttu-id="a35d3-105">データベースとの間でデータをストリーミングして、ラージ オブジェクトの読み取りと書き込み中のメモリ使用量を削減できます。</span><span class="sxs-lookup"><span data-stu-id="a35d3-105">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="a35d3-106">これは、データを解析または変換するときに特に有用です。</span><span class="sxs-lookup"><span data-stu-id="a35d3-106">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="a35d3-107">最初に、行を通常どおりに挿入します。</span><span class="sxs-lookup"><span data-stu-id="a35d3-107">Start by inserting a row as normal.</span></span> <span data-ttu-id="a35d3-108">`zeroblob()` SQL 関数を使用して、ラージ オブジェクトを保持するデータベースの領域を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a35d3-108">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="a35d3-109">`last_insert_rowid()` 関数を使用すると、rowid を簡単に取得できます。</span><span class="sxs-lookup"><span data-stu-id="a35d3-109">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="a35d3-110">行を挿入したら、<xref:Microsoft.Data.Sqlite.SqliteBlob> を使用してストリームを開き、ラージ オブジェクトを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a35d3-110">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="a35d3-111">データベースからラージ オブジェクトをストリーミングするには、ラージ オブジェクトの列のほか、ここに示すように、rowid またはその別名のいずれかを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a35d3-111">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="a35d3-112">rowid を選択しない場合、オブジェクト全体がメモリに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="a35d3-112">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="a35d3-113">正常に完了すると、`GetStream()` によって返されるオブジェクトは `SqliteBlob` になります。</span><span class="sxs-lookup"><span data-stu-id="a35d3-113">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
