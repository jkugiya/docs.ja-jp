---
description: '詳細情報: LINQ to XML を使用した XML データの処理'
title: LINQ to XML を使用した XML データの処理
ms.date: 03/30/2017
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
ms.openlocfilehash: 9aad2e8b8981cef72952f393a4b9d4d49f503377
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783249"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="ea2ad-103">LINQ to XML を使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="ea2ad-103">Process XML Data Using LINQ to XML</span></span>

<span data-ttu-id="ea2ad-104">LINQ to XML は、XML データの処理を目的とした Microsoft .NET Framework version 3.5 の新しいモデルです。</span><span class="sxs-lookup"><span data-stu-id="ea2ad-104">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="ea2ad-105">LINQ to XML を使用することで、XML ドキュメントのクエリ、変更、作成、保存、シリアル化など、XML データを扱う際に必要な処理をすべて実行できます。</span><span class="sxs-lookup"><span data-stu-id="ea2ad-105">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="ea2ad-106">特に、クエリと作成の機能が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ea2ad-106">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="ea2ad-107">LINQ to XML のクエリでは、XPath や XQuery よりも SQL に類似した構文が使用され、簡潔で表現力に優れています。</span><span class="sxs-lookup"><span data-stu-id="ea2ad-107">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="ea2ad-108">クエリの結果を要素や属性のコレクションとして返すことができ、XElement オブジェクトのパラメーターとして使用できるため、XML ツリーの形を簡単に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="ea2ad-108">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="ea2ad-109">LINQ to XML では、.NET Framework version 3.5 の統合言語クエリ (LINQ) テクノロジを利用しています。</span><span class="sxs-lookup"><span data-stu-id="ea2ad-109">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="ea2ad-110">LINQ は C# および Visual Basic の言語構文を拡張したもので、潜在的には任意のデータ ストアまで拡張できる強力なクエリ機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="ea2ad-110">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="ea2ad-111">その使用方法の詳細については、「[LINQ to XML (C#)](../../linq/linq-xml-overview.md)」および「[LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea2ad-111">For a detailed discussion of its use, see [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span> <span data-ttu-id="ea2ad-112">LINQ フレームワークの概要については、「[統合言語クエリ (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)」または「[統合言語クエリ (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea2ad-112">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2ad-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea2ad-113">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="ea2ad-114">LINQ to XML とDOM (C#)</span><span class="sxs-lookup"><span data-stu-id="ea2ad-114">LINQ to XML vs. DOM (C#)</span></span>](../../linq/linq-xml-vs-dom.md)
- [<span data-ttu-id="ea2ad-115">LINQ to XML とDOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea2ad-115">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../linq/linq-xml-vs-dom.md)
- [<span data-ttu-id="ea2ad-116">LINQ to XML とその他の XML テクノロジ (C#)</span><span class="sxs-lookup"><span data-stu-id="ea2ad-116">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../linq/linq-xml-vs-xml-technologies.md)
- [<span data-ttu-id="ea2ad-117">LINQ to XML とその他の XML テクノロジ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea2ad-117">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../linq/linq-xml-vs-xml-technologies.md)
