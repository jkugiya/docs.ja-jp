---
description: 詳細については、「HttpsClientCertificateInvalid」を参照してください。
title: System.ServiceModel.Channels.HttpsClientCertificateInvalid
ms.date: 03/30/2017
ms.assetid: 8884dda1-fa0e-4d2a-8079-7042c51b64ef
ms.openlocfilehash: c9d6545beee55000dc609c68824f27e33b71f60f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635234"
---
# <a name="systemservicemodelchannelshttpsclientcertificateinvalid"></a><span data-ttu-id="510b7-103">System.ServiceModel.Channels.HttpsClientCertificateInvalid</span><span class="sxs-lookup"><span data-stu-id="510b7-103">System.ServiceModel.Channels.HttpsClientCertificateInvalid</span></span>

<span data-ttu-id="510b7-104">クライアント証明書が無効です。</span><span class="sxs-lookup"><span data-stu-id="510b7-104">Client certificate is invalid.</span></span>  
  
## <a name="description"></a><span data-ttu-id="510b7-105">説明</span><span class="sxs-lookup"><span data-stu-id="510b7-105">Description</span></span>  

 <span data-ttu-id="510b7-106">このトレースは、HTTPS リスナーが、クライアントによって提供された証明書が無効であることを検出したことを示します。</span><span class="sxs-lookup"><span data-stu-id="510b7-106">This trace indicates that the certificate provided by the client was found to be invalid by the HTTPS listener.</span></span> <span data-ttu-id="510b7-107">HTTPS リスナーは、この証明書を使用してクライアントの信頼性を検証しようとしていました。</span><span class="sxs-lookup"><span data-stu-id="510b7-107">The HTTPS listener was attempting to validate the authenticity of the client using this certificate.</span></span> <span data-ttu-id="510b7-108">サービスをホストしているサーバーによって証明書の証明機関が認識されないと、証明書は無効になります。</span><span class="sxs-lookup"><span data-stu-id="510b7-108">A certificate could be invalid if its Certificate Authority is not recognized by the server hosting the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510b7-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="510b7-109">See also</span></span>

- [<span data-ttu-id="510b7-110">トレース</span><span class="sxs-lookup"><span data-stu-id="510b7-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="510b7-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="510b7-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="510b7-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="510b7-112">Administration and Diagnostics</span></span>](../index.md)
