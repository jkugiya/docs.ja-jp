---
description: '詳細情報: 表記規則とコード規則 (Visual Basic)'
title: 表記規則とコード規則
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: 44e8445bb56f4f0c8b2f4eedddecda46ffcebb68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768806"
---
# <a name="typographic-and-code-conventions-visual-basic"></a><span data-ttu-id="d44c9-103">表記規則とコード規則 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d44c9-103">Typographic and Code Conventions (Visual Basic)</span></span>

<span data-ttu-id="d44c9-104">Visual Basic のドキュメントでは、次の表記規則とコード規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="d44c9-104">Visual Basic documentation uses the following typographic and code conventions.</span></span>  
  
## <a name="typographic-conventions"></a><span data-ttu-id="d44c9-105">表記規則</span><span class="sxs-lookup"><span data-stu-id="d44c9-105">Typographic Conventions</span></span>  
  
|<span data-ttu-id="d44c9-106">例</span><span class="sxs-lookup"><span data-stu-id="d44c9-106">Example</span></span>|<span data-ttu-id="d44c9-107">説明</span><span class="sxs-lookup"><span data-stu-id="d44c9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d44c9-108">`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`</span><span class="sxs-lookup"><span data-stu-id="d44c9-108">`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`</span></span>|<span data-ttu-id="d44c9-109">言語固有のキーワードとランタイム メンバーは、先頭文字が大文字であり、この例のように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-109">Language-specific keywords and runtime members have initial uppercase letters and are formatted as shown in this example.</span></span>|  
|<span data-ttu-id="d44c9-110">**SmallProject**、**ButtonCollection**</span><span class="sxs-lookup"><span data-stu-id="d44c9-110">**SmallProject**, **ButtonCollection**</span></span>|<span data-ttu-id="d44c9-111">入力を求められる語句は、この例のように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-111">Words and phrases you are instructed to type are formatted as shown in this example.</span></span>|  
|[<span data-ttu-id="d44c9-112">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="d44c9-112">Module Statement</span></span>](statements/module-statement.md)|<span data-ttu-id="d44c9-113">別のヘルプ ページにアクセスするためにクリックするリンクは、この例のように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-113">Links you can click to go to another Help page are formatted as shown in this example.</span></span>|  
|<span data-ttu-id="d44c9-114">*object*、*variableName*、`argumentList`</span><span class="sxs-lookup"><span data-stu-id="d44c9-114">*object*, *variableName*, `argumentList`</span></span>|<span data-ttu-id="d44c9-115">指定する情報のプレースホルダーは、この例のように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-115">Placeholders for information that you supply are formatted as shown in this example.</span></span>|  
|<span data-ttu-id="d44c9-116">[ Shadows ]、[ *expressionList* ]</span><span class="sxs-lookup"><span data-stu-id="d44c9-116">[ Shadows ], [ *expressionList* ]</span></span>|<span data-ttu-id="d44c9-117">構文では、省略可能な項目は角かっこで囲まれています。</span><span class="sxs-lookup"><span data-stu-id="d44c9-117">In syntax, optional items are enclosed in brackets.</span></span>|  
|<span data-ttu-id="d44c9-118">{ `Public` &#124; `Friend` &#124; `Private` }</span><span class="sxs-lookup"><span data-stu-id="d44c9-118">{ `Public` &#124; `Friend` &#124; `Private` }</span></span>|<span data-ttu-id="d44c9-119">構文で、2 つ以上の項目のいずれかを選択する必要がある場合、項目は中かっこで囲まれ、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-119">In syntax, when you must make a choice between two or more items, the items are enclosed in braces and separated by vertical bars.</span></span><br /><br /> <span data-ttu-id="d44c9-120">項目を 1 つだけ選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d44c9-120">You must select one, and only one, of the items.</span></span>|  
|<span data-ttu-id="d44c9-121">[ `Protected` &#124; `Friend` ]</span><span class="sxs-lookup"><span data-stu-id="d44c9-121">[ `Protected` &#124; `Friend` ]</span></span>|<span data-ttu-id="d44c9-122">構文で、2 つ以上の項目から任意で選択できる場合、項目は角かっこで囲まれ、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-122">In syntax, when you have the option of selecting between two or more items, the items are enclosed in square brackets and separated by vertical bars.</span></span><br /><br /> <span data-ttu-id="d44c9-123">項目は自由に組み合わせて選択でき、項目をまったく選択しないこともできます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-123">You can select any combination of the items, or no item.</span></span>|  
|<span data-ttu-id="d44c9-124">[{ `ByVal` &#124; `ByRef` }]</span><span class="sxs-lookup"><span data-stu-id="d44c9-124">[{ `ByVal` &#124; `ByRef` }]</span></span>|<span data-ttu-id="d44c9-125">構文で、項目を 1 つのみ選択できるが、項目を完全に省略することもできる場合、これらの項目は、中かっこで囲まれて角かっこで囲まれ、縦棒で区切られます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-125">In syntax, when you can select no more than one item, but you can also omit the items completely, the items are enclosed in square brackets surrounded by braces and separated by vertical bars.</span></span>|  
|<span data-ttu-id="d44c9-126">*memberName* 1、*memberName* 2、*memberName* 3</span><span class="sxs-lookup"><span data-stu-id="d44c9-126">*memberName* 1, *memberName* 2, *memberName* 3</span></span>|<span data-ttu-id="d44c9-127">同じプレースホルダーの複数のインスタンスは、例に示すように、添字により区別されます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-127">Multiple instances of the same placeholder are differentiated by subscripts, as shown in the example.</span></span>|  
|<span data-ttu-id="d44c9-128">*memberName1*</span><span class="sxs-lookup"><span data-stu-id="d44c9-128">*memberName1*</span></span><br /><br /> <span data-ttu-id="d44c9-129">...</span><span class="sxs-lookup"><span data-stu-id="d44c9-129">...</span></span><br /><br /> <span data-ttu-id="d44c9-130">*memberNameN*</span><span class="sxs-lookup"><span data-stu-id="d44c9-130">*memberNameN*</span></span>|<span data-ttu-id="d44c9-131">構文では、省略記号 (...) を使用して、省略記号の直前にある種類の項目の数が不定であることを示します。</span><span class="sxs-lookup"><span data-stu-id="d44c9-131">In syntax, an ellipsis (...) is used to indicate an indefinite number of items of the kind immediately in front of the ellipsis.</span></span><br /><br /> <span data-ttu-id="d44c9-132">コード内の省略記号は、わかりやすくするために省略されたコードを示します。</span><span class="sxs-lookup"><span data-stu-id="d44c9-132">In code, ellipses signify code omitted for the sake of clarity.</span></span>|  
|<span data-ttu-id="d44c9-133">ESC、ENTER</span><span class="sxs-lookup"><span data-stu-id="d44c9-133">ESC, ENTER</span></span>|<span data-ttu-id="d44c9-134">キーボードのキー名とキー シーケンスは、すべて大文字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-134">Key names and key sequences on the keyboard appear in all uppercase letters.</span></span>|  
|<span data-ttu-id="d44c9-135">Alt + F1</span><span class="sxs-lookup"><span data-stu-id="d44c9-135">ALT+F1</span></span>|<span data-ttu-id="d44c9-136">各キー名の間にプラス記号 (+) が表示されている場合は、一方のキーを押しながらもう一方のキーを押す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d44c9-136">When plus signs (+) appear between key names, you must hold down one key while pressing the other.</span></span> <span data-ttu-id="d44c9-137">たとえば、ALT + F1 は、ALT キーを押しながら F1 キーを押すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="d44c9-137">For example, ALT+F1 means hold down the ALT key while pressing the F1 key.</span></span>|  
  
## <a name="code-conventions"></a><span data-ttu-id="d44c9-138">コード規則</span><span class="sxs-lookup"><span data-stu-id="d44c9-138">Code Conventions</span></span>  
  
|<span data-ttu-id="d44c9-139">例</span><span class="sxs-lookup"><span data-stu-id="d44c9-139">Example</span></span>|<span data-ttu-id="d44c9-140">説明</span><span class="sxs-lookup"><span data-stu-id="d44c9-140">Description</span></span>|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|<span data-ttu-id="d44c9-141">コード サンプルは固定ピッチ フォントで表示され、次の例のように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-141">Code samples appear in a fixed-pitch font and are formatted as shown in this example.</span></span>|  
|<span data-ttu-id="d44c9-142">上記のステートメントは、`sampleString` の値を "Hello, world!" に設定します</span><span class="sxs-lookup"><span data-stu-id="d44c9-142">The previous statement sets the value of `sampleString` to "Hello, world!"</span></span>|<span data-ttu-id="d44c9-143">次の例に示すように、説明文のコード要素は固定ピッチ フォントで表示されます。</span><span class="sxs-lookup"><span data-stu-id="d44c9-143">Code elements in explanatory text appear in a fixed-pitch font, as shown in this example.</span></span>|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|<span data-ttu-id="d44c9-144">コードのコメントは、アポストロフィ (') または REM キーワードで始まります。</span><span class="sxs-lookup"><span data-stu-id="d44c9-144">Code comments are introduced by an apostrophe (') or the REM keyword.</span></span>|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|<span data-ttu-id="d44c9-145">行の末尾にスペースに続いてアンダースコア (_) があるは、ステートメントが次の行に続くことを示します。</span><span class="sxs-lookup"><span data-stu-id="d44c9-145">A space followed by an underscore ( _) at the end of a line indicates that the statement continues on the following line.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d44c9-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="d44c9-146">See also</span></span>

- [<span data-ttu-id="d44c9-147">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="d44c9-147">Visual Basic Language Reference</span></span>](index.md)
- [<span data-ttu-id="d44c9-148">キーワード</span><span class="sxs-lookup"><span data-stu-id="d44c9-148">Keywords</span></span>](keywords/index.md)
- [<span data-ttu-id="d44c9-149">Visual Basic ランタイム ライブラリのメンバー</span><span class="sxs-lookup"><span data-stu-id="d44c9-149">Visual Basic Runtime Library Members</span></span>](runtime-library-members.md)
- [<span data-ttu-id="d44c9-150">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="d44c9-150">Visual Basic Naming Conventions</span></span>](../programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="d44c9-151">方法: コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="d44c9-151">How to: Break and Combine Statements in Code</span></span>](../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="d44c9-152">コード内のコメント</span><span class="sxs-lookup"><span data-stu-id="d44c9-152">Comments in Code</span></span>](../programming-guide/program-structure/comments-in-code.md)
