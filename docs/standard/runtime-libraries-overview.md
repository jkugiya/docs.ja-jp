---
title: ランタイム ライブラリの概要
description: 目次の「ランタイム ライブラリ」セクションに含まれる内容について学習します。
author: tdykstra
ms.date: 11/12/2020
ms.openlocfilehash: 5a8f888e1778553e2968277738cfef5134f11589
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "103412170"
---
# <a name="runtime-libraries-overview"></a><span data-ttu-id="3038c-103">ランタイム ライブラリの概要</span><span class="sxs-lookup"><span data-stu-id="3038c-103">Runtime libraries overview</span></span>

<span data-ttu-id="3038c-104">[フレームワークに依存するアプリ](../core/introduction.md#deployment-models)で使用するためにコンピューターにインストールされている [.NET ランタイム](../core/introduction.md#sdk-and-runtimes)には、[ランタイム ライブラリ](glossary.md#runtime)、[フレームワーク ライブラリ](glossary.md#framework-libraries)、または[基本クラス ライブラリ (BCL)](glossary.md#bcl)と呼ばれるクラス ライブラリの包括的な標準セットがあります。</span><span class="sxs-lookup"><span data-stu-id="3038c-104">The [.NET runtime](../core/introduction.md#sdk-and-runtimes), which is installed on a machine for use by [framework-dependent apps](../core/introduction.md#deployment-models), has an expansive standard set of class libraries, known as [runtime libraries](glossary.md#runtime), [framework libraries](glossary.md#framework-libraries), or the [base class library (BCL)](glossary.md#bcl).</span></span> <span data-ttu-id="3038c-105">また、NuGet パッケージで提供されているランタイム ライブラリの拡張機能もあります。</span><span class="sxs-lookup"><span data-stu-id="3038c-105">In addition, there are extensions to the runtime libraries, provided in NuGet packages.</span></span>

<span data-ttu-id="3038c-106">これらのライブラリでは、多くの汎用およびアプリ固有の型、アルゴリズム、ユーティリティの機能の実装が提供されます。</span><span class="sxs-lookup"><span data-stu-id="3038c-106">These libraries provide implementations for many general and app-specific types, algorithms, and utility functionality.</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="3038c-107">ランタイム ライブラリ</span><span class="sxs-lookup"><span data-stu-id="3038c-107">Runtime libraries</span></span>

<span data-ttu-id="3038c-108">これらのライブラリでは、基本的な型およびユーティリティの機能が提供され、他のすべての .NET クラス ライブラリの基本となります。</span><span class="sxs-lookup"><span data-stu-id="3038c-108">These libraries provide the foundational types and utility functionality and are the base of all other .NET class libraries.</span></span> <span data-ttu-id="3038c-109">たとえば、<xref:System.String?displayProperty=nameWithType> クラスで、これにより文字列を操作するための API が提供されます。</span><span class="sxs-lookup"><span data-stu-id="3038c-109">An example is the <xref:System.String?displayProperty=nameWithType> class, which provides APIs for working with strings.</span></span> <span data-ttu-id="3038c-110">別の例としては、[シリアル化ライブラリ](serialization/index.md)があります。</span><span class="sxs-lookup"><span data-stu-id="3038c-110">Another example is the [serialization libraries](serialization/index.md).</span></span>

## <a name="extensions-to-the-runtime-libraries"></a><span data-ttu-id="3038c-111">ランタイム ライブラリの拡張機能</span><span class="sxs-lookup"><span data-stu-id="3038c-111">Extensions to the runtime libraries</span></span>

<span data-ttu-id="3038c-112">一部のライブラリは、ランタイムの[共有フレームワーク](glossary.md#shared-framework)に含まれるのではなく、NuGet パッケージで提供されます。</span><span class="sxs-lookup"><span data-stu-id="3038c-112">Some libraries are provided in NuGet packages rather than included in the runtime's [shared framework](glossary.md#shared-framework).</span></span> <span data-ttu-id="3038c-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3038c-113">For example:</span></span>

* [<span data-ttu-id="3038c-114">Logging</span><span class="sxs-lookup"><span data-stu-id="3038c-114">Logging</span></span>](../core/extensions/logging.md)
* [<span data-ttu-id="3038c-115">依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="3038c-115">Dependency injection</span></span>](../core/extensions/dependency-injection.md)
* [<span data-ttu-id="3038c-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="3038c-116">Configuration</span></span>](../core/extensions/configuration.md)

## <a name="see-also"></a><span data-ttu-id="3038c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3038c-117">See also</span></span>

* [<span data-ttu-id="3038c-118">.NET の概要</span><span class="sxs-lookup"><span data-stu-id="3038c-118">Introduction to .NET</span></span>](../core/introduction.md)
* [<span data-ttu-id="3038c-119">.NET SDK またはランタイムのインストール</span><span class="sxs-lookup"><span data-stu-id="3038c-119">Install .NET SDK or runtime</span></span>](../core/install/index.yml)
* [<span data-ttu-id="3038c-120">インストールされている .NET SDK または使用するランタイムのバージョンを選択する</span><span class="sxs-lookup"><span data-stu-id="3038c-120">Select the installed .NET SDK or runtime version to use</span></span>](../core/versions/selection.md)
* [<span data-ttu-id="3038c-121">フレームワークに依存するアプリの発行</span><span class="sxs-lookup"><span data-stu-id="3038c-121">Publish framework-dependent apps</span></span>](../core/deploying/index.md#publish-framework-dependent)
