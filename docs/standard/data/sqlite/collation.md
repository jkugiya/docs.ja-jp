---
title: 照合順序
ms.date: 12/13/2019
description: カスタムの照合順序を作成する方法について説明します。
ms.openlocfilehash: ab330e798c95fec82892f02f4a1b6b96df6113b3
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190425"
---
# <a name="collation"></a><span data-ttu-id="1b35f-103">照合順序</span><span class="sxs-lookup"><span data-stu-id="1b35f-103">Collation</span></span>

<span data-ttu-id="1b35f-104">照合順序は、SQLite によって TEXT 値を比較して順序と等価性を判断するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b35f-104">Collating sequences are used by SQLite when comparing TEXT values to determine order and equality.</span></span> <span data-ttu-id="1b35f-105">SQL クエリで列の作成時または操作ごとに、使用する照合順序を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b35f-105">You can specify which collation to use when creating columns or per-operation in SQL queries.</span></span> <span data-ttu-id="1b35f-106">SQLite には、既定で 3 つの照合順序があります。</span><span class="sxs-lookup"><span data-stu-id="1b35f-106">SQLite includes three collating sequences by default.</span></span>

| <span data-ttu-id="1b35f-107">照合順序</span><span class="sxs-lookup"><span data-stu-id="1b35f-107">Collation</span></span> | <span data-ttu-id="1b35f-108">説明</span><span class="sxs-lookup"><span data-stu-id="1b35f-108">Description</span></span>                               |
| --------- | ----------------------------------------- |
| <span data-ttu-id="1b35f-109">RTRIM</span><span class="sxs-lookup"><span data-stu-id="1b35f-109">RTRIM</span></span>     | <span data-ttu-id="1b35f-110">末尾の空白を無視します</span><span class="sxs-lookup"><span data-stu-id="1b35f-110">Ignores trailing whitespace</span></span>               |
| <span data-ttu-id="1b35f-111">NOCASE</span><span class="sxs-lookup"><span data-stu-id="1b35f-111">NOCASE</span></span>    | <span data-ttu-id="1b35f-112">ASCII 文字 A から Z の大文字と小文字を区別しません</span><span class="sxs-lookup"><span data-stu-id="1b35f-112">Case-insensitive for ASCII characters A-Z</span></span> |
| <span data-ttu-id="1b35f-113">BINARY</span><span class="sxs-lookup"><span data-stu-id="1b35f-113">BINARY</span></span>    | <span data-ttu-id="1b35f-114">大文字と小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="1b35f-114">Case-sensitive.</span></span> <span data-ttu-id="1b35f-115">バイトを直接比較します</span><span class="sxs-lookup"><span data-stu-id="1b35f-115">Compares bytes directly</span></span>   |

## <a name="custom-collation"></a><span data-ttu-id="1b35f-116">カスタム照合順序</span><span class="sxs-lookup"><span data-stu-id="1b35f-116">Custom collation</span></span>

<span data-ttu-id="1b35f-117"><xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A> を使用して、独自の照合シーケンスを定義したり、組み込みの照合順序をオーバーライドしたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1b35f-117">You can also define your own collating sequences or override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>.</span></span> <span data-ttu-id="1b35f-118">次の例では、Unicode 文字をサポートするように NOCASE 照合順序をオーバーライドする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1b35f-118">The following example shows overriding the NOCASE collation to support Unicode characters.</span></span> <span data-ttu-id="1b35f-119">[コード サンプル全体](https://github.com/dotnet/docs/blob/main/samples/snippets/standard/data/sqlite/CollationSample/Program.cs)は GitHub で入手できます。</span><span class="sxs-lookup"><span data-stu-id="1b35f-119">The [full sample code](https://github.com/dotnet/docs/blob/main/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) is available on GitHub.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a><span data-ttu-id="1b35f-120">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="1b35f-120">Like operator</span></span>

<span data-ttu-id="1b35f-121">SQLite の LIKE 演算子では照合順序が考慮されません。</span><span class="sxs-lookup"><span data-stu-id="1b35f-121">The LIKE operator in SQLite doesn't honor collations.</span></span> <span data-ttu-id="1b35f-122">既定の実装には、NOCASE 照合順序と同じセマンティクスがあります。</span><span class="sxs-lookup"><span data-stu-id="1b35f-122">The default implementation has the same semantics as the NOCASE collation.</span></span> <span data-ttu-id="1b35f-123">ASCII 文字 A から Z の場合に限り、大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="1b35f-123">It's only case-insensitive for the ASCII characters A through Z.</span></span>

<span data-ttu-id="1b35f-124">次の pragma ステートメントを使用すると、簡単に LIKE 演算子で大文字と小文字が区別されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="1b35f-124">You can easily make the LIKE operator case-sensitive by using the following pragma statement:</span></span>

```sql
PRAGMA case_sensitive_like = 1
```

<span data-ttu-id="1b35f-125">LIKE 演算子の実装のオーバーライドの詳細については、「[ユーザー定義関数](user-defined-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b35f-125">See [User-defined functions](user-defined-functions.md) for details on overriding the implementation of the LIKE operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b35f-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b35f-126">See also</span></span>

* [<span data-ttu-id="1b35f-127">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="1b35f-127">User-defined functions</span></span>](user-defined-functions.md)
* [<span data-ttu-id="1b35f-128">SQL 構文</span><span class="sxs-lookup"><span data-stu-id="1b35f-128">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
