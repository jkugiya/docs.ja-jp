---
description: '詳細情報: イベントとコールバック'
title: イベントとコールバック
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 8a9049808ec0f7a490889ab1f17c4d8b8e8bd2b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642150"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="dab26-103">イベントとコールバック</span><span class="sxs-lookup"><span data-stu-id="dab26-103">Events and Callbacks</span></span>

<span data-ttu-id="dab26-104">コールバックは、フレームワークで、デリゲートを通じてユーザー コードにコールバックできるようにする拡張ポイントです。</span><span class="sxs-lookup"><span data-stu-id="dab26-104">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="dab26-105">これらのデリゲートは、通常、メソッドのパラメーターを通してフレームワークに渡されます。</span><span class="sxs-lookup"><span data-stu-id="dab26-105">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="dab26-106">イベントはコールバックの特殊なケースであり、デリゲート (イベント ハンドラー) を提供する便利な一貫性のある構文をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="dab26-106">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="dab26-107">さらに、イベントベースの API の使用では、Visual Studio のステートメント入力候補とデザイナーが役立ちます。</span><span class="sxs-lookup"><span data-stu-id="dab26-107">In addition, Visual Studio's statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="dab26-108">(「[イベントの設計](event.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="dab26-108">(See [Event Design](event.md).)</span></span>

 <span data-ttu-id="dab26-109">✔️ コールバックを使用して、ユーザーがフレームワークによって実行されるカスタム コードを指定できるようにすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="dab26-109">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="dab26-110">✔️ イベントを使用して、ユーザーがオブジェクト指向設計を理解していなくてもフレームワークの動作をカスタマイズできるようにすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="dab26-110">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="dab26-111">✔️ 幅広い開発者が慣れていることと、Visual Studio のステートメント入力候補と統合されているため、単純なコールバックよりもイベントを優先してください。</span><span class="sxs-lookup"><span data-stu-id="dab26-111">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="dab26-112">❌ パフォーマンスを重視する API でコールバックを使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="dab26-112">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="dab26-113">✔️ コールバックを使用して API を定義するときは、カスタム デリゲートではなく、新しい `Func<...>`、`Action<...>`、または `Expression<...>` 型を使用してください。</span><span class="sxs-lookup"><span data-stu-id="dab26-113">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="dab26-114">`Func<...>` と `Action<...>` は、汎用デリゲートを表します。</span><span class="sxs-lookup"><span data-stu-id="dab26-114">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="dab26-115">`Expression<...>` は、コンパイルして実行時に呼び出すことができる関数定義を表していますが、シリアル化してリモート プロセスに渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="dab26-115">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="dab26-116">✔️ `Func<...>` と `Action<...>` デリゲートの使用に代わる `Expression<...>` の使用によるパフォーマンスへの影響を測定して理解してください。</span><span class="sxs-lookup"><span data-stu-id="dab26-116">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="dab26-117">`Expression<...>` 型は、ほとんどの場合、`Func<...>` と `Action<...>` デリゲートと論理的に等価です。</span><span class="sxs-lookup"><span data-stu-id="dab26-117">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="dab26-118">これらの主な違いは、デリゲートはローカル プロセス シナリオで使用されることを意図しており、式は、リモート プロセスまたはコンピューターで式を評価することが有益であり、それが可能であるケースを対象としていることです。</span><span class="sxs-lookup"><span data-stu-id="dab26-118">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it's beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="dab26-119">✔️ デリゲートを呼び出すことは任意のコードを実行することであり、セキュリティ、正確性、および互換性に影響を与える可能性があることを理解しておいてください。</span><span class="sxs-lookup"><span data-stu-id="dab26-119">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="dab26-120">*Portions &copy; 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="dab26-120">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="dab26-121">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="dab26-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="dab26-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="dab26-122">See also</span></span>

- [<span data-ttu-id="dab26-123">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="dab26-123">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="dab26-124">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="dab26-124">Framework Design Guidelines</span></span>](index.md)
