---
description: '詳細情報: ジェネリック コレクションに対するインターフェイスでの変性の使用 (Visual Basic)'
title: ジェネリック コレクションに対するインターフェイスでの分散の使用
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: 9f98facbe1b89e468902384d2145fc5f91aae66a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100458981"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="5db82-103">ジェネリック コレクションに対するインターフェイスでの変性の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5db82-103">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>

<span data-ttu-id="5db82-104">共変のインターフェイスのメソッドでは、そのインターフェイスで指定された型よりも強い派生型を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="5db82-104">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="5db82-105">反変のインターフェイスのメソッドでは、そのインターフェイスで指定された型よりも弱い派生型のパラメーターを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="5db82-105">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>

<span data-ttu-id="5db82-106">.NET Framework 4 では、既存のいくつかのインターフェイスが共変および反変になります。</span><span class="sxs-lookup"><span data-stu-id="5db82-106">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="5db82-107">その中には、<xref:System.Collections.Generic.IEnumerable%601> や <xref:System.IComparable%601> があります。</span><span class="sxs-lookup"><span data-stu-id="5db82-107">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="5db82-108">これにより、派生型のコレクションに対して、基本型のジェネリック コレクションを操作するメソッドを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="5db82-108">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>

<span data-ttu-id="5db82-109">.NET Framework のバリアント インターフェイスの一覧については、「[ジェネリック インターフェイスの変性 (Visual Basic)](variance-in-generic-interfaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5db82-109">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md).</span></span>

## <a name="converting-generic-collections"></a><span data-ttu-id="5db82-110">ジェネリック コレクションの変換</span><span class="sxs-lookup"><span data-stu-id="5db82-110">Converting Generic Collections</span></span>

<span data-ttu-id="5db82-111">次の例は、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにおける共変性のサポートの利点を示しています。</span><span class="sxs-lookup"><span data-stu-id="5db82-111">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="5db82-112">`PrintFullName` メソッドは、パラメーターとして `IEnumerable(Of Person)` 型のコレクションを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5db82-112">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="5db82-113">ただし、`Employee` は `Person` を継承しているため、`IEnumerable(Of Person)` 型のコレクションで再利用できます。</span><span class="sxs-lookup"><span data-stu-id="5db82-113">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>

```vb
' Simple hierarchy of classes.
Public Class Person
    Public Property FirstName As String
    Public Property LastName As String
End Class

Public Class Employee
    Inherits Person
End Class

' The method has a parameter of the IEnumerable(Of Person) type.
Public Sub PrintFullName(ByVal persons As IEnumerable(Of Person))
    For Each person As Person In persons
        Console.WriteLine(
            "Name: " & person.FirstName & " " & person.LastName)
    Next
End Sub

Sub Main()
    Dim employees As IEnumerable(Of Employee) = New List(Of Employee)

    ' You can pass IEnumerable(Of Employee),
    ' although the method expects IEnumerable(Of Person).

    PrintFullName(employees)

End Sub
```

## <a name="comparing-generic-collections"></a><span data-ttu-id="5db82-114">ジェネリック コレクションの比較</span><span class="sxs-lookup"><span data-stu-id="5db82-114">Comparing Generic Collections</span></span>

<span data-ttu-id="5db82-115">次の例は、<xref:System.Collections.Generic.IComparer%601> インターフェイスにおける反変性のサポートの利点を示しています。</span><span class="sxs-lookup"><span data-stu-id="5db82-115">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="5db82-116">`PersonComparer` クラスは、`IComparer(Of Person)` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="5db82-116">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="5db82-117">ただし、`Employee` は `Person` を継承しているため、`Employee` 型の一連のオブジェクトを比較するためにこのクラスを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="5db82-117">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>

```vb
' Simple hierarchy of classes.
Public Class Person
    Public Property FirstName As String
    Public Property LastName As String
End Class

Public Class Employee
    Inherits Person
End Class
' The custom comparer for the Person type
' with standard implementations of Equals()
' and GetHashCode() methods.
Class PersonComparer
    Implements IEqualityComparer(Of Person)

    Public Function Equals1(
        ByVal x As Person,
        ByVal y As Person) As Boolean _
        Implements IEqualityComparer(Of Person).Equals

        If x Is y Then Return True
        If x Is Nothing OrElse y Is Nothing Then Return False
        Return (x.FirstName = y.FirstName) AndAlso
            (x.LastName = y.LastName)
    End Function
    Public Function GetHashCode1(
        ByVal person As Person) As Integer _
        Implements IEqualityComparer(Of Person).GetHashCode

        If person Is Nothing Then Return 0
        Dim hashFirstName =
            If(person.FirstName Is Nothing,
            0, person.FirstName.GetHashCode())
        Dim hashLastName = person.LastName.GetHashCode()
        Return hashFirstName Xor hashLastName
    End Function
End Class

Sub Main()
    Dim employees = New List(Of Employee) From {
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}
    }

    ' You can pass PersonComparer,
    ' which implements IEqualityComparer(Of Person),
    ' although the method expects IEqualityComparer(Of Employee)

    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())

    For Each employee In noduplicates
        Console.WriteLine(employee.FirstName & " " & employee.LastName)
    Next
End Sub
```

## <a name="see-also"></a><span data-ttu-id="5db82-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="5db82-118">See also</span></span>

- [<span data-ttu-id="5db82-119">ジェネリック インターフェイスの分散 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5db82-119">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)
