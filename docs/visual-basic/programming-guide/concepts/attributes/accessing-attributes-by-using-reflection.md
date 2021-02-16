---
description: '詳細情報: リフレクションを使用した属性へのアクセス (Visual Basic)'
title: リフレクションを使用した属性へのアクセス
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: e585bb427456f1187eaf8c39937eaa67651d9309
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437866"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="83363-103">リフレクションを使用した属性へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83363-103">Accessing Attributes by Using Reflection (Visual Basic)</span></span>

<span data-ttu-id="83363-104">カスタム属性を定義し、それらをソース コード内に配置することができても、その情報を取得して操作する手段がなければ、ほとんど価値はありません。</span><span class="sxs-lookup"><span data-stu-id="83363-104">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="83363-105">リフレクションを使用すれば、カスタム属性を使用して定義された情報を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="83363-105">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="83363-106">鍵となるメソッドは `GetCustomAttributes` です。このメソッドは、ソース コード属性の実行時の等価オブジェクトを配列で返します。</span><span class="sxs-lookup"><span data-stu-id="83363-106">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="83363-107">このメソッドには、いくつかのオーバー ロード バージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="83363-107">This method has several overloaded versions.</span></span> <span data-ttu-id="83363-108">詳細については、「<xref:System.Attribute>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83363-108">For more information, see <xref:System.Attribute>.</span></span>

<span data-ttu-id="83363-109">次のような属性指定は、</span><span class="sxs-lookup"><span data-stu-id="83363-109">An attribute specification such as:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 <span data-ttu-id="83363-110">概念的には次の記述と同じです。</span><span class="sxs-lookup"><span data-stu-id="83363-110">is conceptually equivalent to this:</span></span>

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

<span data-ttu-id="83363-111">ただし、属性について `SampleClass` が照会されるまで、コードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="83363-111">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="83363-112">`SampleClass` について `GetCustomAttributes` を呼び出すと、`Author` オブジェクトが作成され、上記のように初期化されます。</span><span class="sxs-lookup"><span data-stu-id="83363-112">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="83363-113">クラスに他の属性がある場合は、他の属性オブジェクトも同様に作成されます。</span><span class="sxs-lookup"><span data-stu-id="83363-113">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="83363-114">`GetCustomAttributes` はその後、`Author` オブジェクトと配列内の他の属性オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="83363-114">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="83363-115">その後、この配列を反復処理し、各配列要素の型に基づいてどの属性が適用されたかを確認して、属性オブジェクトから情報を抽出することができます。</span><span class="sxs-lookup"><span data-stu-id="83363-115">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>

## <a name="example"></a><span data-ttu-id="83363-116">例</span><span class="sxs-lookup"><span data-stu-id="83363-116">Example</span></span>

<span data-ttu-id="83363-117">完全な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="83363-117">Here is a complete example.</span></span> <span data-ttu-id="83363-118">カスタム属性が定義され、複数のエンティティに適用された後、リフレクションを使用して取得されています。</span><span class="sxs-lookup"><span data-stu-id="83363-118">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>

```vb
' Multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName

        ' Default value
        version = 1.0
    End Sub

    Function GetName() As String
        Return name
    End Function
End Class

' Class with the Author attribute
<Author("P. Ackerman")>
Public Class FirstClass
End Class

' Class without the Author attribute
Public Class SecondClass
End Class

' Class with multiple Author attributes.
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>
Public Class ThirdClass
End Class

Class TestAuthorAttribute
    Sub Main()
        PrintAuthorInfo(GetType(FirstClass))
        PrintAuthorInfo(GetType(SecondClass))
        PrintAuthorInfo(GetType(ThirdClass))
    End Sub

    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)
        System.Console.WriteLine("Author information for {0}", t)

        ' Using reflection
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)

        ' Displaying output
        For Each attr In attrs
            Dim a As Author = CType(attr, Author)
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)
        Next
    End Sub

    ' Output:
    '   Author information for FirstClass
    '     P. Ackerman, version 1.00
    ' Author information for SecondClass
    ' Author information for ThirdClass
    '  R. Koch, version 2.00
    '  P. Ackerman, version 1.00

End Class
```

## <a name="see-also"></a><span data-ttu-id="83363-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="83363-119">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="83363-120">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="83363-120">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="83363-121">属性に格納されている情報の取得</span><span class="sxs-lookup"><span data-stu-id="83363-121">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="83363-122">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83363-122">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="83363-123">属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83363-123">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="83363-124">カスタム属性の作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83363-124">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
