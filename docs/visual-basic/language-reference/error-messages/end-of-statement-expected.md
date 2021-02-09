---
description: '詳細情報: BC30205:ステートメントの終わりを指定してください。'
title: ステートメントの終わりを指定してください。
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: a3f309a4674f6de34c0be8abfef31e293a10dec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796549"
---
# <a name="bc30205-end-of-statement-expected"></a><span data-ttu-id="966ce-103">BC30205:ステートメントの終わりを指定してください。</span><span class="sxs-lookup"><span data-stu-id="966ce-103">BC30205: End of statement expected</span></span>

<span data-ttu-id="966ce-104">ステートメントは構文的に完全ですが、ステートメントを完了する要素の後に追加のプログラミング要素が続いています。</span><span class="sxs-lookup"><span data-stu-id="966ce-104">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="966ce-105">すべてのステートメントの末尾には、行終端記号が必要です。</span><span class="sxs-lookup"><span data-stu-id="966ce-105">A line terminator is required at the end of every statement.</span></span>

 <span data-ttu-id="966ce-106">行終端記号は、Visual Basic のソース ファイルの文字を行に分割します。</span><span class="sxs-lookup"><span data-stu-id="966ce-106">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="966ce-107">行終端記号の例としては、Unicode 復帰文字 (&HD)、Unicode 改行文字 (&HA)、および Unicode 復帰文字とその後の Unicode 改行文字があります。</span><span class="sxs-lookup"><span data-stu-id="966ce-107">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="966ce-108">行終端記号の詳細については、[Visual Basic 言語の仕様](~/_vblang/spec/lexical-grammar.md#line-terminators)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="966ce-108">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>

 <span data-ttu-id="966ce-109">**エラー ID:** BC30205</span><span class="sxs-lookup"><span data-stu-id="966ce-109">**Error ID:** BC30205</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="966ce-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="966ce-110">To correct this error</span></span>

1. <span data-ttu-id="966ce-111">2 つの異なるステートメントが誤って同じ行に配置されていないかを確認します。</span><span class="sxs-lookup"><span data-stu-id="966ce-111">Check to see if two different statements have inadvertently been put on the same line.</span></span>

2. <span data-ttu-id="966ce-112">行終端記号を、ステートメントを完了する要素の後に挿入します。</span><span class="sxs-lookup"><span data-stu-id="966ce-112">Insert a line terminator after the element that completes the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="966ce-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="966ce-113">See also</span></span>

- [<span data-ttu-id="966ce-114">方法: コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="966ce-114">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="966ce-115">ステートメント</span><span class="sxs-lookup"><span data-stu-id="966ce-115">Statements</span></span>](../../programming-guide/language-features/statements.md)
