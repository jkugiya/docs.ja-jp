---
description: '詳細情報: 方法:HTTP 固有のプロパティにアクセスする'
title: '方法: HTTP 固有のプロパティにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
ms.openlocfilehash: a54ef247b479cf6cdec8dc28732304cf03b0b202
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729303"
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="c4c49-103">方法: HTTP 固有のプロパティにアクセスする</span><span class="sxs-lookup"><span data-stu-id="c4c49-103">How to: Access HTTP-Specific Properties</span></span>

<span data-ttu-id="c4c49-104">このサンプルでは、HTTP の **Keep-alive** 動作を無効にして、Web サーバーからプロトコル バージョン番号を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c4c49-104">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4c49-105">例</span><span class="sxs-lookup"><span data-stu-id="c4c49-105">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4c49-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c4c49-106">Compiling the Code</span></span>  

 <span data-ttu-id="c4c49-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c4c49-107">This example requires:</span></span>  
  
- <span data-ttu-id="c4c49-108">**System.Net** 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="c4c49-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c49-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4c49-109">See also</span></span>

- [<span data-ttu-id="c4c49-110">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="c4c49-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="c4c49-111">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="c4c49-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="c4c49-112">HTTP</span><span class="sxs-lookup"><span data-stu-id="c4c49-112">HTTP</span></span>](http.md)
