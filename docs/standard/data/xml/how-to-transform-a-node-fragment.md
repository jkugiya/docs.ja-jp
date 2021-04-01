---
description: '詳細情報: ノード フラグメントを変換する方法'
title: '方法: ノード フラグメントを変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: 9373491837fdfb176547aa7e01b8ebf72ae91bef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713768"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="e83cf-103">方法: ノード フラグメントを変換する</span><span class="sxs-lookup"><span data-stu-id="e83cf-103">How to: Transform a Node Fragment</span></span>

<span data-ttu-id="e83cf-104"><xref:System.Xml.XmlDocument> オブジェクトまたは <xref:System.Xml.XPath.XPathDocument> オブジェクトに含まれるデータを変換すると、XSLT 変換はドキュメント全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e83cf-104">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="e83cf-105">つまり、ドキュメント ルート ノード以外のノードを指定しても、変換処理では、読み込んだドキュメントのすべてのノードがアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="e83cf-105">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="e83cf-106">1 つのノード フラグメントを変換するには、ノード フラグメントだけを含むオブジェクトを別に作成し、そのオブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e83cf-106">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e83cf-107">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e83cf-107">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="e83cf-108">1 つのノード フラグメントを変換するには</span><span class="sxs-lookup"><span data-stu-id="e83cf-108">To transform a node fragment</span></span>  
  
1. <span data-ttu-id="e83cf-109">ソース ドキュメントを含むオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e83cf-109">Create an object containing the source document.</span></span>  
  
2. <span data-ttu-id="e83cf-110">変換するノード フラグメントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e83cf-110">Locate the node fragment you wish to transform.</span></span>  
  
3. <span data-ttu-id="e83cf-111">そのノード フラグメントだけの別のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e83cf-111">Create separate object with just the node fragment.</span></span>  
  
4. <span data-ttu-id="e83cf-112">ノード フラグメントを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e83cf-112">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e83cf-113">例</span><span class="sxs-lookup"><span data-stu-id="e83cf-113">Example</span></span>  

 <span data-ttu-id="e83cf-114">次の例は、1 つのノード フラグメントを変換して、結果をコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="e83cf-114">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="e83cf-115">入力</span><span class="sxs-lookup"><span data-stu-id="e83cf-115">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="e83cf-116">books.xml</span><span class="sxs-lookup"><span data-stu-id="e83cf-116">books.xml</span></span>  

 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="e83cf-117">single.xsl</span><span class="sxs-lookup"><span data-stu-id="e83cf-117">single.xsl</span></span>  

 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="e83cf-118">Output</span><span class="sxs-lookup"><span data-stu-id="e83cf-118">Output</span></span>  

 <span data-ttu-id="e83cf-119">Book title is The Confidence Man.</span><span class="sxs-lookup"><span data-stu-id="e83cf-119">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83cf-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e83cf-120">See also</span></span>

- [<span data-ttu-id="e83cf-121">XslCompiledTransform クラスの使用</span><span class="sxs-lookup"><span data-stu-id="e83cf-121">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
