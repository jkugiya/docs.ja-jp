---
description: '詳細情報: My.Response オブジェクト'
title: My.Response オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 551528356040539994251cb66a905d0249f482da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640616"
---
# <a name="myresponse-object"></a><span data-ttu-id="de186-103">My.Response オブジェクト</span><span class="sxs-lookup"><span data-stu-id="de186-103">My.Response Object</span></span>

<span data-ttu-id="de186-104"><xref:System.Web.UI.Page> に関連付けられた <xref:System.Web.HttpResponse> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="de186-104">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="de186-105">このオブジェクトでは、HTTP 応答データをクライアントに送信し、その応答に関する情報を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="de186-105">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de186-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="de186-106">Remarks</span></span>  

 <span data-ttu-id="de186-107">`My.Response` オブジェクトには、ページに関連付けられている現在の <xref:System.Web.HttpResponse> オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="de186-107">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="de186-108">`My.Response` オブジェクトは、ASP.NET アプリケーションでのみ使うことができます。</span><span class="sxs-lookup"><span data-stu-id="de186-108">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de186-109">例</span><span class="sxs-lookup"><span data-stu-id="de186-109">Example</span></span>  

 <span data-ttu-id="de186-110">次の例では、`My.Request` オブジェクトからヘッダー コレクションを取得し、`My.Response` オブジェクトを使用して ASP.NET ページに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="de186-110">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="de186-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="de186-111">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="de186-112">My.Request オブジェクト</span><span class="sxs-lookup"><span data-stu-id="de186-112">My.Request Object</span></span>](my-request-object.md)
