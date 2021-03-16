---
title: 破壊的変更:Unix 上で ASCII 以外の文字を含む URI パスが正しく解析される
description: Core .NET ライブラリでの .NET 5 の破壊的変更について学習します。この変更後、Unix プラットフォームで非 ASCII 文字を含む絶対 URI パスによって正しく解析が行われるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 50e9b4597a5ac0b73732a38ce662037292777a03
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257415"
---
# <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="a7e82-103">Unix 上で ASCII 以外の文字を含む URI パスが正しく解析される</span><span class="sxs-lookup"><span data-stu-id="a7e82-103">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="a7e82-104"><xref:System.Uri?displayProperty=fullName> クラス内のバグが修正され、Unix プラットフォーム上で ASCII 以外の文字を含む絶対 URI パスが正しく解析されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a7e82-104">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

## <a name="change-description"></a><span data-ttu-id="a7e82-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="a7e82-105">Change description</span></span>

<span data-ttu-id="a7e82-106">以前のバージョンの .NET では、Unix プラットフォーム上で ASCII 以外の文字を含む絶対 URI パスが正しく解析されず、パスのセグメントに重複が生じます。</span><span class="sxs-lookup"><span data-stu-id="a7e82-106">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="a7e82-107">(絶対パスとは、"/" で始まるものです)。 .NET 5.0 ではこの解析の問題が修正されました。</span><span class="sxs-lookup"><span data-stu-id="a7e82-107">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="a7e82-108">以前のバージョンの .NET から .NET 5 以降に移行すると、<xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>、<xref:System.Uri.ToString?displayProperty=nameWithType>、およびその他の <xref:System.Uri> メンバーによって生成され出力される値は異なるものとなります。</span><span class="sxs-lookup"><span data-stu-id="a7e82-108">If you move from a previous version of .NET to .NET 5 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="a7e82-109">Unix 上で実行する場合は、次のコードの出力を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a7e82-109">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="a7e82-110">以前のバージョンの .NET での出力:</span><span class="sxs-lookup"><span data-stu-id="a7e82-110">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="a7e82-111">.NET 5 以降のバージョンでの出力:</span><span class="sxs-lookup"><span data-stu-id="a7e82-111">Output on .NET 5 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

## <a name="version-introduced"></a><span data-ttu-id="a7e82-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a7e82-112">Version introduced</span></span>

<span data-ttu-id="a7e82-113">5.0</span><span class="sxs-lookup"><span data-stu-id="a7e82-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a7e82-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="a7e82-114">Recommended action</span></span>

<span data-ttu-id="a7e82-115">重複したパス セグメントの発生が予期される、および明らかであるコードがある場合は、そのコードを削除できます。</span><span class="sxs-lookup"><span data-stu-id="a7e82-115">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a7e82-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a7e82-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
