---
description: 詳細については、「IAppDomainBinding インターフェイス」を参照してください。
title: IAppDomainBinding インターフェイス
ms.date: 03/30/2017
api_name:
- IAppDomainBinding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainBinding
helpviewer_keywords:
- IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type:
- apiref
ms.openlocfilehash: 3de559af023311f705f9f7dc6eb9785788216a83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760616"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="712b9-103">IAppDomainBinding インターフェイス</span><span class="sxs-lookup"><span data-stu-id="712b9-103">IAppDomainBinding Interface</span></span>

<span data-ttu-id="712b9-104">アプリケーションドメインが作成されたことをホストアプリケーションに通知するために、共通言語ランタイム (CLR) によって呼び出されるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="712b9-104">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="712b9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="712b9-105">Methods</span></span>  
  
|<span data-ttu-id="712b9-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="712b9-106">Method</span></span>|<span data-ttu-id="712b9-107">説明</span><span class="sxs-lookup"><span data-stu-id="712b9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="712b9-108">OnAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="712b9-108">OnAppDomain Method</span></span>](iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="712b9-109">アプリケーションドメインが作成されたことをホストに通知するために、共通言語ランタイム (CLR) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="712b9-109">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="712b9-110">要件</span><span class="sxs-lookup"><span data-stu-id="712b9-110">Requirements</span></span>  

 <span data-ttu-id="712b9-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="712b9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712b9-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="712b9-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="712b9-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="712b9-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="712b9-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="712b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712b9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="712b9-115">See also</span></span>

- [<span data-ttu-id="712b9-116">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="712b9-116">Hosting Interfaces</span></span>](hosting-interfaces.md)
