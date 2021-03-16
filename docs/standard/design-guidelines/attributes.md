---
description: '詳細情報: 属性'
title: 属性
ms.date: 10/22/2008
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 1557ba0945da0c8498c67f70ba4a01dd0bbe432e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642423"
---
# <a name="attributes"></a><span data-ttu-id="e0355-103">属性</span><span class="sxs-lookup"><span data-stu-id="e0355-103">Attributes</span></span>

<span data-ttu-id="e0355-104"><xref:System.Attribute?displayProperty=nameWithType> は、カスタム属性を定義するために使用される基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="e0355-104"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="e0355-105">属性は、アセンブリ、型、メンバー、パラメーターなどのプログラミング要素に追加できる注釈です。</span><span class="sxs-lookup"><span data-stu-id="e0355-105">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="e0355-106">それらは、アセンブリのメタデータに格納され、リフレクション API を使用して実行時にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e0355-106">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="e0355-107">たとえば、フレームワークによって定義されている <xref:System.ObsoleteAttribute> を型またはメンバーに適用して、その型またはメンバーが非推奨になったことを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="e0355-107">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="e0355-108">属性には、属性に関連する追加データを保持する 1 つ以上のプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="e0355-108">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="e0355-109">たとえば、`ObsoleteAttribute` は、型またはメンバーが非推奨になったリリース、および古い API を置き換える新しい API の説明に関する追加情報を保持できます。</span><span class="sxs-lookup"><span data-stu-id="e0355-109">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>

 <span data-ttu-id="e0355-110">属性の一部のプロパティは、属性を適用するときに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0355-110">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="e0355-111">これらは、位置指定のコンストラクター パラメーターとして表されるため、必須プロパティまたは必須引数と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e0355-111">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="e0355-112">たとえば、<xref:System.Diagnostics.ConditionalAttribute> の <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> プロパティは必須プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e0355-112">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="e0355-113">属性が適用されるときに必ずしも指定する必要がないプロパティは、省略可能なプロパティ (または省略可能な引数) と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e0355-113">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="e0355-114">それらは、設定可能なプロパティによって表されます。</span><span class="sxs-lookup"><span data-stu-id="e0355-114">They are represented by settable properties.</span></span> <span data-ttu-id="e0355-115">コンパイラには、属性が適用されるときにこれらのプロパティを設定するための特別な構文が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e0355-115">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="e0355-116">たとえば、<xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> プロパティは省略可能な引数を表します。</span><span class="sxs-lookup"><span data-stu-id="e0355-116">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="e0355-117">✔️ カスタム属性クラスの名前には "Attribute" というサフィックスを付けます。</span><span class="sxs-lookup"><span data-stu-id="e0355-117">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="e0355-118">✔️ カスタム属性には <xref:System.AttributeUsageAttribute> を適用します。</span><span class="sxs-lookup"><span data-stu-id="e0355-118">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="e0355-119">✔️ 省略可能な引数には設定可能なプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="e0355-119">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="e0355-120">✔️ 必須の引数には取得専用のプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="e0355-120">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="e0355-121">✔️ 必須の引数に対応するプロパティを初期化するためのコンストラクター パラメーターを提供ます。</span><span class="sxs-lookup"><span data-stu-id="e0355-121">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="e0355-122">各パラメーターの名前は、対応するプロパティと同じにする必要があります (ただし、異なる大文字と小文字の使い分けで)。</span><span class="sxs-lookup"><span data-stu-id="e0355-122">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="e0355-123">❌ 省略可能な引数に対応するプロパティを初期化するためのコンストラクター パラメーターは提供しないようにします。</span><span class="sxs-lookup"><span data-stu-id="e0355-123">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="e0355-124">つまり、コンストラクターとセッターの両方で設定できるプロパティがないようにします。</span><span class="sxs-lookup"><span data-stu-id="e0355-124">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="e0355-125">このガイドラインにより、省略可能な引数と必須の引数の区別が非常に明確になり、同じことを 2 つの方法で行うことが回避されます。</span><span class="sxs-lookup"><span data-stu-id="e0355-125">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="e0355-126">❌ カスタム属性コンストラクターをオーバーロードしないようにします。</span><span class="sxs-lookup"><span data-stu-id="e0355-126">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="e0355-127">コンストラクターを 1 つだけにすると、どの引数が必須で、どれが省略可能であるかが、ユーザーに明確に伝わります。</span><span class="sxs-lookup"><span data-stu-id="e0355-127">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="e0355-128">✔️ 可能であれば、カスタム属性クラスをシールします。</span><span class="sxs-lookup"><span data-stu-id="e0355-128">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="e0355-129">これにより、属性の参照が高速になります。</span><span class="sxs-lookup"><span data-stu-id="e0355-129">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="e0355-130">*Portions &copy; 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="e0355-130">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e0355-131">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="e0355-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e0355-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0355-132">See also</span></span>

- [<span data-ttu-id="e0355-133">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="e0355-133">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="e0355-134">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="e0355-134">Usage Guidelines</span></span>](usage-guidelines.md)
