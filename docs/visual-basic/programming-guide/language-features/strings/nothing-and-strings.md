---
description: '詳細情報: Visual Basic の Nothing と文字列'
title: テキストと文字列
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: a32dd8b38033f1845f2ada87bf5f538d45fede18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424347"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="fbac5-103">Visual Basic の Nothing と文字列</span><span class="sxs-lookup"><span data-stu-id="fbac5-103">Nothing and Strings in Visual Basic</span></span>

<span data-ttu-id="fbac5-104">Visual Basic ランタイムと .NET Framework では、文字列に関する `Nothing` の評価が異なります。</span><span class="sxs-lookup"><span data-stu-id="fbac5-104">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="fbac5-105">Visual Basic ランタイムと .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fbac5-105">Visual Basic Runtime and the .NET Framework</span></span>  

 <span data-ttu-id="fbac5-106">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fbac5-106">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="fbac5-107">通常、Visual Basic ランタイムでは、`Nothing` が空の文字列 ("") として評価されます。</span><span class="sxs-lookup"><span data-stu-id="fbac5-107">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="fbac5-108">ただし、.NET Framework では実行されず、`Nothing` に対して文字列操作を実行しようとするたびに例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fbac5-108">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbac5-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbac5-109">See also</span></span>

- [<span data-ttu-id="fbac5-110">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="fbac5-110">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
