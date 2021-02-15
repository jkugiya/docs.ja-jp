---
description: "詳細情報: BC42026:式は、含んでいるプロパティ '<propertyname>' を再帰的に呼び出します"
title: 式は、含んでいるプロパティ '<propertyname>' を再帰的に呼び出します。
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 4b6abcbab62ae0c4c5b18b0e6946bcfb21857112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796341"
---
# <a name="bc42026-expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="04e5f-103">BC42026:式は、含んでいるプロパティ '\<propertyname>' を再帰的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="04e5f-103">BC42026: Expression recursively calls the containing property '\<propertyname>'</span></span>

<span data-ttu-id="04e5f-104">プロパティ定義の `Set` プロシージャ内のステートメントは、プロパティの名前に値を格納します。</span><span class="sxs-lookup"><span data-stu-id="04e5f-104">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>

 <span data-ttu-id="04e5f-105">プロパティの値を保持するために推奨される方法は、プロパティのコンテナーで `Private` 変数を定義し、それを `Get` と `Set` の両方のプロシージャで使用することです。</span><span class="sxs-lookup"><span data-stu-id="04e5f-105">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="04e5f-106">`Set` プロシージャは、この `Private` 変数に受け取った値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04e5f-106">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>

 <span data-ttu-id="04e5f-107">`Get` プロシージャは `Function` プロシージャと同じように動作するため、プロパティ名に値を代入し、`End Get` ステートメントに遭遇することで制御を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="04e5f-107">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="04e5f-108">ただし、推奨される方法は、[Return ステートメント](../statements/return-statement.md)に値として `Private` 変数を含めることです。</span><span class="sxs-lookup"><span data-stu-id="04e5f-108">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../statements/return-statement.md).</span></span>

 <span data-ttu-id="04e5f-109">`Set` プロシージャは、値を返さない `Sub` プロシージャと同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="04e5f-109">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="04e5f-110">そのため、プロシージャまたはプロパティの名前は `Set` プロシージャ内で特別な意味を持たず、値を格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="04e5f-110">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>

 <span data-ttu-id="04e5f-111">次の例では、このエラーの原因となる可能性がある方法と、その後に推奨される方法を示します。</span><span class="sxs-lookup"><span data-stu-id="04e5f-111">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>

```vb
Public Class illustrateProperties
' The code in the following property causes this error.
    Public Property badProp() As Char
        Get
            Dim charValue As Char
            ' Insert code to update charValue.
            badProp = charValue
        End Get
        Set(ByVal Value As Char)
            ' The following statement causes this error.
            badProp = Value
            ' The value stored in the local variable badProp
            ' is not used by the Get procedure in this property.
        End Set
    End Property
' The following code uses the recommended approach.
    Private propValue As Char
    Public Property goodProp() As Char
        Get
            ' Insert code to update propValue.
            Return propValue
        End Get
        Set(ByVal Value As Char)
            propValue = Value
        End Set
    End Property
End Class
```

 <span data-ttu-id="04e5f-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="04e5f-112">By default, this message is a warning.</span></span> <span data-ttu-id="04e5f-113">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04e5f-113">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="04e5f-114">**エラー ID:** BC42026</span><span class="sxs-lookup"><span data-stu-id="04e5f-114">**Error ID:** BC42026</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="04e5f-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="04e5f-115">To correct this error</span></span>

- <span data-ttu-id="04e5f-116">前の例に示されているように、推奨される方法を使用するようにプロパティ定義を書き直してください。</span><span class="sxs-lookup"><span data-stu-id="04e5f-116">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>

## <a name="see-also"></a><span data-ttu-id="04e5f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="04e5f-117">See also</span></span>

- [<span data-ttu-id="04e5f-118">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="04e5f-118">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="04e5f-119">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="04e5f-119">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="04e5f-120">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="04e5f-120">Set Statement</span></span>](../statements/set-statement.md)
