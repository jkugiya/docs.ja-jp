---
description: '詳細情報: Default (Visual Basic)'
title: Default
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: fe135df4f29ae3c4064c97d4f2789be7f4f3d8f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774604"
---
# <a name="default-visual-basic"></a><span data-ttu-id="b5950-103">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5950-103">Default (Visual Basic)</span></span>

<span data-ttu-id="b5950-104">クラス、構造体、またはインターフェイスの既定のプロパティとしてプロパティを識別します。</span><span class="sxs-lookup"><span data-stu-id="b5950-104">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5950-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="b5950-105">Remarks</span></span>  

 <span data-ttu-id="b5950-106">プロパティが少なくとも 1 つのパラメーターを受け取る場合、クラス、構造体、またはインターフェイスは、そのプロパティの 1 つだけを *既定のプロパティ* として指定できます。</span><span class="sxs-lookup"><span data-stu-id="b5950-106">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="b5950-107">コードがメンバーを指定せずにクラスまたは構造体を参照する場合、Visual Basic はその参照を既定のプロパティに解決します。</span><span class="sxs-lookup"><span data-stu-id="b5950-107">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="b5950-108">既定のプロパティを使用すると、ソース コード文字が少し少なくなる可能性がありますが、コードが読みにくくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b5950-108">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="b5950-109">呼び出し元のコードがクラスまたは構造体をよく理解していない場合は、クラスまたは構造体の名前を参照するときに、その参照がクラスまたは構造体自体、または既定のプロパティにアクセスするかどうかがわかりません。</span><span class="sxs-lookup"><span data-stu-id="b5950-109">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="b5950-110">これにより、コンパイラ エラーや実行時の微妙なロジック エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b5950-110">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="b5950-111">常に [Option Strict ステートメント](../statements/option-strict-statement.md)を使用してコンパイラの型チェックを `On` に設定することにより、既定のプロパティ エラーが発生する可能性を多少減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="b5950-111">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="b5950-112">定義済みのクラスまたは構造体をコード内で使用する予定の場合は、既定のプロパティがあるかどうかと、ある場合はその名前を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5950-112">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="b5950-113">これらの欠点があるため、既定のプロパティを定義しないことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b5950-113">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="b5950-114">コードを読みやすくするためには、既定のプロパティを含め、常にすべてのプロパティを明示的に参照することも検討してください。</span><span class="sxs-lookup"><span data-stu-id="b5950-114">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="b5950-115">`Default` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5950-115">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b5950-116">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="b5950-116">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5950-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5950-117">See also</span></span>

- [<span data-ttu-id="b5950-118">方法: 既定のプロパティを宣言して呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5950-118">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="b5950-119">キーワード</span><span class="sxs-lookup"><span data-stu-id="b5950-119">Keywords</span></span>](../keywords/index.md)
