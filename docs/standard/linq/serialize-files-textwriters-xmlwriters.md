---
title: ファイル、TextWriter、XmlWriter にシリアル化する - LINQ to XML
description: XML ツリーをファイル、TextWriter、または XmlWriter にシリアル化できます。また、ToString メソッドを使用し、XDocument や XElement など、あらゆる XML コンポーネントを文字列にシリアル化できます。
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20651c06a759d83934c4b035a42eac7c2700eb9f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412111"
---
# <a name="serialize-to-files-textwriters-and-xmlwriters-linq-to-xml"></a><span data-ttu-id="54ca7-103">ファイル、TextWriter、XmlWriter にシリアル化する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="54ca7-103">Serialize to files, TextWriters, and XmlWriters (LINQ to XML)</span></span>

<span data-ttu-id="54ca7-104">XML ツリーは、<xref:System.IO.File>、<xref:System.IO.TextWriter>、または <xref:System.Xml.XmlWriter> にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="54ca7-104">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="54ca7-105"><xref:System.Xml.Linq.XDocument> メソッドを使用すると、<xref:System.Xml.Linq.XElement> や `ToString` など任意の XML コンポーネントを文字列にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="54ca7-105">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>

<span data-ttu-id="54ca7-106">文字列にシリアル化するときに書式設定されないようにするには、<xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="54ca7-106">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="54ca7-107">ファイルにシリアル化するときの既定の動作では、結果の XML ドキュメントの書式設定 (インデント設定) が行われます。</span><span class="sxs-lookup"><span data-stu-id="54ca7-107">The default behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="54ca7-108">インデントを設定する場合、XML ツリー内の意味のない空白は保持されません。</span><span class="sxs-lookup"><span data-stu-id="54ca7-108">When you indent, the insignificant white space in the XML tree isn't preserved.</span></span> <span data-ttu-id="54ca7-109">書式を設定してシリアル化するには、<xref:System.Xml.Linq.SaveOptions> を引数として受け取らない次のメソッドのいずれかのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="54ca7-109">To serialize with formatting, use one of the overloads of the following methods that don't take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="54ca7-110">インデントを設定せず、XML ツリー内の意味のない空白を保持できるようにするには、<xref:System.Xml.Linq.SaveOptions> を引数として受け取る次のメソッドのいずれかのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="54ca7-110">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

<span data-ttu-id="54ca7-111">例については、該当するリファレンス記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54ca7-111">For examples, see the appropriate reference article.</span></span>
