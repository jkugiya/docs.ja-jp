---
title: 破壊的変更:一部の TableLayoutSettings プロパティで InvalidEnumArgumentException がスローされる
description: .NET 6.0 での破壊的変更について学習します。一部の TableLayoutSettings API で、無効な引数に対する InvalidEnumArgumentException がスローされるようになりました。
ms.date: 01/18/2021
ms.openlocfilehash: 8397952e4647347718f11597a100c5d764e7186b
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570245"
---
# <a name="selected-tablelayoutsettings-properties-throw-invalidenumargumentexception"></a><span data-ttu-id="e9c4e-103">選択された TableLayoutSettings プロパティで InvalidEnumArgumentException がスローされる</span><span class="sxs-lookup"><span data-stu-id="e9c4e-103">Selected TableLayoutSettings properties throw InvalidEnumArgumentException</span></span>

<span data-ttu-id="e9c4e-104">正しくない値を割り当てようとすると、選択された <xref:System.Windows.Forms.TableLayoutSettings> プロパティで <xref:System.ComponentModel.InvalidEnumArgumentException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e9c4e-104">Selected <xref:System.Windows.Forms.TableLayoutSettings> properties now throw an <xref:System.ComponentModel.InvalidEnumArgumentException> if you attempt to assign an incorrect value.</span></span>

## <a name="change-description"></a><span data-ttu-id="e9c4e-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="e9c4e-105">Change description</span></span>

<span data-ttu-id="e9c4e-106">以前のバージョンの .NET では、正しくない値を割り当てようとすると、これらのプロパティで <xref:System.ArgumentOutOfRangeException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e9c4e-106">In previous .NET versions, these properties throw an <xref:System.ArgumentOutOfRangeException> if you attempt to assign an incorrect value.</span></span> <span data-ttu-id="e9c4e-107">.NET 6.0 以降では、そのような場合にこれらのプロパティで <xref:System.ComponentModel.InvalidEnumArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e9c4e-107">Starting in .NET 6.0, these properties throw an <xref:System.ComponentModel.InvalidEnumArgumentException> in such cases.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e9c4e-108">変更理由</span><span class="sxs-lookup"><span data-stu-id="e9c4e-108">Reason for change</span></span>

<span data-ttu-id="e9c4e-109"><xref:System.ComponentModel.InvalidEnumArgumentException> のスローは、同様の状況での既存の Windows フォーム API に従っています。</span><span class="sxs-lookup"><span data-stu-id="e9c4e-109">Throwing <xref:System.ComponentModel.InvalidEnumArgumentException> is in line with the existing Windows Forms API in similar situations.</span></span> <span data-ttu-id="e9c4e-110">また、この例外をスローすると、開発者のデバッグ エクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="e9c4e-110">Throwing this exception also provides developers with a better debug experience.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e9c4e-111">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e9c4e-111">Version introduced</span></span>

<span data-ttu-id="e9c4e-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="e9c4e-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e9c4e-113">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="e9c4e-113">Recommended action</span></span>

- <span data-ttu-id="e9c4e-114">正しくない値が割り当てられないように、コードを更新します。</span><span class="sxs-lookup"><span data-stu-id="e9c4e-114">Update the code to prevent assigning incorrect values.</span></span>
- <span data-ttu-id="e9c4e-115">必要に応じて、これらの API にアクセスするときに <xref:System.ComponentModel.InvalidEnumArgumentException> を処理します。</span><span class="sxs-lookup"><span data-stu-id="e9c4e-115">If necessary, handle an <xref:System.ComponentModel.InvalidEnumArgumentException> when accessing these APIs.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e9c4e-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="e9c4e-116">Affected APIs</span></span>

<span data-ttu-id="e9c4e-117">次の表に、影響を受けるプロパティを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e9c4e-117">The following table lists the affected properties:</span></span>

| <span data-ttu-id="e9c4e-118">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e9c4e-118">Property</span></span> | <span data-ttu-id="e9c4e-119">変更されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e9c4e-119">Version changed</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TableLayoutPanel.CellBorderStyle?displayProperty=fullName> | <span data-ttu-id="e9c4e-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="e9c4e-120">Preview 1</span></span> |
| <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle?displayProperty=fullName> | <span data-ttu-id="e9c4e-121">Preview 1</span><span class="sxs-lookup"><span data-stu-id="e9c4e-121">Preview 1</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.TableLayoutPanel.CellBorderStyle`
- `P:System.Windows.Forms.TableLayoutPanel.GrowStyle`

### Category

Windows Forms

-->
