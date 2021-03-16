---
description: '詳細情報: 例外とパフォーマンス'
title: 例外とパフォーマンス
ms.date: 10/22/2008
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: 72b35ccca5514e56dcc04fc0a07d1f9887c4a2f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642124"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="5ebd1-103">例外とパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="5ebd1-103">Exceptions and Performance</span></span>

<span data-ttu-id="5ebd1-104">例外に関する一般的な懸念の 1 つとして、日常的に失敗するコードに例外を使用すると、実装のパフォーマンスが許容できないものになるだろうということがあります。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-104">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="5ebd1-105">これはもっともな心配です。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-105">This is a valid concern.</span></span> <span data-ttu-id="5ebd1-106">メンバーによって例外がスローされる場合、そのパフォーマンスが桁違いに低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-106">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="5ebd1-107">ただし、エラー コードの使用を禁止する例外ガイドラインに厳密に準拠しながら、優れたパフォーマンスを達成することができます。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-107">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="5ebd1-108">このセクションで説明する 2 つのパターンは、これを行う方法を提案しています。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-108">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="5ebd1-109">❌ 例外によるパフォーマンスへの悪影響の可能性が心配であるという理由で、エラー コードを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-109">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="5ebd1-110">パフォーマンスを向上させるために、次の 2 つのセクションで説明する、Tester-Doer パターンまたは Try-Parse パターンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-110">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="5ebd1-111">Tester-Doer パターン</span><span class="sxs-lookup"><span data-stu-id="5ebd1-111">Tester-Doer Pattern</span></span>

 <span data-ttu-id="5ebd1-112">例外をスローするメンバーを 2 つに分割することで、メンバーのパフォーマンスを向上させることができる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-112">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="5ebd1-113"><xref:System.Collections.Generic.ICollection%601> インターフェイスの <xref:System.Collections.Generic.ICollection%601.Add%2A> メソッドを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-113">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="5ebd1-114">コレクションが読み取り専用の場合、メソッド `Add` によって (例外が) スローされます。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-114">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="5ebd1-115">これは、このメソッドの呼び出しが頻繁に失敗することが予想されるシナリオでは、パフォーマンスの問題になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-115">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="5ebd1-116">この問題を軽減する方法の 1 つは、値を追加する前に、コレクションが書き込み可能かどうかをテストすることです。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-116">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="5ebd1-117">条件をテストするために使用されるメンバー (この例では `IsReadOnly` プロパティ) を Tester と呼びます。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-117">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="5ebd1-118">可能性があるスロー操作を実行するために使用されるメンバー (この例では `Add` メソッド) を Doer と呼びます。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-118">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="5ebd1-119">✔️ 例外に関連するパフォーマンスの問題を回避するために、一般的なシナリオで例外をスローする可能性のあるメンバーに対して Tester-Doer パターンを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-119">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="5ebd1-120">Try-Parse パターン</span><span class="sxs-lookup"><span data-stu-id="5ebd1-120">Try-Parse Pattern</span></span>

 <span data-ttu-id="5ebd1-121">パフォーマンスが非常に重要な API では、前のセクションで説明した Tester-Doer パターンよりも高速なパターンを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-121">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="5ebd1-122">このパターンでは、メンバー名を調整して、適切に定義されたテスト ケースをメンバー セマンティクスの一部にするための呼び出しが行われます。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-122">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="5ebd1-123">たとえば、<xref:System.DateTime> では、文字列の解析が失敗した場合に例外をスローする <xref:System.DateTime.Parse%2A> メソッドが定義されます。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-123">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="5ebd1-124">解析を試行する対応する <xref:System.DateTime.TryParse%2A> メソッドも定義されますが、解析が失敗した場合は false が返され、解析が成功した場合はその結果が `out` パラメーターを使用して返されます。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-124">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="5ebd1-125">このパターンを使用する場合は、Try 機能を厳しい条件で定義することが重要です。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-125">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="5ebd1-126">明確に定義された Try 以外の理由でメンバーが失敗した場合でも、メンバーによって対応する例外がスローされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-126">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="5ebd1-127">✔️ 例外に関連するパフォーマンスの問題を回避するには、一般的なシナリオで例外をスローする可能性のあるメンバーに対して Try-Parse パターンを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-127">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="5ebd1-128">✔️ このパターンを実装するメソッドには、"Try" というプレフィックスとブール型の戻り値を使用してください。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-128">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="5ebd1-129">✔️ Try-Parse パターンを使用して、メンバーごとに例外をスローするメンバーを用意してください。</span><span class="sxs-lookup"><span data-stu-id="5ebd1-129">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="5ebd1-130">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="5ebd1-130">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5ebd1-131">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="5ebd1-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5ebd1-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ebd1-132">See also</span></span>

- [<span data-ttu-id="5ebd1-133">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5ebd1-133">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="5ebd1-134">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5ebd1-134">Design Guidelines for Exceptions</span></span>](exceptions.md)
