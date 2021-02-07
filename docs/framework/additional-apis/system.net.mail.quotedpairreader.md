---
description: '詳細情報: QuotedPairReader クラス'
title: QuotedPairReader クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.QuotedPairReader
- System.Net.Mail.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 810a7b02948a1b7aa542a179563af9a6d79dd763
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699663"
---
# <a name="quotedpairreader-class"></a><span data-ttu-id="cfda0-103">QuotedPairReader クラス</span><span class="sxs-lookup"><span data-stu-id="cfda0-103">QuotedPairReader class</span></span>

<span data-ttu-id="cfda0-104">引用符で囲まれた文字列で引用符で囲まれた文字 (エスケープ) を決定します。</span><span class="sxs-lookup"><span data-stu-id="cfda0-104">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="cfda0-105">このクラスは継承できません。</span><span class="sxs-lookup"><span data-stu-id="cfda0-105">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="cfda0-106">このクラスは内部的なものであり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="cfda0-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="cfda0-107">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cfda0-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="cfda0-108">CountQuotedChars メソッド</span><span class="sxs-lookup"><span data-stu-id="cfda0-108">CountQuotedChars method</span></span>

<span data-ttu-id="cfda0-109">指定した文字列に含まれる、前に引用符で囲まれた複数の円記号を含む、連続する引用符で囲まれた文字の数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="cfda0-109">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="cfda0-110">たとえば、文字列とのインデックスを指定した場合、メソッドはを `a\\\b` `4` 返します。これは、 `4` `b` が引用符で囲まれており、その前に3つの円記号があるためです。</span><span class="sxs-lookup"><span data-stu-id="cfda0-110">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="cfda0-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cfda0-111">Parameters</span></span>

- <span data-ttu-id="cfda0-112">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="cfda0-112">`data` <xref:System.String></span></span>

  <span data-ttu-id="cfda0-113">連続する引用符で囲まれた文字をカウントするデータ文字列。</span><span class="sxs-lookup"><span data-stu-id="cfda0-113">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="cfda0-114">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="cfda0-114">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="cfda0-115">連続する引用符で囲まれた文字を含む、指定した文字列内の位置。</span><span class="sxs-lookup"><span data-stu-id="cfda0-115">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="cfda0-116">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="cfda0-116">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="cfda0-117">`true` Unicode 文字のエスケープを許可するにはそれ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="cfda0-117">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="cfda0-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="cfda0-118">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="cfda0-119">`0` 指定したインデックス位置にある文字がエスケープされない場合は。それ以外の場合は、の文字を含む、連続する引用符で囲まれた文字の数 `index` 。</span><span class="sxs-lookup"><span data-stu-id="cfda0-119">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="cfda0-120">例外</span><span class="sxs-lookup"><span data-stu-id="cfda0-120">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="cfda0-121">エスケープされた Unicode 文字が見つかりましたが、許可されていません。</span><span class="sxs-lookup"><span data-stu-id="cfda0-121">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="cfda0-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="cfda0-122">Requirements</span></span>

<span data-ttu-id="cfda0-123">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="cfda0-123">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="cfda0-124">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="cfda0-124">**Assembly:** System (in System.dll)</span></span>
