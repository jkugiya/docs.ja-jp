---
description: '詳細情報: 匿名型の定義 (Visual Basic)'
title: 匿名型の定義
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 2e3f847f5f844e3ed6e036c26efc330a237d193f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436917"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="96f24-103">匿名型の定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96f24-103">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="96f24-104">匿名型のインスタンスの宣言に応答して、コンパイラでは、型に対して指定されたプロパティを含む新しいクラス定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="96f24-104">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="96f24-105">コンパイラで生成されたコード</span><span class="sxs-lookup"><span data-stu-id="96f24-105">Compiler-Generated Code</span></span>

<span data-ttu-id="96f24-106">次の `product` の定義では、コンパイラで、`Name`、`Price`、および `OnHand` プロパティを含む新しいクラス定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="96f24-106">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="96f24-107">クラス定義には、次のようなプロパティ定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="96f24-107">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="96f24-108">キー プロパティに `Set` メソッドがないことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="96f24-108">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="96f24-109">キー プロパティの値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="96f24-109">The values of key properties are read-only.</span></span>

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

<span data-ttu-id="96f24-110">また、匿名型の定義には、パラメーターなしのコンストラクターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="96f24-110">In addition, anonymous type definitions contain a parameterless constructor.</span></span> <span data-ttu-id="96f24-111">パラメーターを必要とするコンストラクターは許可されません。</span><span class="sxs-lookup"><span data-stu-id="96f24-111">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="96f24-112">匿名型の定義に少なくとも 1 つのキー プロパティが含まれている場合は、<xref:System.Object> から継承された 3 つのメンバー (<xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A>、<xref:System.Object.ToString%2A>) がこの型定義でオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="96f24-112">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="96f24-113">キー プロパティが宣言されていない場合は、<xref:System.Object.ToString%2A> のみがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="96f24-113">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="96f24-114">オーバーライドでは次の機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="96f24-114">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="96f24-115">2 つの匿名型のインスタンスが同じインスタンスである場合、または次の条件を満たしている場合、`Equals` で `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="96f24-115">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="96f24-116">それらのプロパティの数が同じである。</span><span class="sxs-lookup"><span data-stu-id="96f24-116">They have the same number of properties.</span></span>

  - <span data-ttu-id="96f24-117">プロパティが同じ順序で宣言され、名前と推論された型が同じである。</span><span class="sxs-lookup"><span data-stu-id="96f24-117">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="96f24-118">名前の比較では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="96f24-118">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="96f24-119">少なくとも 1 つのプロパティがキー プロパティであり、`Key` キーワードが同じプロパティに適用されている。</span><span class="sxs-lookup"><span data-stu-id="96f24-119">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="96f24-120">キー プロパティの対応する各ペアの比較で、`True` が返される。</span><span class="sxs-lookup"><span data-stu-id="96f24-120">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="96f24-121">たとえば、次の例では、`Equals` で `employee01` と `employee08` に対してのみ `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="96f24-121">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="96f24-122">各行の前のコメントは、新しいインスタンスが `employee01` と一致しない理由を示しています。</span><span class="sxs-lookup"><span data-stu-id="96f24-122">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="96f24-123">`GetHashcode` では、適切な一意の GetHashCode アルゴリズムが提供されます。</span><span class="sxs-lookup"><span data-stu-id="96f24-123">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="96f24-124">このアルゴリズムでは、キー プロパティのみを使用してハッシュ コードを計算します。</span><span class="sxs-lookup"><span data-stu-id="96f24-124">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="96f24-125">`ToString` では、次の例に示すように、連結されたプロパティ値の文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="96f24-125">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="96f24-126">キーとキー以外のプロパティの両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="96f24-126">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="96f24-127">匿名型の明示的に名前が付けられたプロパティは、生成されたこれらのメソッドと競合できません。</span><span class="sxs-lookup"><span data-stu-id="96f24-127">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="96f24-128">つまり、`.Equals`、`.GetHashCode`、`.ToString` を使用してプロパティの名前を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="96f24-128">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="96f24-129">少なくとも 1 つのキー プロパティを含む匿名型定義では、<xref:System.IEquatable%601?displayProperty=nameWithType> インターフェイスも実装します。ここで、`T` は匿名型の型です。</span><span class="sxs-lookup"><span data-stu-id="96f24-129">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="96f24-130">匿名型の宣言では、同じアセンブリ内に存在する場合にのみ、同じ匿名型が作成され、そのプロパティの名前と推論される型は同じで、プロパティは同じ順序で宣言され、同じプロパティがキー プロパティとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="96f24-130">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="96f24-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="96f24-131">See also</span></span>

- [<span data-ttu-id="96f24-132">匿名型</span><span class="sxs-lookup"><span data-stu-id="96f24-132">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="96f24-133">方法: 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="96f24-133">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
