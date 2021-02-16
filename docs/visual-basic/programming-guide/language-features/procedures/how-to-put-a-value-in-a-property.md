---
description: '詳細情報: 方法:プロパティに値を格納する (Visual Basic)'
title: '方法: プロパティに値を格納する'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 62f5552f821fb98bd3a4695505aba5ff73b08fc7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476203"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="b2013-103">方法: プロパティに値を格納する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2013-103">How to: Put a Value in a Property (Visual Basic)</span></span>

<span data-ttu-id="b2013-104">プロパティに値を格納するには、代入ステートメントの左辺にプロパティ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b2013-104">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="b2013-105">プロパティの `Set` プロシージャによって値が格納されますが、名前で明示的に呼び出すことはありません。</span><span class="sxs-lookup"><span data-stu-id="b2013-105">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="b2013-106">変数を使用する場合と同様に、プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2013-106">You use the property just as you would use a variable.</span></span> <span data-ttu-id="b2013-107">Visual Basic によってプロパティのプロシージャが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b2013-107">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="b2013-108">プロパティに値を格納するには</span><span class="sxs-lookup"><span data-stu-id="b2013-108">To store a value in a property</span></span>  
  
1. <span data-ttu-id="b2013-109">代入ステートメントの左辺にプロパティ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="b2013-109">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="b2013-110">次の例では、`Set` プロシージャを暗黙的に呼び出して、Visual Basic の `TimeOfDay` プロパティの値を正午に設定します。</span><span class="sxs-lookup"><span data-stu-id="b2013-110">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="b2013-111">プロパティが引数を受け取る場合は、プロパティ名の後にかっこで囲んだ引数リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="b2013-111">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="b2013-112">引数がない場合は、必要に応じてかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="b2013-112">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="b2013-113">引数リストの引数をコンマで区切ってかっこ内に配置します。</span><span class="sxs-lookup"><span data-stu-id="b2013-113">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="b2013-114">プロパティで定義されている対応するパラメーターと同じ順序で引数を指定してください。</span><span class="sxs-lookup"><span data-stu-id="b2013-114">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="b2013-115">代入ステートメントの右辺で生成された値がプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b2013-115">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2013-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2013-116">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="b2013-117">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="b2013-117">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b2013-118">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="b2013-118">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b2013-119">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="b2013-119">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="b2013-120">Visual Basic のプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="b2013-120">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="b2013-121">方法: プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="b2013-121">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="b2013-122">方法: 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="b2013-122">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="b2013-123">方法: プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="b2013-123">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="b2013-124">方法: 既定のプロパティを宣言して呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2013-124">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="b2013-125">方法: プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="b2013-125">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
