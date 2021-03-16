---
title: 破壊的変更:TextFormatFlags.ModifyString は古くなっています
description: .NET 5 の破壊的変更について学習します。この変更により、TextFormatFlags.ModifyString は警告として古いものとなります。
ms.date: 11/05/2020
ms.openlocfilehash: 9fe1e04b1ad36070b08af2affdca1e058ec74bb8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256167"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="1f4e0-103">TextFormatFlags.ModifyString は古くなっています</span><span class="sxs-lookup"><span data-stu-id="1f4e0-103">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="1f4e0-104"><xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> フィールドには警告として非推奨マークが付いています。今後の .NET バージョンで削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1f4e0-104">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

## <a name="change-description"></a><span data-ttu-id="1f4e0-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="1f4e0-105">Change description</span></span>

<span data-ttu-id="1f4e0-106">以前のバージョンの .NET では、<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 列挙フィールドは非推奨になっていません。</span><span class="sxs-lookup"><span data-stu-id="1f4e0-106">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="1f4e0-107">.NET 5 以降のバージョンでは、警告として非推奨マークが付いています。</span><span class="sxs-lookup"><span data-stu-id="1f4e0-107">In .NET 5 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="1f4e0-108">このフィールドは今後の .NET バージョンで削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1f4e0-108">This field may be removed in a future .NET version.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="1f4e0-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="1f4e0-109">Reason for change</span></span>

<span data-ttu-id="1f4e0-110"><xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> で <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> に文字列を渡すと、その文字列が変化することがあります。</span><span class="sxs-lookup"><span data-stu-id="1f4e0-110">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="1f4e0-111">この動作は文字列の不変性という約束事を破るものであり、.NET ランタイムが致命的に破損するおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="1f4e0-111">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1f4e0-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="1f4e0-112">Version introduced</span></span>

<span data-ttu-id="1f4e0-113">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1f4e0-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1f4e0-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="1f4e0-114">Recommended action</span></span>

<span data-ttu-id="1f4e0-115"><xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> に依存するコードがあれば、それを更新します。</span><span class="sxs-lookup"><span data-stu-id="1f4e0-115">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1f4e0-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="1f4e0-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
