---
description: '詳細情報: プログラム構造とコード規則 (Visual Basic)'
title: プログラム構造とコード規則
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
ms.openlocfilehash: 7d4202ead0550cf54a80eac89c4a4274a22d0315
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468487"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="3fa0b-103">プログラム構造とコード規則 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fa0b-103">Program Structure and Code Conventions (Visual Basic)</span></span>

<span data-ttu-id="3fa0b-104">このセクションでは、一般的な Visual Basic プログラムの構造を紹介します。また、単純な Visual Basic プログラム "Hello World" を示し、Visual Basic のコード規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-104">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="3fa0b-105">コード規則は、プログラムのロジックではなくプログラムの物理的な構造と外観に焦点を合わせた提案です。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-105">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="3fa0b-106">コード規則に従うと、コードの読み取り、理解、保守が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-106">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="3fa0b-107">コード規則には、以下の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-107">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="3fa0b-108">コードのラベル付けとコメント付けに関する標準化された書式</span><span class="sxs-lookup"><span data-stu-id="3fa0b-108">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="3fa0b-109">コードのスペーシング、書式指定、およびインデント設定に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="3fa0b-109">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="3fa0b-110">オブジェクト、変数、およびプロシージャの名前付け規則</span><span class="sxs-lookup"><span data-stu-id="3fa0b-110">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="3fa0b-111">以下のトピックでは、Visual Basic プログラムの一連のプログラミング ガイドラインを適切な使用例と共に示します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-111">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3fa0b-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3fa0b-112">In This Section</span></span>  

 [<span data-ttu-id="3fa0b-113">Visual Basic プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="3fa0b-113">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="3fa0b-114">Visual Basic プログラムを構成する要素の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-114">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="3fa0b-115">Visual Basic の Main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3fa0b-115">Main Procedure in Visual Basic</span></span>](main-procedure.md)  
 <span data-ttu-id="3fa0b-116">アプリケーションの開始点となり、アプリケーションの総合的な制御を行うプロシージャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-116">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="3fa0b-117">参照と Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="3fa0b-117">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)  
 <span data-ttu-id="3fa0b-118">他のアセンブリのオブジェクトを参照する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-118">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="3fa0b-119">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="3fa0b-119">Namespaces in Visual Basic</span></span>](namespaces.md)  
 <span data-ttu-id="3fa0b-120">アセンブリ内のオブジェクトが名前空間でどのように編成されているのかを説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-120">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="3fa0b-121">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="3fa0b-121">Visual Basic Naming Conventions</span></span>](naming-conventions.md)  
 <span data-ttu-id="3fa0b-122">プロシージャ、定数、変数、引数、およびオブジェクトの名前付けに関する一般的なガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-122">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="3fa0b-123">Visual Basic のコーディング規則</span><span class="sxs-lookup"><span data-stu-id="3fa0b-123">Visual Basic Coding Conventions</span></span>](coding-conventions.md)  
 <span data-ttu-id="3fa0b-124">このドキュメントのサンプルを開発するときに使用したガイドラインについてレビューします。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-124">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="3fa0b-125">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="3fa0b-125">Conditional Compilation</span></span>](conditional-compilation.md)  
 <span data-ttu-id="3fa0b-126">特定のコード ブロックを選択的にコンパイルし、その間は他のコード ブロックを無視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-126">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="3fa0b-127">方法: コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="3fa0b-127">How to: Break and Combine Statements in Code</span></span>](how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="3fa0b-128">長いステートメントを複数の行に分割する方法と、複数の短いステートメントを 1 行に結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-128">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="3fa0b-129">方法: コードのセクションを折りたたんで非表示にする</span><span class="sxs-lookup"><span data-stu-id="3fa0b-129">How to: Collapse and Hide Sections of Code</span></span>](how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="3fa0b-130">Visual Basic のコード エディターでコードのセクションを折りたたんで非表示にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-130">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="3fa0b-131">方法: ステートメントへのラベル付け</span><span class="sxs-lookup"><span data-stu-id="3fa0b-131">How to: Label Statements</span></span>](how-to-label-statements.md)  
 <span data-ttu-id="3fa0b-132">`On Error Goto` などのステートメントで使用するために、コード行に識別用のマーキングをする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-132">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="3fa0b-133">コード内の特殊文字</span><span class="sxs-lookup"><span data-stu-id="3fa0b-133">Special Characters in Code</span></span>](special-characters-in-code.md)  
 <span data-ttu-id="3fa0b-134">英数字以外の文字を使用する方法と場所について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-134">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="3fa0b-135">コード内のコメント</span><span class="sxs-lookup"><span data-stu-id="3fa0b-135">Comments in Code</span></span>](comments-in-code.md)  
 <span data-ttu-id="3fa0b-136">説明的なコメントをコードに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-136">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="3fa0b-137">コード内の要素名としてのキーワード</span><span class="sxs-lookup"><span data-stu-id="3fa0b-137">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)  
 <span data-ttu-id="3fa0b-138">角かっこ (`[]`) を使用して、Visual Basic キーワードでもある変数名を区切る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-138">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="3fa0b-139">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="3fa0b-139">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)  
 <span data-ttu-id="3fa0b-140">Visual Basic プログラムの要素を参照するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-140">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="3fa0b-141">Visual Basic の制限事項</span><span class="sxs-lookup"><span data-stu-id="3fa0b-141">Visual Basic Limitations</span></span>](limitations.md)  
 <span data-ttu-id="3fa0b-142">Visual Basic におけるコーディングの既知の制限の排除について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-142">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3fa0b-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fa0b-143">Related Sections</span></span>  

 [<span data-ttu-id="3fa0b-144">表記規則とコード規則</span><span class="sxs-lookup"><span data-stu-id="3fa0b-144">Typographic and Code Conventions</span></span>](../../language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="3fa0b-145">Visual Basic の標準的なコーディング規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-145">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="3fa0b-146">コードの作成</span><span class="sxs-lookup"><span data-stu-id="3fa0b-146">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="3fa0b-147">コードの記述と管理を容易にする機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa0b-147">Describes features that make it easier for you to write and manage your code.</span></span>
