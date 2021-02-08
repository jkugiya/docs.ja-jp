---
description: 詳細については、「WCF で必要なオペレーティングシステムのリソース」を参照してください。
title: WCF に必要なオペレーティング システム リソース
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 717ab2074c0dcf840919c2bd8afa2641e106ac11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779219"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="f3787-103">WCF に必要なオペレーティング システム リソース</span><span class="sxs-lookup"><span data-stu-id="f3787-103">Operating System Resources Required by WCF</span></span>

<span data-ttu-id="f3787-104">Windows Communication Foundation (WCF) は、オペレーティングシステムによって機能するために提供されるいくつかのリソースに依存します。</span><span class="sxs-lookup"><span data-stu-id="f3787-104">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="f3787-105">次の表は、これらのリソースを示しています。</span><span class="sxs-lookup"><span data-stu-id="f3787-105">The following table lists those resources:</span></span>

|<span data-ttu-id="f3787-106">リソース</span><span class="sxs-lookup"><span data-stu-id="f3787-106">Resource</span></span>|<span data-ttu-id="f3787-107">説明</span><span class="sxs-lookup"><span data-stu-id="f3787-107">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="f3787-108">Microsoft 分散トランザクション コーディネーター (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="f3787-108">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="f3787-109">OleTx トランザクションをサポートするために必要です。</span><span class="sxs-lookup"><span data-stu-id="f3787-109">Required to support OleTx transactions.</span></span>|
|<span data-ttu-id="f3787-110">インターネット インフォメーション サービス (IIS)</span><span class="sxs-lookup"><span data-stu-id="f3787-110">Internet Information Services (IIS)</span></span>|<span data-ttu-id="f3787-111">IIS を使用してアプリケーションをホストする場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f3787-111">Required if you want to use IIS to host your application.</span></span>|
|<span data-ttu-id="f3787-112">Windows プロセス アクティブ化サービス (WAS)</span><span class="sxs-lookup"><span data-stu-id="f3787-112">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="f3787-113">WAS を使用してアプリケーションをホストする場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f3787-113">Required if you want to use WAS to host your application.</span></span>|
