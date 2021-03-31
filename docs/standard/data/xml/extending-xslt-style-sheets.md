---
description: '詳細情報: XSLT スタイル シートの拡張'
title: XSLT スタイル シートの拡張
ms.date: 03/30/2017
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
ms.openlocfilehash: 570e2a5b546f6541f551977d7cab9a43b255201c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642540"
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="8c01b-103">XSLT スタイル シートの拡張</span><span class="sxs-lookup"><span data-stu-id="8c01b-103">Extending XSLT Style Sheets</span></span>

<span data-ttu-id="8c01b-104">このセクションでは、XSLT の機能を拡張するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c01b-104">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="8c01b-105">拡張オブジェクトまたはパラメーターは、<xref:System.Xml.Xsl.XsltArgumentList> クラスを使用して追加できます。</span><span class="sxs-lookup"><span data-stu-id="8c01b-105">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="8c01b-106">その後、スタイル シートから拡張オブジェクトまたはパラメーターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8c01b-106">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="8c01b-107">また、`msxsl:script` 要素を使用すると、スタイル シートにスクリプト ブロックを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="8c01b-107">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c01b-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8c01b-108">In This Section</span></span>  

 [<span data-ttu-id="8c01b-109">XSLT 拡張オブジェクト</span><span class="sxs-lookup"><span data-stu-id="8c01b-109">XSLT Extension Objects</span></span>](xslt-extension-objects.md)  
 <span data-ttu-id="8c01b-110"><xref:System.Xml.Xsl.XsltArgumentList> クラスを使用して XSLT 拡張オブジェクトを処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8c01b-110">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="8c01b-111">XSLT パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c01b-111">XSLT Parameters</span></span>](xslt-parameters.md)  
 <span data-ttu-id="8c01b-112"><xref:System.Xml.Xsl.XsltArgumentList> クラスを使用して XSLT パラメーターを処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8c01b-112">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="8c01b-113">msxsl:script を使用したスクリプト ブロック</span><span class="sxs-lookup"><span data-stu-id="8c01b-113">Script Blocks Using msxsl:script</span></span>](script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="8c01b-114">`msxsl:script` 要素の使い方を説明します。</span><span class="sxs-lookup"><span data-stu-id="8c01b-114">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8c01b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c01b-115">Related Sections</span></span>  

 [<span data-ttu-id="8c01b-116">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="8c01b-116">XSLT Transformations</span></span>](xslt-transformations.md)
