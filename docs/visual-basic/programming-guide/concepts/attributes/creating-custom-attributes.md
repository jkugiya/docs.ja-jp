---
description: '詳細情報: カスタム属性の作成 (Visual Basic)'
title: カスタム属性の作成
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: e989a4ce219609aafcec90d12f9d460681e98be9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437775"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="4b12a-103">カスタム属性の作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b12a-103">Creating Custom Attributes (Visual Basic)</span></span>

<span data-ttu-id="4b12a-104">属性クラスを定義することで、独自のカスタム属性を作成できます。属性クラスは、<xref:System.Attribute> の直接的または間接的な派生クラスです。これにより、メタデータの中で属性の定義をすばやく簡単に特定できます。</span><span class="sxs-lookup"><span data-stu-id="4b12a-104">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="4b12a-105">型にそれを記述したプログラマーの名前でタグを付けるとします。</span><span class="sxs-lookup"><span data-stu-id="4b12a-105">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="4b12a-106">`Author` というカスタム属性クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="4b12a-106">You might define a custom `Author` attribute class:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName
        version = 1.0
    End Sub
End Class
```

<span data-ttu-id="4b12a-107">クラス名は属性の名前の `Author` です。</span><span class="sxs-lookup"><span data-stu-id="4b12a-107">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="4b12a-108">このクラスは `System.Attribute` から派生しているので、カスタム属性クラスです。</span><span class="sxs-lookup"><span data-stu-id="4b12a-108">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="4b12a-109">コンストラクターのパラメーターはカスタム属性の位置指定パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="4b12a-109">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="4b12a-110">この例では、`name` が位置指定パラメーターになります。</span><span class="sxs-lookup"><span data-stu-id="4b12a-110">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="4b12a-111">パブリックな読み取り/書き込みフィールドまたはプロパティは名前付きパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="4b12a-111">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="4b12a-112">この場合は、`version` が唯一の名前付きパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="4b12a-112">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="4b12a-113">`AttributeUsage` 属性を使用して、クラスと `Structure` の宣言に対してのみ `Author` 属性を有効にしていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4b12a-113">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>

<span data-ttu-id="4b12a-114">この新しい属性の使用方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4b12a-114">You could use this new attribute as follows:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

<span data-ttu-id="4b12a-115">`AttributeUsage` には名前付きパラメーター `AllowMultiple` があります。これを使用すると、カスタム属性が 1 回しか指定できない属性か、または複数回指定できる属性かを設定できます。</span><span class="sxs-lookup"><span data-stu-id="4b12a-115">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="4b12a-116">次のコード例では、複数回指定できる属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4b12a-116">In the following code example, a multiuse attribute is created.</span></span>

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

<span data-ttu-id="4b12a-117">次のコード例では、同じ型の複数の属性が 1 つのクラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="4b12a-117">In the following code example, multiple attributes of the same type are applied to a class.</span></span>

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> <span data-ttu-id="4b12a-118">属性クラスにプロパティが含まれている場合、そのプロパティは読み取り/書き込み可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b12a-118">If your attribute class contains a property, that property must be read-write.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b12a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b12a-119">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="4b12a-120">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="4b12a-120">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="4b12a-121">カスタム属性の記述</span><span class="sxs-lookup"><span data-stu-id="4b12a-121">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="4b12a-122">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b12a-122">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="4b12a-123">属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b12a-123">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="4b12a-124">リフレクションを使用した属性へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b12a-124">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="4b12a-125">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b12a-125">AttributeUsage (Visual Basic)</span></span>](attributeusage.md)
