---
description: '詳細情報: 方法 : 文字列内を検索する (Visual Basic)'
title: '方法: 文字列内を検索する'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: dab9faf91eef2e6d845805693227e1a6735ec796
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429729"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="9db65-103">方法 : 文字列内を検索する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9db65-103">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="9db65-104">この記事では、Visual Basic で文字列内を検索する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="9db65-104">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="9db65-105">例</span><span class="sxs-lookup"><span data-stu-id="9db65-105">Example</span></span>

<span data-ttu-id="9db65-106">この例では、<xref:System.String> オブジェクトに対して <xref:System.String.IndexOf%2A> メソッドを呼び出して、部分文字列が最初に出現した位置のインデックスを報告します。</span><span class="sxs-lookup"><span data-stu-id="9db65-106">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="9db65-107">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="9db65-107">Robust programming</span></span>

<span data-ttu-id="9db65-108"><xref:System.String.IndexOf%2A> メソッドは、最初に出現した部分文字列の最初の文字の位置を返します。</span><span class="sxs-lookup"><span data-stu-id="9db65-108">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="9db65-109">インデックスは 0 から始まります。つまり、文字列の最初の文字のインデックスは 0 になります。</span><span class="sxs-lookup"><span data-stu-id="9db65-109">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="9db65-110"><xref:System.String.IndexOf%2A> は、部分文字列が見つからない場合、-1 を返します。</span><span class="sxs-lookup"><span data-stu-id="9db65-110">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="9db65-111"><xref:System.String.IndexOf%2A> メソッドでは大文字と小文字が区別され、現在のカルチャが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9db65-111">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="9db65-112">最適なエラー制御を実現するために、[Try...Catch...Finally ステートメント](../../../language-reference/statements/try-catch-finally-statement.md)構成の `Try` ブロックで文字列検索を囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="9db65-112">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="9db65-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9db65-113">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="9db65-114">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="9db65-114">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="9db65-115">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="9db65-115">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="9db65-116">文字列</span><span class="sxs-lookup"><span data-stu-id="9db65-116">Strings</span></span>](index.md)
