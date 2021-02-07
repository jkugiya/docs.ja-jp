---
description: 詳細については、「WebHostServiceCloseFailed」を参照してください。
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: fae41b72e2eb9aba76993081769afc42c0ec8975
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720450"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="4a2d8-103">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="4a2d8-103">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>

<span data-ttu-id="4a2d8-104">サービスが正常に閉じられず、中止された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="4a2d8-104">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4a2d8-105">説明</span><span class="sxs-lookup"><span data-stu-id="4a2d8-105">Description</span></span>  

 <span data-ttu-id="4a2d8-106">このエラー コードはログ ファイルにのみ記録されます。</span><span class="sxs-lookup"><span data-stu-id="4a2d8-106">This error code only appears in the log file.</span></span> <span data-ttu-id="4a2d8-107">通常は、Abort を既に呼び出した後でサービスを閉じようとした場合などの、プログラミング エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="4a2d8-107">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4a2d8-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="4a2d8-108">Troubleshooting</span></span>  

 <span data-ttu-id="4a2d8-109">アプリケーションのソース コードをチェックしてください。</span><span class="sxs-lookup"><span data-stu-id="4a2d8-109">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a2d8-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a2d8-110">See also</span></span>

- [<span data-ttu-id="4a2d8-111">トレース</span><span class="sxs-lookup"><span data-stu-id="4a2d8-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="4a2d8-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="4a2d8-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4a2d8-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="4a2d8-113">Administration and Diagnostics</span></span>](../index.md)
