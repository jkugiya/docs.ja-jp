---
description: '詳細情報: 0 から始まる文字列アクセスと1 から始まる文字列アクセスの比較 (Visual Basic)'
title: 0 から始まる文字列アクセスと1 から始まる文字列アクセスの比較
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: adab6954c4329ae0a547d136f26f6c3115dc5890
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463833"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="16258-103">0 から始まる文字列アクセスと1 から始まる文字列アクセスの比較 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16258-103">Zero-based vs. One-based String Access in Visual Basic</span></span>

<span data-ttu-id="16258-104">このトピックでは、Visual Basic と .NET Framework が文字列内の文字へのアクセスを提供する方法を比較します。</span><span class="sxs-lookup"><span data-stu-id="16258-104">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="16258-105">.NET Framework では、文字列内の文字にアクセスする際に、常に 0 から始まるアクセスが提供されます。一方、Visual Basic では、関数に応じて、0 から始まるアクセスと 1 から始まるアクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="16258-105">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="16258-106">1 から開始</span><span class="sxs-lookup"><span data-stu-id="16258-106">One-Based</span></span>  

 <span data-ttu-id="16258-107">1 から始まる Visual Basic 関数の例として、`Mid` 関数について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="16258-107">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="16258-108">これは、位置 1 から始めて、部分文字列が始まる文字位置を示す引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="16258-108">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="16258-109">.NET Framework の <xref:System.String.Substring%2A?displayProperty=nameWithType> メソッドは、位置 0 から始めて、文字列内の部分文字列が始まる文字のインデックスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="16258-109">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="16258-110">したがって、文字列 "ABCDE" がある場合、個々の文字に付けられる番号は、`Mid` 関数で使用する際には 1,2,3,4,5 ですが、<xref:System.String.Substring%2A?displayProperty=nameWithType> メソッドで使用する際には 0,1,2,3,4 になります。</span><span class="sxs-lookup"><span data-stu-id="16258-110">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="16258-111">0 から開始</span><span class="sxs-lookup"><span data-stu-id="16258-111">Zero-Based</span></span>  

 <span data-ttu-id="16258-112">0 から始まる Visual Basic 関数の例として、`Split` 関数について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="16258-112">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="16258-113">これは、文字列を分割し、部分文字列を含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="16258-113">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="16258-114">.NET Framework の <xref:System.String.Split%2A?displayProperty=nameWithType> メソッドも文字列を分割し、部分文字列を含む配列を返します。</span><span class="sxs-lookup"><span data-stu-id="16258-114">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="16258-115">`Split` 関数と <xref:System.String.Split%2A> メソッドは .NET Framework の配列を返すため、これらは 0 から始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="16258-115">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16258-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="16258-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="16258-117">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="16258-117">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
