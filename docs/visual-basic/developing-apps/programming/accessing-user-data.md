---
description: '詳細情報: ユーザー データへのアクセス (Visual Basic)'
title: ユーザー データへのアクセス
ms.date: 07/20/2015
helpviewer_keywords:
- domain names [Visual Basic], retrieving
- data [Visual Basic], accessing user data
- My.User object [Visual Basic], tasks
- user data [Visual Basic], domain
- user names [Visual Basic], retrieving
- user data [Visual Basic], accessing
- login names [Visual Basic]
- examples [Visual Basic], accessing user data
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
ms.openlocfilehash: 4f7f7a8cb121b74a2680f29c0aa14491f6e38434
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797875"
---
# <a name="accessing-user-data-visual-basic"></a><span data-ttu-id="7e2e9-103">ユーザー データへのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e2e9-103">Accessing User Data (Visual Basic)</span></span>

<span data-ttu-id="7e2e9-104">このセクションには、`My.User` オブジェクトとそれで実行できるタスクに関するトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7e2e9-104">This section contains topics dealing with the `My.User` object and tasks that you can accomplish with it.</span></span>  
  
 <span data-ttu-id="7e2e9-105">`My.User` オブジェクトを利用すれば、<xref:System.Security.Principal.IPrincipal> インターフェイスを実装するオブジェクトを返すことで、ログオン ユーザーに関する情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7e2e9-105">The `My.User` object provides access to information about the logged-on user by returning an object that implements the <xref:System.Security.Principal.IPrincipal> interface.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="7e2e9-106">タスク</span><span class="sxs-lookup"><span data-stu-id="7e2e9-106">Tasks</span></span>  
  
|<span data-ttu-id="7e2e9-107">終了</span><span class="sxs-lookup"><span data-stu-id="7e2e9-107">To</span></span>|<span data-ttu-id="7e2e9-108">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="7e2e9-108">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="7e2e9-109">ユーザーのログイン名を取得する</span><span class="sxs-lookup"><span data-stu-id="7e2e9-109">Get the user's login name</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|<span data-ttu-id="7e2e9-110">アプリケーションで Windows 認証が使用される場合、ユーザーのドメイン名を取得する</span><span class="sxs-lookup"><span data-stu-id="7e2e9-110">Get the user's domain name, if the application uses Windows authentication</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|<span data-ttu-id="7e2e9-111">ユーザーの役割を判断する</span><span class="sxs-lookup"><span data-stu-id="7e2e9-111">Determine the user's role</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="7e2e9-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e2e9-112">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.User>
