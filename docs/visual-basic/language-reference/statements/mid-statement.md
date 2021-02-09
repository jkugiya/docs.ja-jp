---
description: '詳細情報: Mid ステートメント'
title: Mid ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: 29cf933cb38fc6ef831570d0940b481abf9cfecf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768884"
---
# <a name="mid-statement"></a><span data-ttu-id="1ff57-103">Mid ステートメント</span><span class="sxs-lookup"><span data-stu-id="1ff57-103">Mid Statement</span></span>

<span data-ttu-id="1ff57-104">`String` 変数内の指定した数の文字を別の文字列の文字に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1ff57-104">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff57-105">構文</span><span class="sxs-lookup"><span data-stu-id="1ff57-105">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="1ff57-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="1ff57-106">Parts</span></span>  

 `Target`  
 <span data-ttu-id="1ff57-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="1ff57-107">Required.</span></span> <span data-ttu-id="1ff57-108">変更する `String` 変数の名前。</span><span class="sxs-lookup"><span data-stu-id="1ff57-108">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="1ff57-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="1ff57-109">Required.</span></span> <span data-ttu-id="1ff57-110">`Integer` 式。</span><span class="sxs-lookup"><span data-stu-id="1ff57-110">`Integer` expression.</span></span> <span data-ttu-id="1ff57-111">テキストの置換を開始する `Target` の文字の位置。</span><span class="sxs-lookup"><span data-stu-id="1ff57-111">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="1ff57-112">`Start` は 1 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ff57-112">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="1ff57-113">任意。</span><span class="sxs-lookup"><span data-stu-id="1ff57-113">Optional.</span></span> <span data-ttu-id="1ff57-114">`Integer` 式。</span><span class="sxs-lookup"><span data-stu-id="1ff57-114">`Integer` expression.</span></span> <span data-ttu-id="1ff57-115">置換する文字数。</span><span class="sxs-lookup"><span data-stu-id="1ff57-115">Number of characters to replace.</span></span> <span data-ttu-id="1ff57-116">省略した場合、`String` のすべてが使われます。</span><span class="sxs-lookup"><span data-stu-id="1ff57-116">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="1ff57-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="1ff57-117">Required.</span></span> <span data-ttu-id="1ff57-118">`Target` の一部を置き換える `String` 式。</span><span class="sxs-lookup"><span data-stu-id="1ff57-118">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="1ff57-119">例外</span><span class="sxs-lookup"><span data-stu-id="1ff57-119">Exceptions</span></span>  
  
|<span data-ttu-id="1ff57-120">例外の種類</span><span class="sxs-lookup"><span data-stu-id="1ff57-120">Exception type</span></span>|<span data-ttu-id="1ff57-121">条件</span><span class="sxs-lookup"><span data-stu-id="1ff57-121">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="1ff57-122">`Start` <= 0 または `Length` < 0。</span><span class="sxs-lookup"><span data-stu-id="1ff57-122">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ff57-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="1ff57-123">Remarks</span></span>  

 <span data-ttu-id="1ff57-124">置換される文字数は、常に `Target` の文字数以下です。</span><span class="sxs-lookup"><span data-stu-id="1ff57-124">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="1ff57-125">Visual Basic には <xref:Microsoft.VisualBasic.Strings.Mid%2A> 関数と `Mid` ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="1ff57-125">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="1ff57-126">これらの要素は、どちらも文字列内の指定した数の文字に対して操作しますが、`Mid` 関数では文字が返され、`Mid` ステートメントでは文字が置換されます。</span><span class="sxs-lookup"><span data-stu-id="1ff57-126">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="1ff57-127">詳細については、「<xref:Microsoft.VisualBasic.Strings.Mid%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ff57-127">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ff57-128">以前のバージョンの Visual Basic の `MidB` ステートメントでは、文字ではなく、バイト単位で部分文字列が置換されます。</span><span class="sxs-lookup"><span data-stu-id="1ff57-128">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="1ff57-129">それは主に、2 バイト文字セット (DBCS) アプリケーションで文字列を変換するために使用します。</span><span class="sxs-lookup"><span data-stu-id="1ff57-129">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="1ff57-130">すべての Visual Basic の文字列は Unicode 形式であり、`MidB` はサポートされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1ff57-130">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ff57-131">例</span><span class="sxs-lookup"><span data-stu-id="1ff57-131">Example</span></span>  

 <span data-ttu-id="1ff57-132">この例では、`Mid` ステートメントを使用して、String 変数の指定された数の文字を別の文字列からの文字に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1ff57-132">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="1ff57-133">必要条件</span><span class="sxs-lookup"><span data-stu-id="1ff57-133">Requirements</span></span>  

 <span data-ttu-id="1ff57-134">**名前空間:** [Microsoft.VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="1ff57-134">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="1ff57-135">**モジュール:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="1ff57-135">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="1ff57-136">**アセンブリ:** Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="1ff57-136">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff57-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ff57-137">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="1ff57-138">文字列</span><span class="sxs-lookup"><span data-stu-id="1ff57-138">Strings</span></span>](../../programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="1ff57-139">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="1ff57-139">Introduction to Strings in Visual Basic</span></span>](../../programming-guide/language-features/strings/introduction-to-strings.md)
