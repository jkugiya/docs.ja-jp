---
title: インメモリ データベース
ms.date: 12/13/2019
description: インメモリ SQLite データベースの使用方法について説明します。
ms.openlocfilehash: 8bc96811753e49f740a33a2e78f955483efcf04b
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190347"
---
# <a name="in-memory-databases"></a>インメモリ データベース

SQLite インメモリ データベースは、ディスク上ではなく、メモリ内に全体が格納されるデータベースです。 インメモリ データベースを作成するには、特殊なデータ ソース ファイル名 `:memory:` を使用します。 接続が閉じられると、データベースは削除されます。 `:memory:` を使用すると、各接続で独自のデータベースが作成されます。

```connectionstring
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>共有可能なインメモリ データベース

接続文字列で `Mode=Memory` と `Cache=Shared` を使用すると、インメモリ データベースを複数の接続間で共有できます。 インメモリ データベースに名前を付けるには、`Data Source` キーワードを使用します。 同じ名前を使用する接続文字列では、同じインメモリ データベースがアクセスされます。 データベースへの 1 つ以上の接続が開いたままになっている間は、そのデータベースは保持されます。 これを示す[サンプル](https://github.com/dotnet/docs/blob/main/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs)を GitHub で入手できます。

```connectionstring
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
