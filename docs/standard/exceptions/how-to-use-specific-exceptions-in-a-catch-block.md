---
description: '詳細情報: catch ブロックで特定の例外を使用する方法'
title: '方法: catch ブロックで特定の例外を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: 5eb2a753af05c10b722cc7e41b5bb13f45fdef9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775865"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="b8ce1-103">catch ブロックで特定の例外を使用する方法</span><span class="sxs-lookup"><span data-stu-id="b8ce1-103">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="b8ce1-104">一般的には、基本的な `catch` ステートメントを使用するよりも、特定の種類の例外をキャッチするプログラミング手法を勧めします。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-104">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="b8ce1-105">例外が発生すると、スタックに渡され、各 catch ブロックが処理する機会を与えられます。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-105">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="b8ce1-106">catch ステートメントの順序が重要です。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-106">The order of catch statements is important.</span></span> <span data-ttu-id="b8ce1-107">一般的な例外 catch ブロックまたはコンパイラがエラーを発行する前に、特定の例外を対象とした catch ブロックを配置します。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-107">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="b8ce1-108">適切な catch ブロックは、例外の種類を catch ブロックで指定された例外の名前に一致させることで決まります。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-108">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="b8ce1-109">特定の catch ブロックがない場合は、汎用 catch ブロック (ある場合) によってキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-109">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="b8ce1-110">次のコード例では、`try`/`catch` ブロックを使用して <xref:System.InvalidCastException> をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-110">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="b8ce1-111">サンプルでは、1 つのプロパティ、従業員レベル (`Emlevel`) を使用して、`Employee` と呼ばれるクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-111">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="b8ce1-112">メソッド `PromoteEmployee` は、オブジェクトを受け取って、従業員レベルをインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-112">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="b8ce1-113"><xref:System.DateTime> インスタンスが `PromoteEmployee` メソッドに渡されたとき、<xref:System.InvalidCastException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="b8ce1-113">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="b8ce1-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8ce1-114">See also</span></span>

- [<span data-ttu-id="b8ce1-115">例外</span><span class="sxs-lookup"><span data-stu-id="b8ce1-115">Exceptions</span></span>](index.md)
