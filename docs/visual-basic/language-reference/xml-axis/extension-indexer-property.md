---
description: '詳細情報: 拡張インデクサー プロパティ (Visual Basic)'
title: 拡張インデクサー プロパティ
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: ec165836f739db9a74ea266ebba32be5bb42cca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700326"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="770f8-103">拡張インデクサー プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="770f8-103">Extension Indexer Property (Visual Basic)</span></span>

<span data-ttu-id="770f8-104">コレクション内の個々の要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="770f8-104">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="770f8-105">構文</span><span class="sxs-lookup"><span data-stu-id="770f8-105">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="770f8-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="770f8-106">Parts</span></span>  
  
|<span data-ttu-id="770f8-107">用語</span><span class="sxs-lookup"><span data-stu-id="770f8-107">Term</span></span>|<span data-ttu-id="770f8-108">定義</span><span class="sxs-lookup"><span data-stu-id="770f8-108">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="770f8-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="770f8-109">Required.</span></span> <span data-ttu-id="770f8-110">クエリ可能なコレクション。</span><span class="sxs-lookup"><span data-stu-id="770f8-110">A queryable collection.</span></span> <span data-ttu-id="770f8-111">つまり、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> を実装するコレクション。</span><span class="sxs-lookup"><span data-stu-id="770f8-111">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="770f8-112">(</span><span class="sxs-lookup"><span data-stu-id="770f8-112">(</span></span>|<span data-ttu-id="770f8-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="770f8-113">Required.</span></span> <span data-ttu-id="770f8-114">インデクサー プロパティの先頭を表します。</span><span class="sxs-lookup"><span data-stu-id="770f8-114">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="770f8-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="770f8-115">Required.</span></span> <span data-ttu-id="770f8-116">コレクションの要素の 0 から始まる位置を指定する整数式。</span><span class="sxs-lookup"><span data-stu-id="770f8-116">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="770f8-117">)</span><span class="sxs-lookup"><span data-stu-id="770f8-117">)</span></span>|<span data-ttu-id="770f8-118">必須です。</span><span class="sxs-lookup"><span data-stu-id="770f8-118">Required.</span></span> <span data-ttu-id="770f8-119">インデクサー プロパティの末尾を表します。</span><span class="sxs-lookup"><span data-stu-id="770f8-119">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="770f8-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="770f8-120">Return Value</span></span>  

 <span data-ttu-id="770f8-121">コレクション内の指定した位置からのオブジェクト、または `Nothing` (インデックスが範囲外の場合)。</span><span class="sxs-lookup"><span data-stu-id="770f8-121">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="770f8-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="770f8-122">Remarks</span></span>  

 <span data-ttu-id="770f8-123">拡張インデクサー プロパティを使用して、コレクションの個別の要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="770f8-123">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="770f8-124">このインデクサー プロパティは、通常、XML 軸プロパティの出力で使用されます。</span><span class="sxs-lookup"><span data-stu-id="770f8-124">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="770f8-125">XML 子軸プロパティおよび XML 子孫軸プロパティは、<xref:System.Xml.Linq.XElement> オブジェクトのコレクションまたは属性値を返します。</span><span class="sxs-lookup"><span data-stu-id="770f8-125">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="770f8-126">拡張インデクサーのプロパティは、Visual Basic コンパイラによって、`ElementAtOrDefault` メソッドへの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="770f8-126">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="770f8-127">配列インデクサーとは異なり、`ElementAtOrDefault` メソッドは、インデックスが範囲外の場合に `Nothing` を返します。</span><span class="sxs-lookup"><span data-stu-id="770f8-127">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="770f8-128">この動作は、コレクション内の要素の数を簡単には判断できない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="770f8-128">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="770f8-129">このインデクサー プロパティは、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> を実装するコレクションの拡張プロパティと似ています。つまり、コレクションにインデクサーまたは既定のプロパティがない場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="770f8-129">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="770f8-130"><xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XAttribute> オブジェクト コレクションの最初の要素の値には、XML `Value` プロパティを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="770f8-130">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="770f8-131">詳細については、「[XML Value プロパティ](xml-value-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="770f8-131">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="770f8-132">例</span><span class="sxs-lookup"><span data-stu-id="770f8-132">Example</span></span>  

 <span data-ttu-id="770f8-133">次の例は、拡張インデクサーを使用して、<xref:System.Xml.Linq.XElement> オブジェクト コレクションの 2 番目の子ノードにアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="770f8-133">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="770f8-134">コレクションには子軸プロパティを使用してアクセスします。これにより、`contact` オブジェクトの `phone` という名前の子要素すべてが取得されます。</span><span class="sxs-lookup"><span data-stu-id="770f8-134">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="770f8-135">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="770f8-135">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="770f8-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="770f8-136">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="770f8-137">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="770f8-137">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="770f8-138">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="770f8-138">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="770f8-139">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="770f8-139">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="770f8-140">XML Value プロパティ</span><span class="sxs-lookup"><span data-stu-id="770f8-140">XML Value Property</span></span>](xml-value-property.md)
