---
description: '詳細情報: 拡張メソッド'
title: 拡張メソッド
ms.date: 10/22/2008
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 2f71ec86252045687558bd61337164ac3afbcd20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642059"
---
# <a name="extension-methods"></a><span data-ttu-id="395f3-103">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="395f3-103">Extension Methods</span></span>

<span data-ttu-id="395f3-104">拡張メソッドは、インスタンス メソッド呼び出し構文を使用して静的メソッドを呼び出せるようにする言語機能です。</span><span class="sxs-lookup"><span data-stu-id="395f3-104">Extension methods are a language feature that allows static methods to be called using instance method call syntax.</span></span> <span data-ttu-id="395f3-105">これらのメソッドでは、メソッドで操作されるインスタンスを表す 1 つ以上のパラメーターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="395f3-105">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>

 <span data-ttu-id="395f3-106">このような拡張メソッドを定義するクラスは "スポンサー" クラスと呼ばれ、静的クラスとして宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="395f3-106">The class that defines such extension methods is referred to as the "sponsor" class, and it must be declared as static.</span></span> <span data-ttu-id="395f3-107">拡張メソッドを使用するには、スポンサー クラスを定義する名前空間をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="395f3-107">To use extension methods, one must import the namespace defining the sponsor class.</span></span>

 <span data-ttu-id="395f3-108">❌ 拡張メソッドをむやみに定義することは避けてください。これは自分が所有していない型に対して特に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="395f3-108">❌ AVOID frivolously defining extension methods, especially on types you don't own.</span></span>

 <span data-ttu-id="395f3-109">型のソース コードを所有している場合は、代わりに通常のインスタンス メソッドを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="395f3-109">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="395f3-110">所有していないときにメソッドを追加する場合は、細心の注意を払ってください。</span><span class="sxs-lookup"><span data-stu-id="395f3-110">If you don't own, and you want to add a method, be very careful.</span></span> <span data-ttu-id="395f3-111">拡張メソッドを自由に使用すると、それらのメソッドを使用するように設計されていなかった種類の API が乱雑になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="395f3-111">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>

 <span data-ttu-id="395f3-112">✔️ 次のシナリオのいずれかに該当する場合に拡張メソッドの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="395f3-112">✔️ CONSIDER using extension methods in any of the following scenarios:</span></span>

- <span data-ttu-id="395f3-113">インターフェイスのすべての実装に関連するヘルパー機能をコア インターフェイスの観点から記述できる場合に、その機能を提供するため。</span><span class="sxs-lookup"><span data-stu-id="395f3-113">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="395f3-114">これは、それ以外の方法では、明確な実装をインターフェイスに割り当てることができないことが理由です。</span><span class="sxs-lookup"><span data-stu-id="395f3-114">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="395f3-115">たとえば、`LINQ to Objects` 演算子は、すべての <xref:System.Collections.Generic.IEnumerable%601> 型の拡張メソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="395f3-115">For example, the `LINQ to Objects` operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="395f3-116">したがって、すべての `IEnumerable<>` の実装は、自動的に LINQ 対応になります。</span><span class="sxs-lookup"><span data-stu-id="395f3-116">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>

- <span data-ttu-id="395f3-117">インスタンス メソッドによって何らかの種類の依存関係が発生するが、そのような依存関係は依存関係管理規則に違反する場合。</span><span class="sxs-lookup"><span data-stu-id="395f3-117">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="395f3-118">たとえば、<xref:System.String> から <xref:System.Uri?displayProperty=nameWithType> への依存関係はおそらく望ましいものではないため、`System.Uri` を返す `String.ToUri()` インスタンス メソッドは、依存関係管理の観点からは不適切な設計になります。</span><span class="sxs-lookup"><span data-stu-id="395f3-118">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="395f3-119">`System.Uri` を返す静的な拡張メソッド `Uri.ToUri(this string str)` のほうが、はるかに優れた設計です。</span><span class="sxs-lookup"><span data-stu-id="395f3-119">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>

 <span data-ttu-id="395f3-120">❌ <xref:System.Object?displayProperty=nameWithType> に拡張メソッドを定義することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="395f3-120">❌ AVOID defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="395f3-121">VB ユーザーは、拡張メソッドの構文を使用して、オブジェクト参照に対してそのようなメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="395f3-121">VB users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="395f3-122">VB では、このようなメソッドの呼び出しはサポートされていません。理由は、VB では、参照をオブジェクトとして宣言すると、それに対するすべてのメソッド呼び出しは遅延バインディングされます (呼び出される実際のメンバーは実行時に決定されます) が、拡張メソッドへのバインドはコンパイル時に決定 (事前バインディング) されるためです。</span><span class="sxs-lookup"><span data-stu-id="395f3-122">VB does not support calling such methods because, in VB, declaring a reference as Object forces all method invocations on it to be late bound (actual member called is determined at runtime), while bindings to extension methods are determined at compile-time (early bound).</span></span>

 <span data-ttu-id="395f3-123">このガイドラインは、同じバインディング動作が存在する、または拡張メソッドがサポートされていない他の言語にも適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="395f3-123">Note that the guideline applies to other languages where the same binding behavior is present, or where extension methods are not supported.</span></span>

 <span data-ttu-id="395f3-124">❌ メソッドをインターフェイスに追加する、または依存関係を管理することが目的でない限り、拡張メソッドを拡張型と同じ名前空間に配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="395f3-124">❌ DO NOT put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>

 <span data-ttu-id="395f3-125">❌ 異なる名前空間に存在する場合でも、同じシグネチャを持つ 2 つ以上の拡張メソッドを定義することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="395f3-125">❌ AVOID defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>

 <span data-ttu-id="395f3-126">✔️ 型がインターフェイスであり、ほとんどまたはすべてのケースで拡張メソッドを使用することを意図している場合は、拡張型と同じ名前空間に拡張メソッドを定義することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="395f3-126">✔️ CONSIDER defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>

 <span data-ttu-id="395f3-127">❌ 通常は他の機能に関連付けられている名前空間内に、機能を実装する拡張メソッドを定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="395f3-127">❌ DO NOT define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="395f3-128">代わりに、それらが属する機能に関連付けられている名前空間内に定義してください。</span><span class="sxs-lookup"><span data-stu-id="395f3-128">Instead, define them in the namespace associated with the feature they belong to.</span></span>

 <span data-ttu-id="395f3-129">❌ 拡張メソッド専用の名前空間の汎用的な名前付け ("Extensions" など) は避けてください。</span><span class="sxs-lookup"><span data-stu-id="395f3-129">❌ AVOID generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="395f3-130">代わりに、わかりやすい名前 ("Routing" など) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="395f3-130">Use a descriptive name (e.g., "Routing") instead.</span></span>

 <span data-ttu-id="395f3-131">*Portions &copy; 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="395f3-131">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="395f3-132">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="395f3-132">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="395f3-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="395f3-133">See also</span></span>

- [<span data-ttu-id="395f3-134">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="395f3-134">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="395f3-135">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="395f3-135">Framework Design Guidelines</span></span>](index.md)
