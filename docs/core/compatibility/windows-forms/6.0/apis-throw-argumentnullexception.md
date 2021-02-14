---
title: 破壊的変更:一部の API によって ArgumentNullException がスローされる
description: .NET 6.0 での破壊的変更について説明します。一部の API で引数が検証され、ArgumentNullException がスローされるようになりました。
ms.date: 01/29/2021
ms.openlocfilehash: f9d7dc8bb57ed8dc5b4ff41bda9b3bde7db7b880
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804150"
---
# <a name="some-apis-throw-argumentnullexception"></a><span data-ttu-id="f801f-103">一部の API によって ArgumentNullException がスローされる</span><span class="sxs-lookup"><span data-stu-id="f801f-103">Some APIs throw ArgumentNullException</span></span>

<span data-ttu-id="f801f-104">一部の API で入力パラメーターが検証されるようになり、入力引数が `null` で呼び出された場合、以前は <xref:System.NullReferenceException> がスローされていたものが、<xref:System.ArgumentNullException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f801f-104">Some APIs now validate input parameters and throw an <xref:System.ArgumentNullException> where previously they threw a <xref:System.NullReferenceException>, if invoked with `null` input arguments.</span></span>

## <a name="change-description"></a><span data-ttu-id="f801f-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="f801f-105">Change description</span></span>

<span data-ttu-id="f801f-106">以前のバージョンの .NET では、影響を受ける API を呼び出すときに引数を `null` にすると、<xref:System.NullReferenceException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f801f-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> if invoked with an argument that's `null`.</span></span>

<span data-ttu-id="f801f-107">.NET 6.0 以降では、影響を受ける API を呼び出すときに引数を `null` にすると、<xref:System.ArgumentNullException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f801f-107">Starting in .NET 6.0, the affected APIs throw an <xref:System.ArgumentNullException> if invoked with an argument that's `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f801f-108">変更理由</span><span class="sxs-lookup"><span data-stu-id="f801f-108">Reason for change</span></span>

<span data-ttu-id="f801f-109"><xref:System.ArgumentNullException> のスローは、.NET ランタイムの動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="f801f-109">Throwing <xref:System.ArgumentNullException> conforms to .NET Runtime behavior.</span></span> <span data-ttu-id="f801f-110">例外の原因になった引数が明確に伝わることにより、デバッグのエクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="f801f-110">It provides a better debug experience by clearly communicating which argument caused the exception.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f801f-111">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f801f-111">Version introduced</span></span>

<span data-ttu-id="f801f-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="f801f-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f801f-113">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f801f-113">Recommended action</span></span>

- <span data-ttu-id="f801f-114">コードをレビューし、必要に応じて、影響を受ける API に `null` 入力引数を渡さないように更新します。</span><span class="sxs-lookup"><span data-stu-id="f801f-114">Review and, if necessary, update your code to prevent passing `null` input arguments to the affected APIs.</span></span>
- <span data-ttu-id="f801f-115">コードで <xref:System.NullReferenceException> を処理している場合は、置き換えるか、<xref:System.ArgumentNullException> 用のハンドラーを別に追加します。</span><span class="sxs-lookup"><span data-stu-id="f801f-115">If your code handles <xref:System.NullReferenceException>, replace or add an additional handler for <xref:System.ArgumentNullException>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f801f-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f801f-116">Affected APIs</span></span>

<span data-ttu-id="f801f-117">次の表に、影響を受けるプロパティを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="f801f-117">The following table lists the affected properties:</span></span>

| <span data-ttu-id="f801f-118">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f801f-118">Property</span></span> | <span data-ttu-id="f801f-119">変更されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f801f-119">Version changed</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | <span data-ttu-id="f801f-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="f801f-120">Preview 1</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
