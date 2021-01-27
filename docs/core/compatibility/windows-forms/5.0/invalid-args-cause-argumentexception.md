---
title: '破壊的変更: WinForms メソッドで ArgumentException がスローされるようになった'
description: .NET 5.0 での破壊的変更について学習します。一部の Windows フォーム メソッドで、無効な引数に対する ArgumentException がスローされるようになりました。
ms.date: 07/18/2020
ms.openlocfilehash: 892f4d16b80f3e42187480a7fcfb24e81868d07c
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570217"
---
# <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="a4e51-103">WinForms メソッドで ArgumentException がスローされるようになった</span><span class="sxs-lookup"><span data-stu-id="a4e51-103">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="a4e51-104">一部の Windows フォーム メソッドで、無効な引数に対して <xref:System.ArgumentException> がスローされるようになりました。以前はスローされませんでした。</span><span class="sxs-lookup"><span data-stu-id="a4e51-104">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="a4e51-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="a4e51-105">Change description</span></span>

<span data-ttu-id="a4e51-106">以前は、予期しない型または不適切な型の引数を特定の Windows フォーム メソッドに渡すと、不確定な状態になりました。</span><span class="sxs-lookup"><span data-stu-id="a4e51-106">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="a4e51-107">.NET 5.0 以降では、そのようなメソッドに無効な引数を渡すと、<xref:System.ArgumentException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a4e51-107">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="a4e51-108"><xref:System.ArgumentException> をスローすることは、.NET ランタイムの動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="a4e51-108">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="a4e51-109">また、どの引数が無効であるのかが明確に伝えられることで、デバッグ エクスペリエンスも向上します。</span><span class="sxs-lookup"><span data-stu-id="a4e51-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a4e51-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a4e51-110">Version introduced</span></span>

<span data-ttu-id="a4e51-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a4e51-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a4e51-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="a4e51-112">Recommended action</span></span>

- <span data-ttu-id="a4e51-113">無効な引数を渡さないようにコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="a4e51-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="a4e51-114">必要に応じて、メソッドを呼び出したときの <xref:System.ArgumentException> を処理します。</span><span class="sxs-lookup"><span data-stu-id="a4e51-114">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a4e51-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a4e51-115">Affected APIs</span></span>

<span data-ttu-id="a4e51-116">次の表では、影響を受けるメソッドとパラメーターを示します。</span><span class="sxs-lookup"><span data-stu-id="a4e51-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="a4e51-117">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e51-117">Method</span></span> | <span data-ttu-id="a4e51-118">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="a4e51-118">Parameter name</span></span> | <span data-ttu-id="a4e51-119">条件</span><span class="sxs-lookup"><span data-stu-id="a4e51-119">Condition</span></span> | <span data-ttu-id="a4e51-120">追加されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a4e51-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="a4e51-121">引数が <xref:System.Windows.Forms.TabPage> 型ではありません。</span><span class="sxs-lookup"><span data-stu-id="a4e51-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="a4e51-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="a4e51-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="a4e51-123">引数が `null`、<xref:System.String.Empty?displayProperty=nameWithType>、または空白です。</span><span class="sxs-lookup"><span data-stu-id="a4e51-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="a4e51-124">Preview 5</span><span class="sxs-lookup"><span data-stu-id="a4e51-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="a4e51-125">指定のカルチャに `InputLanguage` を取得できません。</span><span class="sxs-lookup"><span data-stu-id="a4e51-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="a4e51-126">Preview 7</span><span class="sxs-lookup"><span data-stu-id="a4e51-126">Preview 7</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
