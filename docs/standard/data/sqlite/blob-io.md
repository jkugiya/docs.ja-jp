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
# <a name="blob-io"></a>BLOB の I/O

> [!NOTE]
> SqliteBlob クラスは、バージョン 3.0 で追加されました。

データベースとの間でデータをストリーミングして、ラージ オブジェクトの読み取りと書き込み中のメモリ使用量を削減できます。 これは、データを解析または変換するときに特に有用です。

最初に、行を通常どおりに挿入します。 `zeroblob()` SQL 関数を使用して、ラージ オブジェクトを保持するデータベースの領域を割り当てます。 `last_insert_rowid()` 関数を使用すると、rowid を簡単に取得できます。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

行を挿入したら、<xref:Microsoft.Data.Sqlite.SqliteBlob> を使用してストリームを開き、ラージ オブジェクトを書き込みます。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

データベースからラージ オブジェクトをストリーミングするには、ラージ オブジェクトの列のほか、ここに示すように、rowid またはその別名のいずれかを選択する必要があります。 rowid を選択しない場合、オブジェクト全体がメモリに読み込まれます。 正常に完了すると、`GetStream()` によって返されるオブジェクトは `SqliteBlob` になります。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
