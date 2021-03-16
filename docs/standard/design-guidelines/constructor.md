---
description: '詳細情報: コンストラクターのデザイン'
title: コンストラクターのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 2a5c85e1dea3349f897c24fa5d40d73c6e1f9d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642319"
---
# <a name="constructor-design"></a><span data-ttu-id="00c9a-103">コンストラクターのデザイン</span><span class="sxs-lookup"><span data-stu-id="00c9a-103">Constructor Design</span></span>

<span data-ttu-id="00c9a-104">コンストラクターには、型コンストラクターとインスタンス コンストラクターの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="00c9a-104">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="00c9a-105">型コンストラクターは静的であり、型が使用される前に CLR によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-105">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="00c9a-106">インスタンス コンストラクターは、型のインスタンスが作成されるときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-106">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="00c9a-107">型コンストラクターは、パラメーターを受け取ることができません。</span><span class="sxs-lookup"><span data-stu-id="00c9a-107">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="00c9a-108">インスタンス コンストラクターはできます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-108">Instance constructors can.</span></span> <span data-ttu-id="00c9a-109">パラメーターを受け取らないインスタンス コンストラクターは、通常、パラメーターなしのコンストラクターと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-109">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="00c9a-110">コンストラクターは、型のインスタンスを作成する最も自然な方法です。</span><span class="sxs-lookup"><span data-stu-id="00c9a-110">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="00c9a-111">ほとんどの開発者は、インスタンスを作成する代わりの方法 (ファクトリ メソッドなど) を検討する前に、コンストラクターを探して使おうとします。</span><span class="sxs-lookup"><span data-stu-id="00c9a-111">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="00c9a-112">✔️ 単純な、できれば既定の、コンストラクターを提供することを検討します。</span><span class="sxs-lookup"><span data-stu-id="00c9a-112">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="00c9a-113">単純なコンストラクターとは、ごく少数のパラメーターを持ち、すべてのパラメーターがプリミティブまたは列挙型であるものです。</span><span class="sxs-lookup"><span data-stu-id="00c9a-113">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="00c9a-114">そのような単純なコンストラクターを用意すると、フレームワークの使いやすさが向上します。</span><span class="sxs-lookup"><span data-stu-id="00c9a-114">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="00c9a-115">✔️ 目的の操作のセマンティクスが新しいインスタンスの構築に直接対応しない場合、またはコンストラクターの設計ガイドラインに従うと不自然に感じる場合は、コンストラクターの代わりに静的ファクトリ メソッドの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="00c9a-115">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="00c9a-116">✔️ メイン プロパティを設定するためのショートカットとして、コンストラクターのパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="00c9a-116">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="00c9a-117">空のコンストラクターを使用して後でいくつかのプロパティを設定する場合と、複数の引数を持つコンストラクターを使用する場合とで、セマンティクスに違いがあってはなりません。</span><span class="sxs-lookup"><span data-stu-id="00c9a-117">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="00c9a-118">✔️ コンストラクターのパラメーターがプロパティの設定だけに使用される場合は、コンストラクターのパラメーターとプロパティに同じ名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="00c9a-118">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="00c9a-119">そのようなパラメーターとプロパティの違いは、大文字と小文字の区別だけでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="00c9a-119">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="00c9a-120">✔️ コンストラクターでの処理は最小限にします。</span><span class="sxs-lookup"><span data-stu-id="00c9a-120">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="00c9a-121">コンストラクターのパラメーターをキャプチャする以外の多くの処理を、コンストラクターで行ってはなりません。</span><span class="sxs-lookup"><span data-stu-id="00c9a-121">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="00c9a-122">他のすべての処理のコストは、必要になるまで延期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00c9a-122">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="00c9a-123">✔️ 必要な場合は、インスタンス コンストラクターから例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="00c9a-123">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="00c9a-124">✔️ パブリックのパラメーターなしコンストラクターが必要な場合は、クラスでそのようなコンストラクターを明示的に宣言します。</span><span class="sxs-lookup"><span data-stu-id="00c9a-124">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="00c9a-125">型のコンストラクターを明示的に宣言しない場合、多くの言語 (C# など) では、パブリックのパラメーターなしコンストラクターが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-125">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="00c9a-126">(抽象クラスは、保護されたコンストラクターを受け取ります。)</span><span class="sxs-lookup"><span data-stu-id="00c9a-126">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="00c9a-127">パラメーター化されたコンストラクターをクラスに追加すると、パラメーターなしのコンストラクターはコンパイラによって追加されなくなります。</span><span class="sxs-lookup"><span data-stu-id="00c9a-127">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="00c9a-128">これにより、破壊的変更が誤って発生することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="00c9a-128">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="00c9a-129">❌ 構造体ではパラメーターなしのコンストラクターを明示的に定義しないようにします。</span><span class="sxs-lookup"><span data-stu-id="00c9a-129">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="00c9a-130">パラメーターなしのコンストラクターが定義されていない場合は、配列内のすべてのスロットでそれを実行する必要がないため、これにより配列の作成が高速になります。</span><span class="sxs-lookup"><span data-stu-id="00c9a-130">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="00c9a-131">このような理由から、C# などの多くのコンパイラでは、構造体でパラメーターなしのコンストラクターを使用できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="00c9a-131">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="00c9a-132">❌ コンストラクターの内部では、オブジェクトの仮想メンバーを呼び出さないようにします。</span><span class="sxs-lookup"><span data-stu-id="00c9a-132">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="00c9a-133">最も派生した型のコンストラクターがまだ完全には実行されていない場合でも、仮想メンバーを呼び出すと、最も派生したオーバーライドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-133">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="00c9a-134">型コンストラクターのガイドライン</span><span class="sxs-lookup"><span data-stu-id="00c9a-134">Type Constructor Guidelines</span></span>

<span data-ttu-id="00c9a-135">✔️ 静的コンストラクターはプライベートにします。</span><span class="sxs-lookup"><span data-stu-id="00c9a-135">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="00c9a-136">静的コンストラクター (クラス コンストラクターとも呼ばれます) は、型を初期化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-136">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="00c9a-137">型の最初のインスタンスが作成される前、またはその型の静的メンバーが呼び出される前に、CLR によって静的コンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-137">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="00c9a-138">ユーザーは、静的コンストラクターが呼び出されるタイミングを制御できません。</span><span class="sxs-lookup"><span data-stu-id="00c9a-138">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="00c9a-139">静的コンストラクターがプライベートでない場合、CLR 以外のコードから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-139">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="00c9a-140">コンストラクターで実行される操作によっては、これにより予期しない動作が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="00c9a-140">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="00c9a-141">C# コンパイラでは、静的コンストラクターは強制的にプライベートにされます。</span><span class="sxs-lookup"><span data-stu-id="00c9a-141">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="00c9a-142">❌ 静的コンストラクターから例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="00c9a-142">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="00c9a-143">型コンストラクターから例外がスローされた場合、その型は現在のアプリケーション ドメインで使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="00c9a-143">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="00c9a-144">✔️ 静的フィールドの初期化は、静的コンストラクターを使用して明示的に行うのではなく、インラインで行うことを検討します。これは、明示的に定義された静的コンストラクターを持たない型の場合、ランタイムでパフォーマンスを最適化できるためです。</span><span class="sxs-lookup"><span data-stu-id="00c9a-144">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="00c9a-145">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="00c9a-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="00c9a-146">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="00c9a-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="00c9a-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="00c9a-147">See also</span></span>

- [<span data-ttu-id="00c9a-148">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="00c9a-148">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="00c9a-149">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="00c9a-149">Framework Design Guidelines</span></span>](index.md)
