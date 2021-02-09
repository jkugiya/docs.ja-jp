---
description: "詳細情報: BC42107:プロパティ '<propertyname>' は、すべてのコードのパスでは値を返しません。"
title: プロパティ '<propertyname>' は、すべてのコードのパスでは値を返しません。
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 9aa0d6fea1feeaf7503f5f8831fbd3de910a4822
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774890"
---
# <a name="bc42107-property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="e676b-103">BC42107:プロパティ '\<propertyname>' は、すべてのコードのパスでは値を返しません。</span><span class="sxs-lookup"><span data-stu-id="e676b-103">BC42107: Property '\<propertyname>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="e676b-104">プロパティ '\<propertyname>' は、すべてのコードのパスでは値を返しません。</span><span class="sxs-lookup"><span data-stu-id="e676b-104">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="e676b-105">この結果が使用されると、実行時に Null 参照例外が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e676b-105">A null reference exception could occur at run time when the result is used.</span></span>

<span data-ttu-id="e676b-106">プロパティ `Get` プロシージャのコードには、値を返さないパスが少なくとも 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="e676b-106">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="e676b-107">次のいずれかの方法で、プロパティ `Get` プロシージャから値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e676b-107">You can return a value from a property `Get` procedure in any of the following ways:</span></span>

- <span data-ttu-id="e676b-108">プロパティ名に値を代入して、`Exit Property` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e676b-108">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>

- <span data-ttu-id="e676b-109">プロパティ名に値を代入して、`End Get` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e676b-109">Assign the value to the property name and then perform the `End Get` statement.</span></span>

- <span data-ttu-id="e676b-110">[return ステートメント](../statements/return-statement.md)に値を含めます。</span><span class="sxs-lookup"><span data-stu-id="e676b-110">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

<span data-ttu-id="e676b-111">制御が `Exit Property` または `End Get` に渡され、プロパティ名に何も値を代入していない場合、`Get` プロシージャでは、プロパティのデータ型の既定値が返されます。</span><span class="sxs-lookup"><span data-stu-id="e676b-111">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="e676b-112">詳細については、「[Function ステートメント](../statements/function-statement.md)」の "動作" に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e676b-112">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

<span data-ttu-id="e676b-113">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="e676b-113">By default, this message is a warning.</span></span> <span data-ttu-id="e676b-114">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e676b-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="e676b-115">**エラー ID:** BC42107</span><span class="sxs-lookup"><span data-stu-id="e676b-115">**Error ID:** BC42107</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e676b-116">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e676b-116">To correct this error</span></span>

- <span data-ttu-id="e676b-117">制御フロー ロジックをチェックし、戻り値を返すすべてのステートメントの前に値を代入してください。</span><span class="sxs-lookup"><span data-stu-id="e676b-117">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

  <span data-ttu-id="e676b-118">常に `Return` ステートメントを使用すれば、プロシージャからのすべての戻り値で、値が返されることを簡単に保証できます。</span><span class="sxs-lookup"><span data-stu-id="e676b-118">It's easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="e676b-119">これを実行する場合、`End Get` の前の最後のステートメントは、`Return` ステートメントでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="e676b-119">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="e676b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e676b-120">See also</span></span>

- [<span data-ttu-id="e676b-121">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e676b-121">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="e676b-122">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="e676b-122">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="e676b-123">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="e676b-123">Get Statement</span></span>](../statements/get-statement.md)
