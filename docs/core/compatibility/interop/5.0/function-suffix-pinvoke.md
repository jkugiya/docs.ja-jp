---
title: '破壊的変更: Windows 以外のプラットフォームでは A/W サフィックスのプローブは行われません'
description: .NET 5 での相互運用に関する破壊的変更について学習します。この変更により、Windows 以外のプラットフォームでの P/Invokes のプローブ中に、サフィックスは関数エクスポート名に追加されなくなりました。
ms.date: 08/13/2020
ms.openlocfilehash: 924cbcb6c432e2f7c52c7218d48a938b61306c9c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256622"
---
# <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="9d387-103">Windows 以外のプラットフォームでは A/W サフィックスのプローブは行われません</span><span class="sxs-lookup"><span data-stu-id="9d387-103">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="9d387-104">.NET ランタイムでは、Windows 以外のプラットフォームにおいて P/Invoke のプローブ中に関数エクスポート名に `A` または `W` サフィックスを追加しなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9d387-104">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9d387-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="9d387-105">Version introduced</span></span>

<span data-ttu-id="9d387-106">5.0</span><span class="sxs-lookup"><span data-stu-id="9d387-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="9d387-107">変更の説明</span><span class="sxs-lookup"><span data-stu-id="9d387-107">Change description</span></span>

<span data-ttu-id="9d387-108">[Windows には、Windows コードページと Unicode バージョンに対応する `A` または `W` サフィックスを Windows SDK 関数名に追加するという ](/windows/win32/intl/conventions-for-function-prototypes) 規約があります。</span><span class="sxs-lookup"><span data-stu-id="9d387-108">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="9d387-109">以前のバージョンの .NET では、CoreCLR と Mono の両方のランタイムによって、"*すべてのプラットフォームでの*" P/Invoke のエクスポートの検出時に、エクスポート名に `A` または `W` サフィックスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="9d387-109">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="9d387-110">.NET 5 以降のバージョンでは、"*Windows のみでの*" エクスポートの検出時に `A` または `W` サフィックスがエクスポート名に追加されます。</span><span class="sxs-lookup"><span data-stu-id="9d387-110">In .NET 5 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="9d387-111">Unix プラットフォームでは、サフィックスは追加されません。</span><span class="sxs-lookup"><span data-stu-id="9d387-111">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="9d387-112">Windows プラットフォーム上の両方のランタイムのセマンティクスは変更されません。</span><span class="sxs-lookup"><span data-stu-id="9d387-112">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9d387-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="9d387-113">Reason for change</span></span>

<span data-ttu-id="9d387-114">この変更は、クロスプラットフォームのプローブを簡素化するために行われました。</span><span class="sxs-lookup"><span data-stu-id="9d387-114">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="9d387-115">Windows 以外のプラットフォームにはこのセマンティックが含まれていないため、オーバーヘッドが発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="9d387-115">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9d387-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="9d387-116">Recommended action</span></span>

<span data-ttu-id="9d387-117">変更を軽減するには、Windows 以外のプラットフォームに必要なサフィックスを手動で追加します。</span><span class="sxs-lookup"><span data-stu-id="9d387-117">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="9d387-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9d387-118">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

## <a name="affected-apis"></a><span data-ttu-id="9d387-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="9d387-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

### Category

Interop

-->
