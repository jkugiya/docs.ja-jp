---
description: '詳細情報: DOM の要素ノードからの属性の削除'
title: DOM の要素ノードからの属性の削除
ms.date: 03/30/2017
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: a1e15f8358db6723d99194975cad2d121f6d48c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783132"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a><span data-ttu-id="17e02-103">DOM の要素ノードからの属性の削除</span><span class="sxs-lookup"><span data-stu-id="17e02-103">Removing Attributes from an Element Node in the DOM</span></span>

<span data-ttu-id="17e02-104">属性を削除するには、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="17e02-104">There are many ways to remove attributes.</span></span> <span data-ttu-id="17e02-105">その 1 つとして、属性コレクションから属性を削除する方法があります。</span><span class="sxs-lookup"><span data-stu-id="17e02-105">One technique is to remove them from the attribute collection.</span></span> <span data-ttu-id="17e02-106">属性コレクションから属性を削除するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="17e02-106">To do this, the following steps are performed:</span></span>  
  
1. <span data-ttu-id="17e02-107">`XmlAttributeCollection attrs = elem.Attributes;` を使用して要素から属性コレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="17e02-107">Get the attribute collection from the element using `XmlAttributeCollection attrs = elem.Attributes;`.</span></span>  
  
2. <span data-ttu-id="17e02-108">属性コレクションから属性を削除するには、次の 3 つのメソッドのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="17e02-108">Remove the attribute from the attribute collection using one of three methods:</span></span>  
  
    - <span data-ttu-id="17e02-109"><xref:System.Xml.XmlAttributeCollection.Remove%2A> メソッドを使用して、特定の属性を削除する。</span><span class="sxs-lookup"><span data-stu-id="17e02-109">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> to remove a specific attribute.</span></span>  
  
    - <span data-ttu-id="17e02-110"><xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> メソッドを使用して、コレクションからずべての属性を削除し、属性のない要素を残す。</span><span class="sxs-lookup"><span data-stu-id="17e02-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> to remove all attributes from the collection and leave the element with no attributes.</span></span>  
  
    - <span data-ttu-id="17e02-111"><xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> メソッドを使用して、コレクションのインデックス番号を使用して 1 つの属性を属性コレクションから削除する。</span><span class="sxs-lookup"><span data-stu-id="17e02-111">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> to remove an attribute from the attribute collection by using its index number.</span></span>  
  
 <span data-ttu-id="17e02-112">要素ノードから属性を削除するには、次のメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="17e02-112">The following methods remove attributes from the element node.</span></span>  
  
- <span data-ttu-id="17e02-113"><xref:System.Xml.XmlElement.RemoveAllAttributes%2A> メソッドを使用して、属性のコレクションを削除する。</span><span class="sxs-lookup"><span data-stu-id="17e02-113">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> to remove the attribute collection.</span></span>  
  
- <span data-ttu-id="17e02-114"><xref:System.Xml.XmlElement.RemoveAttribute%2A> メソッドを使用して、名前を指定して単一の属性をコレクションから削除する。</span><span class="sxs-lookup"><span data-stu-id="17e02-114">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> to remove a single attribute by name from the collection.</span></span>  
  
- <span data-ttu-id="17e02-115"><xref:System.Xml.XmlElement.RemoveAttributeAt%2A> メソッドを使用して、インデックス番号を指定して単一の属性をコレクションから削除する。</span><span class="sxs-lookup"><span data-stu-id="17e02-115">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> to remove a single attribute by index number from the collection.</span></span>  
  
 <span data-ttu-id="17e02-116">もう 1 つの方法として、要素を取得し、属性コレクションから属性を取得して、属性ノードを直接削除する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="17e02-116">One more alternative is to get the element, get the attribute from the attribute collection, and remove the attribute node directly.</span></span> <span data-ttu-id="17e02-117">属性コレクションから属性を取得するには、名前 (`XmlAttribute attr = attrs["attr_name"];`)、インデックス (`XmlAttribute attr = attrs[0];`)、または名前空間を指定した完全修飾名 (`XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="17e02-117">To get the attribute from the attribute collection, you can use a name, `XmlAttribute attr = attrs["attr_name"];`, an index `XmlAttribute attr = attrs[0];`, or by fully qualifying the name with the namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span></span>  
  
 <span data-ttu-id="17e02-118">既定の属性としてドキュメント型定義 (DTD) に定義されている属性を削除するときは、使用するメソッドにかかわらず、特別な制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="17e02-118">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the document type definition (DTD).</span></span> <span data-ttu-id="17e02-119">既定の属性は、その属性が含まれている要素を削除しない限り削除できません。</span><span class="sxs-lookup"><span data-stu-id="17e02-119">Default attributes cannot be removed unless the element they belong to is removed.</span></span> <span data-ttu-id="17e02-120">既定の属性が宣言されている要素には、常に既定の属性が存在します。</span><span class="sxs-lookup"><span data-stu-id="17e02-120">Default attributes are always present for elements that have default attributes declared.</span></span> <span data-ttu-id="17e02-121"><xref:System.Xml.XmlAttributeCollection> または <xref:System.Xml.XmlElement> から既定の属性を削除すると、代わりの属性が要素の <xref:System.Xml.XmlAttributeCollection> に挿入され、宣言されている既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="17e02-121">Removing a default attribute from an <xref:System.Xml.XmlAttributeCollection> or from the <xref:System.Xml.XmlElement> results in a replacement attribute inserted into the <xref:System.Xml.XmlAttributeCollection> of the element, initialized to the default value that was declared.</span></span> <span data-ttu-id="17e02-122">たとえば、`<book att1="1" att2="2" att3="3"></book>` として定義された要素がある場合、`book` 要素には、宣言された 3 つの既定の属性が設定されます。</span><span class="sxs-lookup"><span data-stu-id="17e02-122">If you have an element defined as `<book att1="1" att2="2" att3="3"></book>`, then you have a `book` element with three default attributes declared.</span></span> <span data-ttu-id="17e02-123">XML ドキュメント オブジェクト モデル (DOM) の実装によって、この `book`要素が存在する限り、`att1`、`att2`、および `att3` という 3 つの既定の属性が存在することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="17e02-123">The XML Document Object Model (DOM) implementation guarantees that as long as this `book` element exists, it has these three default attributes of `att1`, `att2`, and `att3`.</span></span>  
  
 <span data-ttu-id="17e02-124"><xref:System.Xml.XmlAttribute> を呼び出した場合、<xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> メソッドにより、属性の値が String.Empty に設定されます。これは、値のない属性が存在できないためです。</span><span class="sxs-lookup"><span data-stu-id="17e02-124">When called with an <xref:System.Xml.XmlAttribute>, the <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> method sets the value of the attribute to String.Empty, as an attribute cannot exist without a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e02-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="17e02-125">See also</span></span>

- [<span data-ttu-id="17e02-126">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="17e02-126">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
