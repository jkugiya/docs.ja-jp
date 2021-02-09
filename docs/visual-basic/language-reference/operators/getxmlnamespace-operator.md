---
description: '詳細情報: GetXmlNamespace 演算子 (Visual Basic)'
title: GetXmlNamespace 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 704ac22493a0d6ce1255d171ae3b418313b74f09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665914"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="4c30d-103">GetXmlNamespace 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c30d-103">GetXmlNamespace Operator (Visual Basic)</span></span>

<span data-ttu-id="4c30d-104">指定した XML 名前空間プレフィックスに対応する <xref:System.Xml.Linq.XNamespace> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="4c30d-104">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c30d-105">構文</span><span class="sxs-lookup"><span data-stu-id="4c30d-105">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="4c30d-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="4c30d-106">Parts</span></span>  

 `xmlNamespacePrefix`  
 <span data-ttu-id="4c30d-107">任意。</span><span class="sxs-lookup"><span data-stu-id="4c30d-107">Optional.</span></span> <span data-ttu-id="4c30d-108">XML 名前空間プレフィックスを識別する文字列です。</span><span class="sxs-lookup"><span data-stu-id="4c30d-108">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="4c30d-109">指定する場合、文字列は有効な XML 識別子である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c30d-109">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="4c30d-110">詳細については、「[宣言する XML 要素と属性の名前](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c30d-110">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="4c30d-111">プレフィックスが指定されていない場合は、既定の名前空間が返されます。</span><span class="sxs-lookup"><span data-stu-id="4c30d-111">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="4c30d-112">既定の名前空間が指定されていない場合は、空の名前空間が返されます。</span><span class="sxs-lookup"><span data-stu-id="4c30d-112">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c30d-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="4c30d-113">Return Value</span></span>  

 <span data-ttu-id="4c30d-114">XML 名前空間プレフィックスに対応する <xref:System.Xml.Linq.XNamespace> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4c30d-114">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c30d-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c30d-115">Remarks</span></span>  

 <span data-ttu-id="4c30d-116">`GetXmlNamespace` 演算子は、XML 名前空間プレフィックス `xmlNamespacePrefix` に対応する <xref:System.Xml.Linq.XNamespace> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="4c30d-116">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="4c30d-117">XML 名前空間プレフィックスは、XML リテラルと XML 軸プロパティで直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c30d-117">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="4c30d-118">ただし、コードで名前空間プレフィックスを使用する前に、`GetXmlNamespace` 演算子を使用して、それを <xref:System.Xml.Linq.XNamespace> オブジェクトに変換しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c30d-118">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="4c30d-119"><xref:System.Xml.Linq.XNamespace> オブジェクトに非修飾要素名を追加して、多くの [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] メソッドで必要となる完全修飾 <xref:System.Xml.Linq.XName> オブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="4c30d-119">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c30d-120">例</span><span class="sxs-lookup"><span data-stu-id="4c30d-120">Example</span></span>  

 <span data-ttu-id="4c30d-121">次の例では、名前空間プレフィックスとして `ns` をインポートしています。</span><span class="sxs-lookup"><span data-stu-id="4c30d-121">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="4c30d-122">その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名が `ns:phone` である最初の子ノードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4c30d-122">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="4c30d-123">次に、その子ノードを `ShowName` サブルーチンに渡します。これにより、`GetXmlNamespace` 演算子を使用して修飾名が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4c30d-123">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="4c30d-124">次に、`ShowName` サブルーチンが修飾名を <xref:System.Xml.Linq.XNode.Ancestors%2A> メソッドに渡して、親の `ns:contact` ノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="4c30d-124">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="4c30d-125">`TestGetXmlNamespace.RunSample()` を呼び出すと、次のテキストを含むメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c30d-125">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="4c30d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c30d-126">See also</span></span>

- [<span data-ttu-id="4c30d-127">Imports ステートメント (XML 名前空間)</span><span class="sxs-lookup"><span data-stu-id="4c30d-127">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="4c30d-128">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="4c30d-128">Accessing XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/accessing-xml.md)
