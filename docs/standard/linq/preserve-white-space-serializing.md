---
title: シリアル化時に空白を維持する - LINQ to XML
description: XML ツリーをシリアル化するとき、さまざまな方法で空白を制御できます。
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d907e68a2df3905794b555954330f31b5e75655
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411984"
---
# <a name="preserve-white-space-while-serializing-linq-to-xml"></a><span data-ttu-id="93339-103">シリアル化時に空白を維持する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="93339-103">Preserve white space while serializing (LINQ to XML)</span></span>

<span data-ttu-id="93339-104">この記事では、XML ツリーをシリアル化するときに空白を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="93339-104">This article describes how to control white space when serializing an XML tree.</span></span>

<span data-ttu-id="93339-105">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="93339-105">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="93339-106">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="93339-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="93339-107">これが LINQ to XML の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="93339-107">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="93339-108">もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="93339-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="93339-109">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="93339-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="93339-110">LINQ to XML でこれを行うには、XML を読み込む際または解析する場合に空白を維持し、XML をシリアル化するときに書式設定を無効にします。</span><span class="sxs-lookup"><span data-stu-id="93339-110">To do this in LINQ to XML, you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>

## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="93339-111">XML ツリーをシリアル化するメソッドの空白に関する動作</span><span class="sxs-lookup"><span data-stu-id="93339-111">White-space behavior of methods that serialize XML trees</span></span>

<span data-ttu-id="93339-112"><xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq.XDocument> クラスにある次のメソッドは、XML ツリーをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="93339-112">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="93339-113">XML ツリーは、ファイル、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="93339-113">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="93339-114">`ToString` メソッドは、文字列にシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="93339-114">The `ToString` method serializes to a string.</span></span>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- [<span data-ttu-id="93339-115">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="93339-115">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
- [<span data-ttu-id="93339-116">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="93339-116">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)

<span data-ttu-id="93339-117">メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取らない場合は、シリアル化された XML が書式設定 (インデント) されます。</span><span class="sxs-lookup"><span data-stu-id="93339-117">If the method doesn't take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="93339-118">この場合、XML ツリー内の意味のない空白はすべて破棄されます。</span><span class="sxs-lookup"><span data-stu-id="93339-118">In this case, all insignificant white space in the XML tree is discarded.</span></span>

<span data-ttu-id="93339-119">メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取る場合は、シリアル化された XML が書式設定 (インデント) されないことを指定できます。</span><span class="sxs-lookup"><span data-stu-id="93339-119">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="93339-120">この場合、XML ツリー内の空白はすべて維持されます。</span><span class="sxs-lookup"><span data-stu-id="93339-120">In this case, all white space in the XML tree is preserved.</span></span>
