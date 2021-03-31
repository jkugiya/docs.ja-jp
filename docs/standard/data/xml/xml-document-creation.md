---
description: '詳細情報: XML ドキュメントの作成'
title: XML ドキュメントの作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: 825c616fc6c0f7216248ae71e7d7630383d9cfea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782781"
---
# <a name="xml-document-creation"></a><span data-ttu-id="f0af6-103">XML ドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="f0af6-103">XML Document Creation</span></span>

<span data-ttu-id="f0af6-104">XML ドキュメントは、2 とおりの方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="f0af6-104">There are two ways to create an XML document.</span></span> <span data-ttu-id="f0af6-105">1 つは、パラメーターを使用せずに **XmlDocument** を作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="f0af6-105">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="f0af6-106">もう 1 つは、**XmlDocument** の作成時に XmlNameTable をパラメーターとして渡す方法です。</span><span class="sxs-lookup"><span data-stu-id="f0af6-106">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="f0af6-107">パラメーターを使用せず、新しい空の **XmlDocument** を作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="f0af6-107">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="f0af6-108">ドキュメントを作成すると、**Load** メソッドを使用することにより、文字列、ストリーム、URL、テキスト リーダー、または **XmlReader** から派生したクラスのデータを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f0af6-108">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="f0af6-109">文字列から XML を読み込む **LoadXML** メソッドという読み込みメソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="f0af6-109">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="f0af6-110">各種の **Load** メソッドの詳細については、「[XML ドキュメントの DOM への読み込み](reading-an-xml-document-into-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0af6-110">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="f0af6-111">**XmlNameTable** というクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="f0af6-111">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="f0af6-112">このクラスは、分解された文字列オブジェクトのテーブルです。</span><span class="sxs-lookup"><span data-stu-id="f0af6-112">This class is a table of atomized string objects.</span></span> <span data-ttu-id="f0af6-113">このテーブルを使用すると、パーサーは XML ドキュメント内で繰り返されているすべての要素名と属性名に同じ文字列オブジェクトを使用でき、効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="f0af6-113">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="f0af6-114">**XmlNameTable** は、前述のようにドキュメントの作成時に自動的に作成され、ドキュメントの読み込み時に属性名および要素名と共に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f0af6-114">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="f0af6-115">名前テーブルのあるドキュメントが既に存在し、それらの名前が別のドキュメントで役に立つ場合は、**XmlNameTable** をパラメーターとしてとる **Load** メソッドを使用して新しいドキュメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f0af6-115">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="f0af6-116">このメソッドによるドキュメントの作成時には、別のドキュメントからの既存の **XmlNameTable** と、既に読み込まれているすべての属性および要素が使われます。</span><span class="sxs-lookup"><span data-stu-id="f0af6-116">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="f0af6-117">XmlNameTable を使用すると、要素名と属性名を効率的に比較できます。</span><span class="sxs-lookup"><span data-stu-id="f0af6-117">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="f0af6-118">**XmlNameTable** の詳細については、「[XmlNameTable によるオブジェクトの比較](object-comparison-using-xmlnametable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0af6-118">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="f0af6-119"><xref:System.Xml.XmlNameTable>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0af6-119">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0af6-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0af6-120">See also</span></span>

- [<span data-ttu-id="f0af6-121">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="f0af6-121">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
