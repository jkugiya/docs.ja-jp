---
title: 自動実装するプロパティ - C# プログラミング ガイド
description: C# の自動実装プロパティの場合、プロパティの get アクセサーと set アクセサーでのみアクセスできるプライベートの匿名バッキング フィールドがこのコンパイラによって作成されます。
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: ef3e2d6dd5851801ea06d65b87c2274d8e44b4f1
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190282"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="64a92-103">自動実装するプロパティ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="64a92-103">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="64a92-104">C# 3.0 以降では、自動実装プロパティを使用することで、プロパティ アクセサーに追加のロジックが必要ない場合は、プロパティをより簡潔に宣言できます。</span><span class="sxs-lookup"><span data-stu-id="64a92-104">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="64a92-105">これにより、クライアント コードでオブジェクトを作成することも可能になります。</span><span class="sxs-lookup"><span data-stu-id="64a92-105">They also enable client code to create objects.</span></span> <span data-ttu-id="64a92-106">次の例に示すようにプロパティを宣言する場合、コンパイラによって、プロパティの `get` および `set` アクセサーを介してのみアクセスできる、プライベートの匿名バッキング フィールドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="64a92-106">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span> <span data-ttu-id="64a92-107">C# 9 以降では、`init` アクセサーを自動実装プロパティとして宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="64a92-107">In C# 9 and later, `init` accessors can also be declared as auto-implemented properties.</span></span>
  
## <a name="example"></a><span data-ttu-id="64a92-108">例</span><span class="sxs-lookup"><span data-stu-id="64a92-108">Example</span></span>

<span data-ttu-id="64a92-109">次の例に、自動実装プロパティを持つ簡単なクラスを示します。</span><span class="sxs-lookup"><span data-stu-id="64a92-109">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="64a92-110">インターフェイスで自動実装プロパティを宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="64a92-110">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="64a92-111">自動実装プロパティでは、プライベートのインスタンス バッキング フィールドが宣言されます。インターフェイスでは、インスタンス フィールドを宣言できません。</span><span class="sxs-lookup"><span data-stu-id="64a92-111">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="64a92-112">本文を定義せずにインターフェイスでプロパティを宣言すると、アクセサーを利用してプロパティが宣言されますが、そのアクセサーは、そのインターフェイスを実装する型ごとに実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64a92-112">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="64a92-113">C# 6 以降では、フィールドと同様に自動実装プロパティを初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="64a92-113">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="64a92-114">前の例に示したクラスは、変更可能です。</span><span class="sxs-lookup"><span data-stu-id="64a92-114">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="64a92-115">クライアント コードでは、作成後、オブジェクト内の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="64a92-115">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="64a92-116">データだけでなく、重要な動作 (メソッド) も含まれる複雑なクラスでは、多くの場合、パブリック プロパティが必要です。</span><span class="sxs-lookup"><span data-stu-id="64a92-116">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="64a92-117">ただし、値のセット (データ) をカプセル化するだけで動作がほとんどまたはまったくない小さなクラスまたは構造体の場合は、次のいずれかのオプションを使用して、オブジェクトを変更不可にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="64a92-117">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should use one of the following options for making the objects immutable:</span></span>

* <span data-ttu-id="64a92-118">`get` アクセサーのみを宣言します (コンストラクター以外のすべての場所で変更できません)。</span><span class="sxs-lookup"><span data-stu-id="64a92-118">Declare only a `get` accessor (immutable everywhere except the constructor).</span></span>
* <span data-ttu-id="64a92-119">`get`アクセサーと `init` アクセサーを宣言します (オブジェクトの構築時を除き、すべての場所で変更できません)。</span><span class="sxs-lookup"><span data-stu-id="64a92-119">Declare a `get` accessor and an `init` accessor (immutable everywhere except during object construction).</span></span>
* <span data-ttu-id="64a92-120">`set` アクセサーを[プライベート](../../language-reference/keywords/private.md)として宣言します (コンシューマーには変更できません)。</span><span class="sxs-lookup"><span data-stu-id="64a92-120">Declare the `set` accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers).</span></span>

<span data-ttu-id="64a92-121">詳細については、「[自動実装するプロパティを使用して簡易クラスを実装する方法](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64a92-121">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64a92-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="64a92-122">See also</span></span>

- [<span data-ttu-id="64a92-123">プロパティ</span><span class="sxs-lookup"><span data-stu-id="64a92-123">Properties</span></span>](./properties.md)
- [<span data-ttu-id="64a92-124">修飾子</span><span class="sxs-lookup"><span data-stu-id="64a92-124">Modifiers</span></span>](../../language-reference/keywords/index.md)
