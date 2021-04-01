---
title: XML の読み込み時または解析時に空白を維持する - LINQ to XML
description: XML ツリーを設定する LINQ to XML メソッドの空白文字動作を制御できます。 たとえば、インメモリ処理のインデントを削除したり、そのままにしたりできます。
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 783a1198f0b1754c690f04159860056a0fbadeb4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411989"
---
# <a name="preserve-white-space-while-loading-or-parsing-xml-linq-to-xml"></a><span data-ttu-id="00ae0-104">XML の読み込み時または解析時に空白を維持する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="00ae0-104">Preserve white space while loading or parsing XML (LINQ to XML)</span></span>

<span data-ttu-id="00ae0-105">この記事では、空白に対する LINQ to XML の動作を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="00ae0-105">This article describes how to control the white space behavior of LINQ to XML.</span></span>

<span data-ttu-id="00ae0-106">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="00ae0-106">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="00ae0-107">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="00ae0-107">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="00ae0-108">これが LINQ to XML の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="00ae0-108">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="00ae0-109">もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="00ae0-109">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="00ae0-110">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="00ae0-110">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="00ae0-111">LINQ to XML でこれを行うには、XML を読み込む際または解析する場合に空白を維持し、XML をシリアル化するときに書式設定を無効にします。</span><span class="sxs-lookup"><span data-stu-id="00ae0-111">To do this in LINQ to XML, you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>

<span data-ttu-id="00ae0-112">この記事では、空白に対する、XML ツリーを設定するメソッドの動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="00ae0-112">This article describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="00ae0-113">XML ツリーをシリアル化するときの空白の制御については、「[シリアル化時に空白を維持する](preserve-white-space-serializing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00ae0-113">For information about controlling white space when you serialize XML trees, see [Preserve white space while serializing](preserve-white-space-serializing.md).</span></span>

## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="00ae0-114">XML ツリーを設定するメソッドの動作</span><span class="sxs-lookup"><span data-stu-id="00ae0-114">Behavior of methods that populate XML trees</span></span>

<span data-ttu-id="00ae0-115"><xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq.XDocument> クラスにある次のメソッドは、XML ツリーを設定します。</span><span class="sxs-lookup"><span data-stu-id="00ae0-115">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="00ae0-116">XML ツリーは、ファイル、<xref:System.IO.TextReader>、<xref:System.Xml.XmlReader>、または文字列から設定することができます。</span><span class="sxs-lookup"><span data-stu-id="00ae0-116">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>

- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>

<span data-ttu-id="00ae0-117">メソッドが <xref:System.Xml.Linq.LoadOptions> を引数として受け取らない場合、意味のない空白は維持されません。</span><span class="sxs-lookup"><span data-stu-id="00ae0-117">If the method doesn't take <xref:System.Xml.Linq.LoadOptions> as an argument, the method won't preserve insignificant white space.</span></span>

<span data-ttu-id="00ae0-118">ほとんどの場合、メソッドが <xref:System.Xml.Linq.LoadOptions> を引数として受け取ると、意味のない空白を XML ツリー内のテキスト ノードとして維持できます。これは、オプションの動作です。</span><span class="sxs-lookup"><span data-stu-id="00ae0-118">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="00ae0-119">ただし、メソッドが <xref:System.Xml.XmlReader> から XML を読み込んでいる場合は、<xref:System.Xml.XmlReader> によって空白を維持するかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="00ae0-119">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="00ae0-120"><xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> を設定しても効果はありません。</span><span class="sxs-lookup"><span data-stu-id="00ae0-120">Setting <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> will have no effect.</span></span>

<span data-ttu-id="00ae0-121">これらのメソッドで空白を維持すると、意味のない空白が <xref:System.Xml.Linq.XText> ノードとして XML ツリーに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="00ae0-121">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="00ae0-122">空白が維持されない場合、テキスト ノードは挿入されません。</span><span class="sxs-lookup"><span data-stu-id="00ae0-122">If white space isn't preserved, text nodes aren't inserted.</span></span>

<span data-ttu-id="00ae0-123"><xref:System.Xml.XmlWriter> を使用して、XML ツリーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="00ae0-123">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="00ae0-124"><xref:System.Xml.XmlWriter> に書き込まれたノードが、ツリーに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="00ae0-124">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="00ae0-125">ただし、このメソッドを使用して XML ツリーを構築すると、ノードが空白かどうかにかかわらず、また空白に意味があるかどうかにかかわらず、すべてのノードが維持されます。</span><span class="sxs-lookup"><span data-stu-id="00ae0-125">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>
