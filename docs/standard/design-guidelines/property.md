---
description: '詳細情報: プロパティのデザイン'
title: プロパティのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: b2f776a5fb651f8b2e61b750a556704fa6c8c366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731800"
---
# <a name="property-design"></a><span data-ttu-id="1f171-103">プロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="1f171-103">Property Design</span></span>

<span data-ttu-id="1f171-104">プロパティは技術的にはメソッドとよく似ていますが、使用シナリオの観点からは非常に異なります。</span><span class="sxs-lookup"><span data-stu-id="1f171-104">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="1f171-105">それらは、スマートなフィールドと見なす必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f171-105">They should be seen as smart fields.</span></span> <span data-ttu-id="1f171-106">フィールドの呼び出し構文と、メソッドの柔軟性を備えています。</span><span class="sxs-lookup"><span data-stu-id="1f171-106">They have the calling syntax of fields, and the flexibility of methods.</span></span>

 <span data-ttu-id="1f171-107">✔️ 呼び出し元でプロパティの値を変更できないようにする必要がある場合は、取得専用プロパティを作成ます。</span><span class="sxs-lookup"><span data-stu-id="1f171-107">✔️ DO create get-only properties if the caller should not be able to change the value of the property.</span></span>

 <span data-ttu-id="1f171-108">プロパティの型が変更可能な参照型である場合は、プロパティが取得専用であっても、プロパティの値を変更できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1f171-108">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>

 <span data-ttu-id="1f171-109">❌ 設定専用のプロパティまたはセッターのあるプロパティに、ゲッターより広いアクセシビリティを提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="1f171-109">❌ DO NOT provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>

 <span data-ttu-id="1f171-110">たとえば、パブリック セッターとプロテクト ゲッターを持つプロパティは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1f171-110">For example, do not use properties with a public setter and a protected getter.</span></span>

 <span data-ttu-id="1f171-111">プロパティのゲッターを提供できない場合は、代わりにメソッドとして機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="1f171-111">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="1f171-112">そのメソッドの名前は、`Set` で始めて、その後にプロパティの名前を付けたものにすることを検討します。</span><span class="sxs-lookup"><span data-stu-id="1f171-112">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="1f171-113">たとえば、<xref:System.AppDomain> には、`CachePath` という名前の設定専用プロパティではなく、`SetCachePath` という名前のメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f171-113">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>

 <span data-ttu-id="1f171-114">✔️ すべてのプロパティに適切な既定値を提供し、既定値によってセキュリティ ホールや非常に非効率的なコードが発生しないようにします。</span><span class="sxs-lookup"><span data-stu-id="1f171-114">✔️ DO provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>

 <span data-ttu-id="1f171-115">✔️ オブジェクトが一時的に無効な状態になることがあっても、プロパティを任意の順序で設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1f171-115">✔️ DO allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>

 <span data-ttu-id="1f171-116">同じオブジェクトの他のプロパティの値により、あるプロパティの一部の値が無効になる可能性があるポイントに、複数のプロパティが相互に関連付けられているのはよくあることです。</span><span class="sxs-lookup"><span data-stu-id="1f171-116">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="1f171-117">そのような場合は、相互に関連するプロパティがオブジェクトによって実際にまとめて使用されるまで、無効な状態による例外を延期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f171-117">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>

 <span data-ttu-id="1f171-118">✔️ プロパティのセッターによって例外がスローされる場合は、前の値を保持します。</span><span class="sxs-lookup"><span data-stu-id="1f171-118">✔️ DO preserve the previous value if a property setter throws an exception.</span></span>

 <span data-ttu-id="1f171-119">❌ プロパティのゲッターからは例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="1f171-119">❌ AVOID throwing exceptions from property getters.</span></span>

 <span data-ttu-id="1f171-120">プロパティのゲッターは、単純な操作にして、いかなる前提条件も持たないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f171-120">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="1f171-121">ゲッターで例外がスローされる可能性がある場合は、メソッドとして再設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f171-121">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="1f171-122">このルールは、インデクサーには適用されないことに注意してください。そこでは、引数を検証した結果として、例外が発生することが予想されます。</span><span class="sxs-lookup"><span data-stu-id="1f171-122">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>

### <a name="indexed-property-design"></a><span data-ttu-id="1f171-123">インデックス付きプロパティの設計</span><span class="sxs-lookup"><span data-stu-id="1f171-123">Indexed Property Design</span></span>

 <span data-ttu-id="1f171-124">インデックス付きプロパティは、パラメーターを持つことができる特殊なプロパティであり、配列のインデックス指定に似た特殊な構文を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1f171-124">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>

 <span data-ttu-id="1f171-125">インデックス付きプロパティは、通常、インデクサーと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1f171-125">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="1f171-126">インデクサーは、論理コレクション内の項目へのアクセスを提供する API でのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f171-126">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="1f171-127">たとえば、文字列は文字のコレクションであり、その文字にアクセスするために <xref:System.String?displayProperty=nameWithType> にインデクサーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="1f171-127">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>

 <span data-ttu-id="1f171-128">✔️ 内部配列に格納されているデータへのアクセスを提供するには、インデクサーの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="1f171-128">✔️ CONSIDER using indexers to provide access to data stored in an internal array.</span></span>

 <span data-ttu-id="1f171-129">✔️ 項目のコレクションを表す型には、インデクサーを提供することを検討します。</span><span class="sxs-lookup"><span data-stu-id="1f171-129">✔️ CONSIDER providing indexers on types representing collections of items.</span></span>

 <span data-ttu-id="1f171-130">❌ 複数のパラメーターでインデックス付きプロパティを使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="1f171-130">❌ AVOID using indexed properties with more than one parameter.</span></span>

 <span data-ttu-id="1f171-131">設計で複数のパラメーターが必要な場合は、プロパティが論理コレクションへのアクセサーを実際に表しているかどうかを再検討します。</span><span class="sxs-lookup"><span data-stu-id="1f171-131">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="1f171-132">そうでない場合は、代わりにメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f171-132">If it does not, use methods instead.</span></span> <span data-ttu-id="1f171-133">そのメソッドの名前は、`Get` または `Set` で始めることを検討します。</span><span class="sxs-lookup"><span data-stu-id="1f171-133">Consider starting the method name with `Get` or `Set`.</span></span>

 <span data-ttu-id="1f171-134">❌ <xref:System.Int32?displayProperty=nameWithType>、<xref:System.Int64?displayProperty=nameWithType>、<xref:System.String?displayProperty=nameWithType>、<xref:System.Object?displayProperty=nameWithType>、または列挙型以外のパラメーターの型では、インデクサーを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1f171-134">❌ AVOID indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>

 <span data-ttu-id="1f171-135">設計で他の型のパラメーターが必要な場合は、API が論理コレクションへのアクセサーを実際に表しているかどうかを厳しく再評価します。</span><span class="sxs-lookup"><span data-stu-id="1f171-135">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="1f171-136">そうでない場合は、メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f171-136">If it does not, use a method.</span></span> <span data-ttu-id="1f171-137">そのメソッドの名前は、`Get` または `Set` で始めることを検討します。</span><span class="sxs-lookup"><span data-stu-id="1f171-137">Consider starting the method name with `Get` or `Set`.</span></span>

 <span data-ttu-id="1f171-138">✔️ 明らかにもっとよい名前がある場合を除き (たとえば、`System.String` の <xref:System.String.Chars%2A> プロパティを参照)、インデックス付きプロパティには `Item` という名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f171-138">✔️ DO use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>

 <span data-ttu-id="1f171-139">C# では、インデクサーは既定で Item という名前になります。</span><span class="sxs-lookup"><span data-stu-id="1f171-139">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="1f171-140"><xref:System.Runtime.CompilerServices.IndexerNameAttribute> を使用して、この名前をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="1f171-140">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>

 <span data-ttu-id="1f171-141">❌ セマンティクス的に同等であるインデクサーとメソッドの両方を提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="1f171-141">❌ DO NOT provide both an indexer and methods that are semantically equivalent.</span></span>

 <span data-ttu-id="1f171-142">❌ 1 つの型でオーバーロードされたインデクサーのファミリを複数提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="1f171-142">❌ DO NOT provide more than one family of overloaded indexers in one type.</span></span>

 <span data-ttu-id="1f171-143">これは、C# コンパイラによって強制されます。</span><span class="sxs-lookup"><span data-stu-id="1f171-143">This is enforced by the C# compiler.</span></span>

 <span data-ttu-id="1f171-144">❌ 既定以外のインデックス付きプロパティは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1f171-144">❌ DO NOT use nondefault indexed properties.</span></span>

 <span data-ttu-id="1f171-145">これは、C# コンパイラによって強制されます。</span><span class="sxs-lookup"><span data-stu-id="1f171-145">This is enforced by the C# compiler.</span></span>

### <a name="property-change-notification-events"></a><span data-ttu-id="1f171-146">プロパティ変更通知イベント</span><span class="sxs-lookup"><span data-stu-id="1f171-146">Property Change Notification Events</span></span>

 <span data-ttu-id="1f171-147">場合によっては、プロパティ値の変更をユーザーに通知するイベントを提供すると便利です。</span><span class="sxs-lookup"><span data-stu-id="1f171-147">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="1f171-148">たとえば、`Text` プロパティの値が変更された後で、`System.Windows.Forms.Control` から `TextChanged` イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="1f171-148">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>

 <span data-ttu-id="1f171-149">✔️ 高レベルの API (通常はデザイナー コンポーネント) のプロパティ値が変更されたら、変更通知イベントを発生させることを検討します。</span><span class="sxs-lookup"><span data-stu-id="1f171-149">✔️ CONSIDER raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>

 <span data-ttu-id="1f171-150">オブジェクトのプロパティが変更されたことをユーザーが知るための適切なシナリオがある場合、オブジェクトでプロパティの変更通知イベントを発生させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f171-150">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>

 <span data-ttu-id="1f171-151">ただし、基本データ型やコレクションなどの低レベルの API については、そのようなイベントを発生させるオーバーヘッドに価値があることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="1f171-151">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="1f171-152">たとえば、新しい項目がリストに追加されて、`Count` プロパティが変更されたときでも、<xref:System.Collections.Generic.List%601> からはそのようなイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="1f171-152">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>

 <span data-ttu-id="1f171-153">✔️ プロパティの値が外部からの強制によって変更された場合は、変更通知イベントを発生させることを検討します。</span><span class="sxs-lookup"><span data-stu-id="1f171-153">✔️ CONSIDER raising change notification events when the value of a property changes via external forces.</span></span>

 <span data-ttu-id="1f171-154">プロパティ値が何らかの外部強制 (オブジェクトのメソッドを呼び出す以外の方法) によって変更された場合、イベントの発生は、値が変更されていること、および変更されたことを開発者に示します。</span><span class="sxs-lookup"><span data-stu-id="1f171-154">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="1f171-155">テキスト ボックス コントロールの `Text` プロパティがよい例です。</span><span class="sxs-lookup"><span data-stu-id="1f171-155">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="1f171-156">ユーザーが `TextBox` にテキストを入力すると、プロパティ値が自動的に変更されます。</span><span class="sxs-lookup"><span data-stu-id="1f171-156">When the user types text in a `TextBox`, the property value automatically changes.</span></span>

 <span data-ttu-id="1f171-157">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="1f171-157">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1f171-158">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="1f171-158">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1f171-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f171-159">See also</span></span>

- [<span data-ttu-id="1f171-160">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="1f171-160">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="1f171-161">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="1f171-161">Framework Design Guidelines</span></span>](index.md)
