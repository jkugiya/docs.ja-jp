---
title: '方法: WebRequest に一致するプロトコル固有の WebResponse を取得する'
description: .NET Framework で WebRequest に一致するプロトコル固有の WebResponse を取得する方法について学習します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 920704bedce478ed5a4f7906379a634a3b2a4e31
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584343"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="d00b3-103">方法: WebRequest に一致するプロトコル固有の WebResponse を取得する</span><span class="sxs-lookup"><span data-stu-id="d00b3-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>

<span data-ttu-id="d00b3-104">この例では、WebRequest に一致するプロトコル固有の WebResponse を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d00b3-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d00b3-105">例</span><span class="sxs-lookup"><span data-stu-id="d00b3-105">Example</span></span>  
  
```csharp  
HttpWebRequest req = (HttpWebRequest)WebRequest.Create("http://www.contoso.com/");
HttpWebResponse resp = (HttpWebResponse)req.GetResponse();
```  
  
```vb  
Dim req As HttpWebRequest = CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)
Dim resp As HttpWebResponse = CType(req.GetResponse(), HttpWebResponse)
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d00b3-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d00b3-106">Compiling the Code</span></span>  

 <span data-ttu-id="d00b3-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d00b3-107">This example requires:</span></span>  
  
- <span data-ttu-id="d00b3-108">**System.Net** 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="d00b3-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d00b3-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="d00b3-109">See also</span></span>

- [<span data-ttu-id="d00b3-110">データの要求</span><span class="sxs-lookup"><span data-stu-id="d00b3-110">Requesting Data</span></span>](requesting-data.md)
