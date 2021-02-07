---
description: 詳細については、「MessageClosedAgain」を参照してください。
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: 40e6dcc8974440bd7d7f10ca30e36447c4ae790a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716199"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="9a853-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="9a853-103">System.ServiceModel.MessageClosedAgain</span></span>

<span data-ttu-id="9a853-104">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="9a853-104">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="9a853-105">説明</span><span class="sxs-lookup"><span data-stu-id="9a853-105">Description</span></span>  

 <span data-ttu-id="9a853-106">メッセージがもう一度閉じられました。</span><span class="sxs-lookup"><span data-stu-id="9a853-106">A message was closed again.</span></span>  
  
 <span data-ttu-id="9a853-107">メッセージを閉じることができるのは一度だけです。</span><span class="sxs-lookup"><span data-stu-id="9a853-107">A message should be closed only once.</span></span> <span data-ttu-id="9a853-108">このトレースがユーザー拡張コード内で出力されている場合は、ユーザー拡張コードは既に閉じられているメッセージをさらに閉じようとしていることが示されています。</span><span class="sxs-lookup"><span data-stu-id="9a853-108">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="9a853-109">このトレースが製品のコード内で出力されている場合は、ユーザー拡張コードがメッセージを閉じるのが早すぎる可能性があることが示されています。</span><span class="sxs-lookup"><span data-stu-id="9a853-109">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a853-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a853-110">See also</span></span>

- [<span data-ttu-id="9a853-111">トレース</span><span class="sxs-lookup"><span data-stu-id="9a853-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="9a853-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9a853-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9a853-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="9a853-113">Administration and Diagnostics</span></span>](../index.md)
