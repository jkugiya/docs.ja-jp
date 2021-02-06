---
description: 詳細については、サービスの展開に関するページをご覧ください。
title: サービスの配置
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 6a0b1d88410b865f57cd1eb16f070842a75ddb07
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645998"
---
# <a name="deploying-services"></a><span data-ttu-id="03527-103">サービスの配置</span><span class="sxs-lookup"><span data-stu-id="03527-103">Deploying Services</span></span>

<span data-ttu-id="03527-104">このトピックでは、Windows Communication Foundation (WCF) アプリケーションを実行時環境に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="03527-104">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="03527-105">アプリケーションのホスト環境の選択</span><span class="sxs-lookup"><span data-stu-id="03527-105">Choosing the Hosting Environment for Your Application</span></span>  

 <span data-ttu-id="03527-106">WCF サービスは、マネージコードをサポートする任意の Windows プロセスで実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="03527-106">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="03527-107">アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="03527-107">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="03527-108">ホスティング環境の範囲は、最も単純なコンソール アプリケーション内、Windows サービスやインターネット インフォメーション サービス (IIS) のようなサーバー環境、あるいは Windows アクティブ化サービス (WAS) で管理されるワーカー プロセス内での実行にまで及びます。</span><span class="sxs-lookup"><span data-stu-id="03527-108">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="03527-109">WCF アプリケーションのさまざまなホスティングオプションを確認するには、「 [ホスティングサービス](../hosting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03527-109">To review the different hosting options for your WCF application, see [Hosting Services](../hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03527-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="03527-110">See also</span></span>

- [<span data-ttu-id="03527-111">ホスティング</span><span class="sxs-lookup"><span data-stu-id="03527-111">Hosting</span></span>](../feature-details/hosting.md)
- [<span data-ttu-id="03527-112">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="03527-112">Hosting Services</span></span>](../hosting-services.md)
