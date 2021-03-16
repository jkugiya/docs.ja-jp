---
title: '破壊的変更: WinForms メソッドで ArgumentException がスローされるようになった'
description: .NET 5 での破壊的変更について学習します。一部の Windows フォーム メソッドで、無効な引数に対する ArgumentException がスローされるようになりました。
ms.date: 07/18/2020
ms.openlocfilehash: 9823e9162a562081cdd64346a502ca136b51fa75
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256140"
---
# <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="a11d5-103">WinForms メソッドで ArgumentException がスローされるようになった</span><span class="sxs-lookup"><span data-stu-id="a11d5-103">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="a11d5-104">一部の Windows フォーム メソッドで、無効な引数に対して <xref:System.ArgumentException> がスローされるようになりました。以前はスローされませんでした。</span><span class="sxs-lookup"><span data-stu-id="a11d5-104">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="a11d5-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="a11d5-105">Change description</span></span>

<span data-ttu-id="a11d5-106">以前は、予期しない型または不適切な型の引数を特定の Windows フォーム メソッドに渡すと、不確定な状態になりました。</span><span class="sxs-lookup"><span data-stu-id="a11d5-106">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="a11d5-107">.NET 5 以降では、そのようなメソッドに無効な引数を渡すと、<xref:System.ArgumentException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a11d5-107">Starting in .NET 5, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="a11d5-108"><xref:System.ArgumentException> をスローすることは、.NET ランタイムの動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="a11d5-108">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="a11d5-109">また、どの引数が無効であるのかが明確に伝えられることで、デバッグ エクスペリエンスも向上します。</span><span class="sxs-lookup"><span data-stu-id="a11d5-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a11d5-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a11d5-110">Version introduced</span></span>

<span data-ttu-id="a11d5-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a11d5-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a11d5-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="a11d5-112">Recommended action</span></span>

- <span data-ttu-id="a11d5-113">無効な引数を渡さないようにコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="a11d5-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="a11d5-114">必要に応じて、メソッドを呼び出したときの <xref:System.ArgumentException> を処理します。</span><span class="sxs-lookup"><span data-stu-id="a11d5-114">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a11d5-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a11d5-115">Affected APIs</span></span>

<span data-ttu-id="a11d5-116">次の表では、影響を受けるメソッドとパラメーターを示します。</span><span class="sxs-lookup"><span data-stu-id="a11d5-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="a11d5-117">メソッド</span><span class="sxs-lookup"><span data-stu-id="a11d5-117">Method</span></span> | <span data-ttu-id="a11d5-118">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="a11d5-118">Parameter name</span></span> | <span data-ttu-id="a11d5-119">条件</span><span class="sxs-lookup"><span data-stu-id="a11d5-119">Condition</span></span> | <span data-ttu-id="a11d5-120">追加されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a11d5-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="a11d5-121">引数が <xref:System.Windows.Forms.TabPage> 型ではありません。</span><span class="sxs-lookup"><span data-stu-id="a11d5-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="a11d5-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="a11d5-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="a11d5-123">引数が `null`、<xref:System.String.Empty?displayProperty=nameWithType>、または空白です。</span><span class="sxs-lookup"><span data-stu-id="a11d5-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="a11d5-124">Preview 5</span><span class="sxs-lookup"><span data-stu-id="a11d5-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="a11d5-125">指定のカルチャに `InputLanguage` を取得できません。</span><span class="sxs-lookup"><span data-stu-id="a11d5-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="a11d5-126">Preview 7</span><span class="sxs-lookup"><span data-stu-id="a11d5-126">Preview 7</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
