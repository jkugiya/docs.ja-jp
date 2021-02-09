---
description: "詳細情報: BC32126:'System.Nullable(Of T)' のメソッドを 'AddressOf' 演算子のオペランドとして使用することはできません。"
title: "'System.Nullable(Of T)' のメソッドを 'AddressOf' 演算子のオペランドとして使用することはできません。"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 5ddf2f11bab3193423a3294a7f96afe68f0e5dce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795795"
---
# <a name="bc32126-methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="c88ec-103">BC32126:'System.Nullable(Of T)' のメソッドを 'AddressOf' 演算子のオペランドとして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c88ec-103">BC32126: Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>

<span data-ttu-id="c88ec-104">ステートメントで、<xref:System.Nullable%601> 構造のプロシージャを表すオペランドで、`AddressOf` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="c88ec-104">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>

 <span data-ttu-id="c88ec-105">**エラー ID:** BC32126</span><span class="sxs-lookup"><span data-stu-id="c88ec-105">**Error ID:** BC32126</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c88ec-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c88ec-106">To correct this error</span></span>

- <span data-ttu-id="c88ec-107">`AddressOf` 句のプロシージャ名を、<xref:System.Nullable%601> のメンバーではないオペランドに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c88ec-107">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>

- <span data-ttu-id="c88ec-108">使用する <xref:System.Nullable%601> のメソッドをラップするクラスを記述します。</span><span class="sxs-lookup"><span data-stu-id="c88ec-108">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="c88ec-109">次の例では、`NullableWrapper` クラスで `GetValueOrDefault` という名前の新しいメソッドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="c88ec-109">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="c88ec-110">この新しいメソッドは <xref:System.Nullable%601> のメンバーではないため、null 許容型のインスタンスである `nullInstance` に適用して `AddressOf` の引数を形成できます。</span><span class="sxs-lookup"><span data-stu-id="c88ec-110">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>

```vb
Module Module1

    Delegate Function Deleg() As Integer

    Sub Main()
        Dim nullInstance As New Nullable(Of Integer)(1)

        Dim del As Deleg

        ' GetValueOrDefault is a method of the Nullable generic
        ' type. It cannot be used as an operand of AddressOf.
        ' del = AddressOf nullInstance.GetValueOrDefault

        ' The following line uses the GetValueOrDefault method
        ' defined in the NullableWrapper class.
        del = AddressOf (New NullableWrapper(
            Of Integer)(nullInstance)).GetValueOrDefault

        Console.WriteLine(del.Invoke())
    End Sub

    Class NullableWrapper(Of T As Structure)
        Private m_Value As Nullable(Of T)

        Sub New(ByVal Value As Nullable(Of T))
            m_Value = Value
        End Sub

        Public Function GetValueOrDefault() As T
            Return m_Value.Value
        End Function
    End Class
End Module
```

## <a name="see-also"></a><span data-ttu-id="c88ec-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c88ec-111">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="c88ec-112">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="c88ec-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="c88ec-113">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="c88ec-113">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="c88ec-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c88ec-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
