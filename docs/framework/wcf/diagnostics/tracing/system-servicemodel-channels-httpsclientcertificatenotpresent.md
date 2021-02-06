---
description: 詳細については、「HttpsClientCertificateNotPresent」を参照してください。
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 1bca23915a55561c76b73c6b96750f324cb0e4dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99654487"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="b3038-103">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="b3038-103">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>

<span data-ttu-id="b3038-104">クライアント証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="b3038-104">Client certificate is required.</span></span> <span data-ttu-id="b3038-105">要求内で証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="b3038-105">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b3038-106">説明</span><span class="sxs-lookup"><span data-stu-id="b3038-106">Description</span></span>  

 <span data-ttu-id="b3038-107">このトレースは、HTTPS リスナーがクライアント証明書に関連付けられていない HTTPS 要求を受信したことを示します。</span><span class="sxs-lookup"><span data-stu-id="b3038-107">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="b3038-108">リスナーはすべての HTTPS 要求においてクライアント証明書を必要とするように構成されているため、リスナーによるクライアントの信頼性の検証は失敗します。</span><span class="sxs-lookup"><span data-stu-id="b3038-108">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3038-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3038-109">See also</span></span>

- [<span data-ttu-id="b3038-110">トレース</span><span class="sxs-lookup"><span data-stu-id="b3038-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="b3038-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b3038-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b3038-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="b3038-112">Administration and Diagnostics</span></span>](../index.md)
