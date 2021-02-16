---
description: '詳細情報: Visual Basic での XML へのアクセス'
title: XML へのアクセス
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 2d77b2aa5f4136095ce5684976fe3ba03be7c28c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462660"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="75dbe-103">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="75dbe-103">Accessing XML in Visual Basic</span></span>

<span data-ttu-id="75dbe-104">Visual Basic には、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 構造体にアクセスして移動するための XML 軸プロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="75dbe-104">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="75dbe-105">これらのプロパティでは、XML 名を指定して、要素と属性にアクセスできる特殊な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-105">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="75dbe-106">次の表に、Visual Basic で XML 要素と属性にアクセスできる言語機能を一覧表示しています。</span><span class="sxs-lookup"><span data-stu-id="75dbe-106">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="75dbe-107">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="75dbe-107">XML Axis Properties</span></span>  
  
|<span data-ttu-id="75dbe-108">プロパティの説明</span><span class="sxs-lookup"><span data-stu-id="75dbe-108">Property description</span></span>|<span data-ttu-id="75dbe-109">例</span><span class="sxs-lookup"><span data-stu-id="75dbe-109">Example</span></span>|<span data-ttu-id="75dbe-110">説明</span><span class="sxs-lookup"><span data-stu-id="75dbe-110">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="75dbe-111">*子軸*</span><span class="sxs-lookup"><span data-stu-id="75dbe-111">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="75dbe-112">`contact` 要素の子要素であるすべての `phone` 要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-112">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="75dbe-113">*属性軸*</span><span class="sxs-lookup"><span data-stu-id="75dbe-113">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="75dbe-114">`phone` 要素のすべての `type` 属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-114">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="75dbe-115">*子孫軸*</span><span class="sxs-lookup"><span data-stu-id="75dbe-115">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="75dbe-116">`contacts` 要素のすべての `name` 要素を、それらが存在する階層の深さに関係なく、取得します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-116">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="75dbe-117">*拡張インデクサー*</span><span class="sxs-lookup"><span data-stu-id="75dbe-117">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="75dbe-118">シーケンスから最初の `name` 要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-118">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="75dbe-119">*value*</span><span class="sxs-lookup"><span data-stu-id="75dbe-119">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="75dbe-120">シーケンス内の最初のオブジェクトの文字列表現、またはシーケンスが空の場合は `Nothing` を取得します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-120">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="75dbe-121">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="75dbe-121">In This Section</span></span>  

 [<span data-ttu-id="75dbe-122">方法: XML 子孫要素にアクセスする</span><span class="sxs-lookup"><span data-stu-id="75dbe-122">How to: Access XML Descendant Elements</span></span>](how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="75dbe-123">子孫軸プロパティを使用して、指定した名前を持ち、指定した XML 要素の下に含まれているすべての XML 要素にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-123">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="75dbe-124">方法: XML 子要素にアクセスする</span><span class="sxs-lookup"><span data-stu-id="75dbe-124">How to: Access XML Child Elements</span></span>](how-to-access-xml-child-elements.md)  
 <span data-ttu-id="75dbe-125">子軸プロパティを使用して、XML 要素内で指定した名前を持つすべての XML 子要素にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-125">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="75dbe-126">方法: XML 属性にアクセスする</span><span class="sxs-lookup"><span data-stu-id="75dbe-126">How to: Access XML Attributes</span></span>](how-to-access-xml-attributes.md)  
 <span data-ttu-id="75dbe-127">属性軸プロパティを使用して、XML 要素内で指定した名前を持つすべての XML 属性にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-127">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="75dbe-128">方法: XML 名前空間プレフィックスを宣言して使用する</span><span class="sxs-lookup"><span data-stu-id="75dbe-128">How to: Declare and Use XML Namespace Prefixes</span></span>](how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="75dbe-129">XML 名前空間プレフィックスを宣言し、それを使用して XML 要素を作成し、アクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-129">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="75dbe-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="75dbe-130">Related Sections</span></span>  

 [<span data-ttu-id="75dbe-131">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="75dbe-131">XML Axis Properties</span></span>](../../../language-reference/xml-axis/index.md)  
 <span data-ttu-id="75dbe-132">さまざまな XML アクセス プロパティについて説明するセクションへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-132">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="75dbe-133">Visual Basic における LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="75dbe-133">Overview of LINQ to XML in Visual Basic</span></span>](overview-of-linq-to-xml.md)  
 <span data-ttu-id="75dbe-134">Visual Basic での [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の使用の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-134">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="75dbe-135">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="75dbe-135">Creating XML in Visual Basic</span></span>](creating-xml.md)  
 <span data-ttu-id="75dbe-136">Visual Basic での XML リテラルの使用の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-136">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="75dbe-137">Visual Basic での XML の操作</span><span class="sxs-lookup"><span data-stu-id="75dbe-137">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)  
 <span data-ttu-id="75dbe-138">Visual Basic での XML の読み込みと変更に関するセクションへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-138">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="75dbe-139">XML</span><span class="sxs-lookup"><span data-stu-id="75dbe-139">XML</span></span>](index.md)  
 <span data-ttu-id="75dbe-140">Visual Basic での [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の使用方法を説明するセクションへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="75dbe-140">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
