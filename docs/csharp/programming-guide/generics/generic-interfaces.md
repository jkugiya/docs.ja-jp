---
title: ジェネリック インターフェイス - C# プログラミング ガイド
description: C# でジェネリック インターフェイスを使用する方法について説明します。 コード例を参照し、使用可能なその他のリソースを確認してください。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 6089e14bd2b13268a03d3600ef8bf78f9afa1c6d
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206740"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="00ed1-104">ジェネリック インターフェイス (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="00ed1-104">Generic Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="00ed1-105">ジェネリック コレクション クラスのインターフェイスか、コレクション内の項目を表すジェネリック クラスのインターフェイスを定義すると、多くの場合、便利です。</span><span class="sxs-lookup"><span data-stu-id="00ed1-105">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="00ed1-106">ジェネリック クラスの優先設定の意図は、値型に対するボックス化とボックス化解除を回避する目的で、<xref:System.IComparable> ではなく <xref:System.IComparable%601> など、ジェネリック インターフェイスを利用することにあります。</span><span class="sxs-lookup"><span data-stu-id="00ed1-106">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="00ed1-107">.NET クラス ライブラリにより、<xref:System.Collections.Generic> 名前空間のコレクション クラスと共に利用するためのジェネリック インターフェイスがいくつか定義されます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-107">The .NET class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="00ed1-108">インターフェイスが型パラメーターの制約として指定される場合、インターフェイスを実装する型のみを利用できます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-108">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="00ed1-109">`GenericList<T>` クラスから派生する `SortedList<T>` クラスを示したのが次のコード サンプルです。</span><span class="sxs-lookup"><span data-stu-id="00ed1-109">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="00ed1-110">詳細については、「[ジェネリックの概要](./index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00ed1-110">For more information, see [Introduction to Generics](./index.md).</span></span> <span data-ttu-id="00ed1-111">`SortedList<T>` により制約 `where T : IComparable<T>` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-111">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="00ed1-112">これにより、`SortedList<T>` の `BubbleSort` メソッドは、一覧要素でジェネリック <xref:System.IComparable%601.CompareTo%2A> メソッドを利用できます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-112">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="00ed1-113">この例では、一覧要素は単純なクラスである `Person` です。これは `IComparable<Person>` を実装します。</span><span class="sxs-lookup"><span data-stu-id="00ed1-113">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="00ed1-114">次のように、複数のインターフェイスを単一の型で制約として指定できます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-114">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="00ed1-115">1 つのインターフェイスで、次のように、複数の型パラメーターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-115">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="00ed1-116">クラスに適用される継承規則は、インターフェイスにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-116">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="00ed1-117">ジェネリック インターフェイスが共変の場合、つまり、その型パラメーターを戻り値としてのみ利用する場合、ジェネリック インターフェイスは非ジェネリック インターフェイスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-117">Generic interfaces can inherit from non-generic interfaces if the generic interface is covariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="00ed1-118">.NET クラス ライブラリでは、<xref:System.Collections.Generic.IEnumerable%601> は <xref:System.Collections.IEnumerable> から継承します。これは、<xref:System.Collections.Generic.IEnumerable%601> が <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> の戻り値と <xref:System.Collections.Generic.IEnumerator%601.Current%2A> プロパティ ゲッターの `T` のみを利用するためです。</span><span class="sxs-lookup"><span data-stu-id="00ed1-118">In the .NET class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="00ed1-119">具象クラスは、次のように、構築されたクローズ型インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-119">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="00ed1-120">ジェネリック クラスは、クラス パラメーターの一覧からインターフェイスが必要とするすべての引数が提供される限り、ジェネリック インターフェイスや構築されたクローズ型インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="00ed1-120">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="00ed1-121">メソッドのオーバーロードを制御する規則は、ジェネリック クラス、ジェネリック構造体、ジェネリック インターフェイス内のメソッドの規則と同じです。</span><span class="sxs-lookup"><span data-stu-id="00ed1-121">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="00ed1-122">詳細については、「[ジェネリック メソッド](./generic-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00ed1-122">For more information, see [Generic Methods](./generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ed1-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="00ed1-123">See also</span></span>

- [<span data-ttu-id="00ed1-124">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="00ed1-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="00ed1-125">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="00ed1-125">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="00ed1-126">interface</span><span class="sxs-lookup"><span data-stu-id="00ed1-126">interface</span></span>](../../language-reference/keywords/interface.md)
- [<span data-ttu-id="00ed1-127">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="00ed1-127">Generics</span></span>](../../../standard/generics/index.md)
