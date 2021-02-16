---
description: '詳細情報: 方法:コレクション初期化子を使用してコレクションを作成する (Visual Basic)'
title: '方法: コレクション初期化子によって使用されるコレクションを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 09928cb0fbeb0346fd0e1148ffcd6ddce54279c0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460021"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="1770a-103">方法: コレクション初期化子を使用してコレクションを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1770a-103">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="1770a-104">コレクション初期化子を使用してコレクションを作成すると、`Add` メソッドのパラメーターがコレクション初期化子の値の型と一致するコレクション型の `Add` メソッドが、Visual Basic コンパイラによって検索されます。</span><span class="sxs-lookup"><span data-stu-id="1770a-104">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="1770a-105">この `Add` メソッドは、コレクションに、コレクション初期化子の値を設定するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="1770a-105">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1770a-106">例</span><span class="sxs-lookup"><span data-stu-id="1770a-106">Example</span></span>  

 <span data-ttu-id="1770a-107">次の例が示す `OrderCollection` コレクションにはパブリック `Add` メソッドが含まれています。このメソッドは、コレクション初期化子が `Order` 型のオブジェクトを追加するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="1770a-107">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="1770a-108">`Add` メソッドを使用すると、短縮されたコレクション初期化子構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1770a-108">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1770a-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="1770a-109">See also</span></span>

- [<span data-ttu-id="1770a-110">コレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="1770a-110">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="1770a-111">方法: コレクション初期化子によって使用される Add 拡張メソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="1770a-111">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
