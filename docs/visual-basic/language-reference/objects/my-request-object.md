---
description: '詳細情報: My.Request オブジェクト'
title: My.Request オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 0b72252e261cd033bfc35c546de5c53a4f3cfe2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640655"
---
# <a name="myrequest-object"></a><span data-ttu-id="d55fb-103">My.Request オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d55fb-103">My.Request Object</span></span>

<span data-ttu-id="d55fb-104">要求されたページの <xref:System.Web.HttpRequest> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="d55fb-104">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d55fb-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="d55fb-105">Remarks</span></span>  

 <span data-ttu-id="d55fb-106">`My.Request` オブジェクトには、現在の HTTP 要求に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d55fb-106">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="d55fb-107">`My.Request` オブジェクトは、ASP.NET アプリケーションでのみ使うことができます。</span><span class="sxs-lookup"><span data-stu-id="d55fb-107">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d55fb-108">例</span><span class="sxs-lookup"><span data-stu-id="d55fb-108">Example</span></span>  

 <span data-ttu-id="d55fb-109">次の例では、`My.Request` オブジェクトからヘッダー コレクションを取得し、`My.Response` オブジェクトを使用して ASP.NET ページに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d55fb-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d55fb-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d55fb-110">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="d55fb-111">My.Response オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d55fb-111">My.Response Object</span></span>](my-response-object.md)
