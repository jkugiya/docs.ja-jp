---
title: '破壊的変更: Razor: コンパイラで 1 つのアセンブリが生成されるようになりました'
description: Razor コンパイラでは 2 つの個別のアセンブリを生成するのに 2 段階のコンパイル プロセスが使用されなくなりました、という ASP.NET Core 6.0 の破壊的変更について説明します。
no-loc:
- Razor
ms.date: 04/08/2021
ms.openlocfilehash: 8b6817563c4670aebfe681d5f24c8e309d2500ad
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299278"
---
# <a name="razor-compiler-no-longer-produces-a-views-assembly"></a><span data-ttu-id="b1e5f-103">Razor: コンパイラによって Views アセンブリが生成されなくなりました</span><span class="sxs-lookup"><span data-stu-id="b1e5f-103">Razor: Compiler no longer produces a Views assembly</span></span>

<span data-ttu-id="b1e5f-104">アプリケーションで定義された CSHTML ビューを含む個別の *Views.dll* ファイルが Razor コンパイラによって生成されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-104">The Razor compiler no longer produces a separate *Views.dll* file that contains the CSHTML views defined in an application.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b1e5f-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b1e5f-105">Version introduced</span></span>

<span data-ttu-id="b1e5f-106">ASP.NET Core 6.0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="b1e5f-106">ASP.NET Core 6.0 Preview 3</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b1e5f-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="b1e5f-107">Old behavior</span></span>

<span data-ttu-id="b1e5f-108">以前のバージョンで、Razor コンパイラには次の 2 つのファイルを生成する 2 段階コンパイル プロセスが利用されています。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-108">In previous versions, the Razor compiler utilizes a two-step compilation process that produces two files:</span></span>

- <span data-ttu-id="b1e5f-109">アプリケーションの種類を含むメインの *AppName.dll* アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-109">A main *AppName.dll* assembly that contains application types.</span></span>
- <span data-ttu-id="b1e5f-110">アプリで定義されている生成済みのビューを含む *AppName.Views.dll* アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-110">An *AppName.Views.dll* assembly that contains the generated views that are defined in the app.</span></span> <span data-ttu-id="b1e5f-111">生成されるビューの種類は、`public` であり、`AspNetCore` 名前空間の下に置かれます。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-111">Generated view types are `public` and under the `AspNetCore` namespace.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="b1e5f-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="b1e5f-112">New behavior</span></span>

<span data-ttu-id="b1e5f-113">ビューとアプリケーションの種類は、どちらも 1 つの *AppName.dll* アセンブリに含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-113">Both views and application types are included in a single *AppName.dll* assembly.</span></span> <span data-ttu-id="b1e5f-114">ビューの種類は既定では、アクセシビリティ修飾子 `internal` と `sealed` を持ち、`AspNetCoreGeneratedDocument` 名前空間の下に含められます。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-114">View types have the accessibility modifiers `internal` and `sealed`, by default, and are included under the `AspNetCoreGeneratedDocument` namespace.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b1e5f-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="b1e5f-115">Reason for change</span></span>

<span data-ttu-id="b1e5f-116">2 段階コンパイル プロセスの削除</span><span class="sxs-lookup"><span data-stu-id="b1e5f-116">Removing the two-step compilation process:</span></span>

* <span data-ttu-id="b1e5f-117">Razor ビューを使用するアプリケーションのビルド パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-117">Improves build performance for applications that use Razor views.</span></span>
* <span data-ttu-id="b1e5f-118">Visual Studio の "ホット リロード" エクスペリエンスに Razor ビューを参加させることができます。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-118">Allows Razor views to participate in the "hot reload" experience for Visual Studio.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b1e5f-119">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="b1e5f-119">Recommended action</span></span>

<span data-ttu-id="b1e5f-120">なし。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-120">None.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b1e5f-121">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="b1e5f-121">Affected APIs</span></span>

<span data-ttu-id="b1e5f-122">なし。</span><span class="sxs-lookup"><span data-stu-id="b1e5f-122">None.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
