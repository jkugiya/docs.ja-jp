---
description: '詳細情報: Func および Action 汎用デリゲートでの変性の使用 (Visual Basic)'
title: Func および Action 汎用デリゲートでの分散の使用
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: 4a445d9ad1cf1bd6ca6e13bdd2e40545c6b28fe8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485238"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="8e037-103">Func および Action 汎用デリゲートでの変性の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e037-103">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>

<span data-ttu-id="8e037-104">以下の例では、`Func` 汎用デリゲートと `Action` 汎用デリゲートの共変性と反変性を使用して、メソッドの再利用を可能にし、コードの柔軟性を高める方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8e037-104">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>

<span data-ttu-id="8e037-105">共変性と反変性の詳細については、「[デリゲートの変性 (Visual Basic)](variance-in-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e037-105">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="8e037-106">デリゲートと共変の型パラメーターの使用</span><span class="sxs-lookup"><span data-stu-id="8e037-106">Using Delegates with Covariant Type Parameters</span></span>

<span data-ttu-id="8e037-107">次の例は、`Func` 汎用デリゲートにおける共変性のサポートの利点を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e037-107">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="8e037-108">`FindByTitle` メソッドは、`String` 型のパラメーターを受け取り、`Employee` 型のオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="8e037-108">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="8e037-109">ただし、このメソッドは `Func(Of String, Person)` デリゲートに割り当てることもできます。これは `Employee` が `Person` を継承するためです。</span><span class="sxs-lookup"><span data-stu-id="8e037-109">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>

```vb
' Simple hierarchy of classes.
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class Finder
    Public Shared Function FindByTitle(
        ByVal title As String) As Employee
        ' This is a stub for a method that returns
        ' an employee that has the specified title.
        Return New Employee
    End Function

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim findEmployee As Func(Of String, Employee) =
            AddressOf FindByTitle

        ' The delegate expects a method to return Person,
        ' but you can assign it a method that returns Employee.
        Dim findPerson As Func(Of String, Person) =
            AddressOf FindByTitle

        ' You can also assign a delegate
        ' that returns a more derived type to a delegate
        ' that returns a less derived type.
        findPerson = findEmployee
    End Sub
End Class
```

## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="8e037-110">デリゲートと反変の型パラメーターの使用</span><span class="sxs-lookup"><span data-stu-id="8e037-110">Using Delegates with Contravariant Type Parameters</span></span>

<span data-ttu-id="8e037-111">次の例は、`Action` 汎用デリゲートにおける反変性のサポートの利点を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e037-111">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="8e037-112">`AddToContacts` メソッドは、`Person` 型のパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="8e037-112">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="8e037-113">ただし、このメソッドは `Action(Of Employee)` デリゲートに割り当てることもできます。これは `Employee` が `Person` を継承するためです。</span><span class="sxs-lookup"><span data-stu-id="8e037-113">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>

```vb
Public Class Person
End Class

Public Class Employee
    Inherits Person
End Class

Class AddressBook
    Shared Sub AddToContacts(ByVal person As Person)
        ' This method adds a Person object
        ' to a contact list.
    End Sub

    Sub Test()
        ' Create an instance of the delegate without using variance.
        Dim addPersonToContacts As Action(Of Person) =
            AddressOf AddToContacts

        ' The Action delegate expects
        ' a method that has an Employee parameter,
        ' but you can assign it a method that has a Person parameter
        ' because Employee derives from Person.
        Dim addEmployeeToContacts As Action(Of Employee) =
            AddressOf AddToContacts

        ' You can also assign a delegate
        ' that accepts a less derived parameter
        ' to a delegate that accepts a more derived parameter.
        addEmployeeToContacts = addPersonToContacts
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="8e037-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e037-114">See also</span></span>

- [<span data-ttu-id="8e037-115">共変性と反変性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e037-115">Covariance and Contravariance (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="8e037-116">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="8e037-116">Generics</span></span>](../../../../standard/generics/index.md)
