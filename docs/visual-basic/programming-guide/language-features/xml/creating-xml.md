---
description: '詳細情報: Visual Basic での XML の作成'
title: XML の作成
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 9511253791720d1f45e00669b0abc41a45237f63
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431647"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="dd8d0-103">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="dd8d0-103">Creating XML in Visual Basic</span></span>

<span data-ttu-id="dd8d0-104">Visual Basic では、コードで *XML リテラル* を直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-104">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="dd8d0-105">XML リテラル構文は [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] オブジェクトを表し、XML 1.0 構文に似ています。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-105">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="dd8d0-106">これにより、コードが最終的な XML と同じ構造を持つため、XML 要素、ドキュメント、およびフラグメントをプログラムで簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-106">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd8d0-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="dd8d0-107">In This Section</span></span>  
  
|<span data-ttu-id="dd8d0-108">用語</span><span class="sxs-lookup"><span data-stu-id="dd8d0-108">Term</span></span>|<span data-ttu-id="dd8d0-109">定義</span><span class="sxs-lookup"><span data-stu-id="dd8d0-109">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="dd8d0-110">XML リテラルの概要</span><span class="sxs-lookup"><span data-stu-id="dd8d0-110">XML Literals Overview</span></span>](xml-literals-overview.md)|<span data-ttu-id="dd8d0-111">XML リテラルの概要と、それらが [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] とどのように関連しているかを説明します。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-111">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="dd8d0-112">XML での埋め込み式</span><span class="sxs-lookup"><span data-stu-id="dd8d0-112">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)|<span data-ttu-id="dd8d0-113">XML リテラルでの埋め込み式の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-113">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="dd8d0-114">方法: XML リテラルを作成する</span><span class="sxs-lookup"><span data-stu-id="dd8d0-114">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)|<span data-ttu-id="dd8d0-115">XML リテラルを使用して、コードで XML 要素を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-115">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="dd8d0-116">XML リテラルでの空白文字</span><span class="sxs-lookup"><span data-stu-id="dd8d0-116">White Space in XML Literals</span></span>](white-space-in-xml-literals.md)|<span data-ttu-id="dd8d0-117">Visual Basic で XML リテラルの空白を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-117">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="dd8d0-118">XML リテラルと XML 1.0 仕様</span><span class="sxs-lookup"><span data-stu-id="dd8d0-118">XML Literals and the XML 1.0 Specification</span></span>](xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="dd8d0-119">Visual Basic の XML リテラル構文が XML 1.0 仕様とどのように関連しているかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-119">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="dd8d0-120">方法: XML リテラルに式を埋め込む</span><span class="sxs-lookup"><span data-stu-id="dd8d0-120">How to: Embed Expressions in XML Literals</span></span>](how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="dd8d0-121">XML リテラルで埋め込み式を使用して、実行時にコンテンツを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-121">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="dd8d0-122">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="dd8d0-122">Names of Declared XML Elements and Attributes</span></span>](names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="dd8d0-123">XML 要素と属性に名前を付ける場合のガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dd8d0-123">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd8d0-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd8d0-124">See also</span></span>

- [<span data-ttu-id="dd8d0-125">XML</span><span class="sxs-lookup"><span data-stu-id="dd8d0-125">XML</span></span>](index.md)
