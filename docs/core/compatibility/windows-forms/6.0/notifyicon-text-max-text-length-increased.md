---
title: 破壊的変更:NotifyIcon。テキストの最大文字数の増加
description: .NET 6 での破壊的変更について学習します。NotifyIcon.Text プロパティのテキストの最大長が増加しています。
ms.date: 01/19/2021
ms.openlocfilehash: f87b98dd852ce202689ae9360bee9b6cfbf01794
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255777"
---
# <a name="notifyicontext-maximum-text-length-increased"></a><span data-ttu-id="84a8b-103">NotifyIcon。テキストの最大文字数の増加</span><span class="sxs-lookup"><span data-stu-id="84a8b-103">NotifyIcon.Text maximum text length increased</span></span>

<span data-ttu-id="84a8b-104"><xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> プロパティに許可されるテキストの最大長が、63 から 127 に増加しました。</span><span class="sxs-lookup"><span data-stu-id="84a8b-104">The maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property increased from 63 to 127.</span></span>

## <a name="change-description"></a><span data-ttu-id="84a8b-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="84a8b-105">Change description</span></span>

<span data-ttu-id="84a8b-106">以前のバージョンの .NET では、<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> プロパティに許可されるテキストの最大長は 63 文字です。</span><span class="sxs-lookup"><span data-stu-id="84a8b-106">In previous .NET versions, the maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property is 63 characters.</span></span> <span data-ttu-id="84a8b-107">.NET 6 以降では、許可されるテキストの最大長は 127 文字です。</span><span class="sxs-lookup"><span data-stu-id="84a8b-107">Starting in .NET 6, the maximum allowed text length is 127 characters.</span></span> <span data-ttu-id="84a8b-108">いずれのバージョンでも、制限を超える値を設定しようとすると <xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="84a8b-108">In any version, an <xref:System.ArgumentException> is thrown when you attempt to set a value that's longer than the limit.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="84a8b-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="84a8b-109">Reason for change</span></span>

<span data-ttu-id="84a8b-110">[基になる Windows API](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080) に従うように、許可されるテキストの最大長が増加しました。</span><span class="sxs-lookup"><span data-stu-id="84a8b-110">The maximum allowed text length was increased to be in line with the [underlying Windows API](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080).</span></span> <span data-ttu-id="84a8b-111">Windows API は Windows 2000 で更新されましたが、互換性の理由から、このプロパティのサイズ制限は .NET Framework で更新されませんでした。</span><span class="sxs-lookup"><span data-stu-id="84a8b-111">The Windows API was updated in Windows 2000, but due to compatibility reasons, the size limit for this property wasn't updated in .NET Framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="84a8b-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="84a8b-112">Version introduced</span></span>

<span data-ttu-id="84a8b-113">.NET 6 Preview 1</span><span class="sxs-lookup"><span data-stu-id="84a8b-113">.NET 6 Preview 1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="84a8b-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="84a8b-114">Recommended action</span></span>

<span data-ttu-id="84a8b-115">コードを確認し、必要に応じて任意の既存のガード条件を緩和します。</span><span class="sxs-lookup"><span data-stu-id="84a8b-115">Review your code and relax any existing guard conditions, if necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="84a8b-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="84a8b-116">Affected APIs</span></span>

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
