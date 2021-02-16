---
description: '詳細情報: 方法:ファイル、文字列、またはストリームから XML を読み込む (Visual Basic)'
title: '方法: ファイル、文字列、またはストリームからの XML の読み込み'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 375190642c93d929abe2ae10bb6ccba927e3bc8a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480064"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="9d2a2-103">方法: ファイル、文字列、またはストリームから XML を読み込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d2a2-103">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="9d2a2-104">複数のメソッドを使用して、[XML リテラル](../../../language-reference/xml-literals/index.md)を作成し、外部ソースからファイル、文字列、ストリームなどの内容を取り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="9d2a2-104">You can create [XML Literals](../../../language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="9d2a2-105">以降の例でこれらのメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="9d2a2-105">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="9d2a2-106">ファイルから XML を読み込むには</span><span class="sxs-lookup"><span data-stu-id="9d2a2-106">To load XML from a file</span></span>

<span data-ttu-id="9d2a2-107">ファイルから <xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XDocument> オブジェクトなどの XML リテラルを取り込むには、`Load` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d2a2-107">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="9d2a2-108">このメソッドは、入力としてファイル パス、テキスト ストリーム、または XML ストリームを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9d2a2-108">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="9d2a2-109">次のコード例では、<xref:System.Xml.Linq.XDocument.Load%28System.String%29> メソッドを使用して、<xref:System.Xml.Linq.XDocument> オブジェクトにテキスト ファイルから XML を取り込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9d2a2-109">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="9d2a2-110">文字列から XML を読み込むには</span><span class="sxs-lookup"><span data-stu-id="9d2a2-110">To load XML from a string</span></span>

<span data-ttu-id="9d2a2-111">文字列から <xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XDocument> オブジェクトなどの XML リテラルを取り込むには、`Parse` メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9d2a2-111">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="9d2a2-112">次のコード例では、<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> メソッドを使用して、<xref:System.Xml.Linq.XDocument> オブジェクトに文字列から XML を取り込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9d2a2-112">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="9d2a2-113">ストリームから XML を読み込むには</span><span class="sxs-lookup"><span data-stu-id="9d2a2-113">To load XML from a stream</span></span>

<span data-ttu-id="9d2a2-114">ストリームから <xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XDocument> オブジェクトなどの XML リテラルを取り込むには、`Load` メソッドまたは <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9d2a2-114">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9d2a2-115">次のコード例では、<xref:System.Xml.Linq.XNode.ReadFrom%2A> メソッドを使用して、<xref:System.Xml.Linq.XDocument> オブジェクトに XML ストリームから XML を取り込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9d2a2-115">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="9d2a2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d2a2-116">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9d2a2-117">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="9d2a2-117">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="9d2a2-118">XML</span><span class="sxs-lookup"><span data-stu-id="9d2a2-118">XML</span></span>](index.md)
- [<span data-ttu-id="9d2a2-119">Visual Basic での XML の操作</span><span class="sxs-lookup"><span data-stu-id="9d2a2-119">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
