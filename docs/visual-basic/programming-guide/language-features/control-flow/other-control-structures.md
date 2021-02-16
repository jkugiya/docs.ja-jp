---
description: '詳細情報: その他の制御構造 (Visual Basic)'
title: その他の制御構造
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 39654b8c780369eeea043087c8a04e2ba1f928c2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473577"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="da535-103">その他の制御構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da535-103">Other Control Structures (Visual Basic)</span></span>

<span data-ttu-id="da535-104">Visual Basic には、リソースを破棄したり、オブジェクト参照を繰り返さなければならない回数を減らしたりするうえで役立つ制御構造が用意されています。</span><span class="sxs-lookup"><span data-stu-id="da535-104">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="da535-105">Using...End Using コンストラクション</span><span class="sxs-lookup"><span data-stu-id="da535-105">Using...End Using Construction</span></span>  

 <span data-ttu-id="da535-106">`Using...End Using` コンストラクションによりステートメント ブロックが構築され、このブロック内で SQL 接続などのリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="da535-106">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="da535-107">必要に応じて、`Using` ステートメントを使用してリソースを取得できます。</span><span class="sxs-lookup"><span data-stu-id="da535-107">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="da535-108">`Using` ブロックを終了すると、リソースが自動的に破棄され、他のコードがそのリソースを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="da535-108">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="da535-109">リソースはローカルで、破棄可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="da535-109">The resource must be local and disposable.</span></span> <span data-ttu-id="da535-110">詳細については、「[Using ステートメント](../../../language-reference/statements/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da535-110">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="da535-111">With...End With コンストラクション</span><span class="sxs-lookup"><span data-stu-id="da535-111">With...End With Construction</span></span>  

 <span data-ttu-id="da535-112">`With...End With` コンストラクションを使用すると、オブジェクト参照を一度指定した後、そのメンバーにアクセスする一連のステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="da535-112">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="da535-113">これにより、Visual Basic にアクセスするステートメントごとに参照を再確立する必要がなくなるため、コードが簡略化され、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="da535-113">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="da535-114">詳細については、「[With...End With ステートメント](../../../language-reference/statements/with-end-with-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da535-114">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da535-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="da535-115">See also</span></span>

- [<span data-ttu-id="da535-116">制御フロー</span><span class="sxs-lookup"><span data-stu-id="da535-116">Control Flow</span></span>](index.md)
- [<span data-ttu-id="da535-117">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="da535-117">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="da535-118">ループ構造</span><span class="sxs-lookup"><span data-stu-id="da535-118">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="da535-119">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="da535-119">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="da535-120">Using ステートメント</span><span class="sxs-lookup"><span data-stu-id="da535-120">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="da535-121">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="da535-121">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
