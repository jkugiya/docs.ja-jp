---
description: '詳細情報: 方法:アクセス レベルの組み合わせを使用してプロパティを宣言する (Visual Basic)'
title: '方法: 複数のアクセス レベルを持つプロパティを宣言する'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: e01849b0a590e499c1ee7b4a67d6aa794cd7cc5d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472463"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="3d3b0-103">方法: アクセス レベルの組み合わせを使用してプロパティを宣言する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d3b0-103">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>

<span data-ttu-id="3d3b0-104">プロパティに対する `Get` プロシージャと `Set` プロシージャに異なるアクセス レベルを設定する場合は、`Property` ステートメントで制限の少ないレベルを使用し、`Get` または `Set` ステートメントでより制限の厳しいレベルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-104">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="3d3b0-105">コードの特定の部分でプロパティの値を取得できるようにし、コードの他の特定の部分で値を変更できるようにする場合は、そのプロパティに対してアクセス レベルの組み合わせを使用します。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-105">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="3d3b0-106">アクセス レベルの詳細については、「[Access Levels in Visual Basic (Visual Basic でのアクセス レベル)](../declared-elements/access-levels.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-106">For more information on access levels, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="3d3b0-107">アクセス レベルの組み合わせを使用してプロパティを宣言するには</span><span class="sxs-lookup"><span data-stu-id="3d3b0-107">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="3d3b0-108">通常の方法でプロパティを宣言し、`Property` ステートメントで制限の少ないアクセス レベル (`Public` など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-108">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="3d3b0-109">より制限の厳しいアクセス レベル (`Friend` など) を指定して、`Get` または `Set` プロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-109">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="3d3b0-110">もう一方のプロパティ プロシージャではアクセス レベルを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-110">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="3d3b0-111">`Property` ステートメントで宣言されたアクセス レベルが想定されています。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-111">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="3d3b0-112">プロパティ プロシージャの 1 つでのみ、アクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-112">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="3d3b0-113">上記の例では、`Get` プロシージャにはプロパティ自体と同じ `Protected` アクセスが設定され、`Set` プロシージャには `Private` アクセスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-113">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="3d3b0-114">`employee` から派生したクラスは `salary` 値を読み取ることができますが、この値を設定できるのは `employee` クラスだけです。</span><span class="sxs-lookup"><span data-stu-id="3d3b0-114">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3b0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d3b0-115">See also</span></span>

- [<span data-ttu-id="3d3b0-116">手順</span><span class="sxs-lookup"><span data-stu-id="3d3b0-116">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3d3b0-117">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3d3b0-117">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="3d3b0-118">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="3d3b0-118">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3d3b0-119">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="3d3b0-119">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="3d3b0-120">Visual Basic のプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="3d3b0-120">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="3d3b0-121">方法: プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="3d3b0-121">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="3d3b0-122">方法: プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="3d3b0-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="3d3b0-123">方法: 既定のプロパティを宣言して呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d3b0-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="3d3b0-124">方法: プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="3d3b0-124">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="3d3b0-125">方法: プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="3d3b0-125">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
