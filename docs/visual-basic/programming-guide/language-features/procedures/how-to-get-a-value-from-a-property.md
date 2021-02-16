---
description: '詳細情報: 方法:プロパティから値を取得する (Visual Basic)'
title: '方法: プロパティから値を取得する'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5626ad1a248c3bb51e0f80076628c8108e424186
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427597"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="d4b34-103">方法: プロパティから値を取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4b34-103">How to: Get a Value from a Property (Visual Basic)</span></span>

<span data-ttu-id="d4b34-104">プロパティの値を取得するには、プロパティ名を式に含めます。</span><span class="sxs-lookup"><span data-stu-id="d4b34-104">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="d4b34-105">プロパティの `Get` プロシージャによって値が取得されますが、名前で明示的に呼び出すことはありません。</span><span class="sxs-lookup"><span data-stu-id="d4b34-105">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="d4b34-106">変数を使用する場合と同様に、プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d4b34-106">You use the property just as you would use a variable.</span></span> <span data-ttu-id="d4b34-107">Visual Basic によってプロパティのプロシージャが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d4b34-107">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="d4b34-108">プロパティから値を取得するには</span><span class="sxs-lookup"><span data-stu-id="d4b34-108">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="d4b34-109">式内のプロパティ名は、変数名を使用する場合と同じように使用します。</span><span class="sxs-lookup"><span data-stu-id="d4b34-109">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="d4b34-110">変数または定数を使用できる場所であればどこでもプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4b34-110">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="d4b34-111">\- または -</span><span class="sxs-lookup"><span data-stu-id="d4b34-111">-or-</span></span>  
  
     <span data-ttu-id="d4b34-112">代入ステートメント内で等号 (`=`) の後にプロパティ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="d4b34-112">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="d4b34-113">次の例では、Visual Basic `Now` プロパティの値を読み取り、その `Get` プロシージャを暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d4b34-113">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="d4b34-114">プロパティが引数を受け取る場合は、プロパティ名の後にかっこで囲んだ引数リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4b34-114">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d4b34-115">引数がない場合は、必要に応じてかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="d4b34-115">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="d4b34-116">引数リストの引数をコンマで区切ってかっこ内に配置します。</span><span class="sxs-lookup"><span data-stu-id="d4b34-116">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d4b34-117">プロパティで定義されている対応するパラメーターと同じ順序で引数を指定してください。</span><span class="sxs-lookup"><span data-stu-id="d4b34-117">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="d4b34-118">プロパティの値は変数または定数の場合と同様に式に含められるか、または代入ステートメントの左辺にある変数またはプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d4b34-118">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b34-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4b34-119">See also</span></span>

- [<span data-ttu-id="d4b34-120">手順</span><span class="sxs-lookup"><span data-stu-id="d4b34-120">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d4b34-121">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="d4b34-121">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="d4b34-122">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="d4b34-122">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d4b34-123">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="d4b34-123">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="d4b34-124">Visual Basic のプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="d4b34-124">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="d4b34-125">方法: プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="d4b34-125">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="d4b34-126">方法: 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="d4b34-126">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="d4b34-127">方法: プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="d4b34-127">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="d4b34-128">方法: 既定のプロパティを宣言して呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4b34-128">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="d4b34-129">方法: プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="d4b34-129">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
