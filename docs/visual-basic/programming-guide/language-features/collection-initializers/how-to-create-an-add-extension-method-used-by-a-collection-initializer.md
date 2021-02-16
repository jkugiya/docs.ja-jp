---
description: '詳細情報: 方法:コレクション初期化子によって使用される拡張メソッドを作成して追加する (Visual Basic)'
title: '方法: コレクション初期化子によって使用される Add 拡張メソッドを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 1fbe6f438c4761ae668a6bd6a0a2c38c8efdb439
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475475"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="9cbe4-103">方法: コレクション初期化子によって使用される拡張メソッドを作成して追加する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cbe4-103">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="9cbe4-104">コレクション初期化子を使用してコレクションを作成すると、`Add` メソッドのパラメーターがコレクション初期化子の値の型と一致するコレクション型の `Add` メソッドが、Visual Basic コンパイラによって検索されます。</span><span class="sxs-lookup"><span data-stu-id="9cbe4-104">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="9cbe4-105">この `Add` メソッドは、コレクションに、コレクション初期化子の値を設定するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cbe4-105">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="9cbe4-106">一致する `Add` メソッドが存在せず、コレクションのコードを変更できない場合は、コレクション初期化子で必要なパラメーターを取る `Add` と呼ばれる拡張メソッドを追加できます。</span><span class="sxs-lookup"><span data-stu-id="9cbe4-106">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="9cbe4-107">この操作は、通常、コレクション初期化子をジェネリック コレクションに使用するときに行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cbe4-107">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cbe4-108">例</span><span class="sxs-lookup"><span data-stu-id="9cbe4-108">Example</span></span>  

 <span data-ttu-id="9cbe4-109">次の例では、コレクション初期化子を使用して `Employee` 型のオブジェクトを追加できるように、拡張メソッドをジェネリック <xref:System.Collections.Generic.List%601> 型に追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9cbe4-109">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="9cbe4-110">拡張メソッドを使用すると、短縮されたコレクション初期化子構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cbe4-110">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9cbe4-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cbe4-111">See also</span></span>

- [<span data-ttu-id="9cbe4-112">コレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="9cbe4-112">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="9cbe4-113">方法: コレクション初期化子によって使用されるコレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="9cbe4-113">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)
