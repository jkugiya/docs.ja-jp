---
title: フレームワーク デザインのガイドライン
description: API の一貫性と使いやすさを実現するために、.NET を拡張および操作するライブラリをデザインするためのフレームワーク デザインのガイドラインをご覧ください。
titleSuffix: ''
ms.date: 10/22/2008
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 03fa44c1fed219b50cf1a8d22b2c9f79947f4976
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706659"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="b542a-103">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b542a-103">Framework Design Guidelines</span></span>

<span data-ttu-id="b542a-104">このセクションでは、.NET Framework を拡張および操作するライブラリをデザインするためのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="b542a-104">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="b542a-105">目標は、開発に使用されるプログラミング言語に依存しない統合プログラミング モデルを提供することにより、ライブラリ デザイナーが API の一貫性と使いやすさを確保できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="b542a-105">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="b542a-106">.NET Framework を拡張するクラスやコンポーネントを開発する場合は、これらのデザイン ガイドラインに従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b542a-106">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="b542a-107">一貫性のないライブラリ デザインは、開発者の生産性に悪影響を及ぼし、採用を妨げます。</span><span class="sxs-lookup"><span data-stu-id="b542a-107">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="b542a-108">ガイドラインは、`Do`、`Consider`、`Avoid`、`Do not` という言葉から始まる単純な推奨事項として編成されています。</span><span class="sxs-lookup"><span data-stu-id="b542a-108">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="b542a-109">これらのガイドラインは、クラス ライブラリ デザイナーがさまざまなソリューション間のトレードオフを理解できるようにすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="b542a-109">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="b542a-110">優れたライブラリ デザインでは、これらのデザイン ガイドラインに違反することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b542a-110">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="b542a-111">このようなケースはまれである必要があり、その決定について明確で説得力のある理由があることが重要です。</span><span class="sxs-lookup"><span data-stu-id="b542a-111">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="b542a-112">これらのガイドラインは、Krzysztof Cwalina 氏と Brad abrams 氏による『*Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*』(フレームワーク デザインのガイドライン: 再利用可能な .NET ライブラリのための表記規則、慣用句、パターン、第 2 版)からの抜粋です。</span><span class="sxs-lookup"><span data-stu-id="b542a-112">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b542a-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b542a-113">In This Section</span></span>  

 [<span data-ttu-id="b542a-114">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b542a-114">Naming Guidelines</span></span>](naming-guidelines.md)  
 <span data-ttu-id="b542a-115">クラス ライブラリ内のアセンブリ、名前空間、型、メンバーの名前付けに関するガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="b542a-115">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="b542a-116">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b542a-116">Type Design Guidelines</span></span>](type.md)  
 <span data-ttu-id="b542a-117">静的および抽象クラス、インターフェイス、列挙型、構造体、およびその他の型を使用するためのガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="b542a-117">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="b542a-118">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b542a-118">Member Design Guidelines</span></span>](member.md)  
 <span data-ttu-id="b542a-119">プロパティ、メソッド、コンストラクター、フィールド、イベント、演算子、パラメーターのデザインと使用に関するガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="b542a-119">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="b542a-120">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="b542a-120">Designing for Extensibility</span></span>](designing-for-extensibility.md)  
 <span data-ttu-id="b542a-121">サブクラス化、イベントの使用、仮想メンバー、コールバックなどの拡張機能のメカニズムについて説明し、フレームワークの要件に最も適したメカニズムを選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b542a-121">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="b542a-122">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b542a-122">Design Guidelines for Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="b542a-123">例外をデザイン、スロー、キャッチするためのデザイン ガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b542a-123">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="b542a-124">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="b542a-124">Usage Guidelines</span></span>](usage-guidelines.md)  
 <span data-ttu-id="b542a-125">配列、属性、コレクションなどの一般的な型の使用、シリアル化のサポート、および等値演算子のオーバーロードに関するガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b542a-125">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="b542a-126">共通デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="b542a-126">Common Design Patterns</span></span>](common-design-patterns.md)  
 <span data-ttu-id="b542a-127">依存関係プロパティの選択と実装に関するガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="b542a-127">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="b542a-128">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b542a-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b542a-129">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="b542a-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b542a-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="b542a-130">See also</span></span>

- [<span data-ttu-id="b542a-131">概要</span><span class="sxs-lookup"><span data-stu-id="b542a-131">Overview</span></span>](../../framework/get-started/overview.md)
- [<span data-ttu-id="b542a-132">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="b542a-132">Development Guide</span></span>](../../framework/development-guide.md)
