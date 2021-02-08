---
description: 詳細については、「IApartmentCallback インターフェイス」を参照してください。
title: IApartmentCallback インターフェイス
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
ms.openlocfilehash: ddf99b1d926bd2d9765b936143785a975ea378a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785132"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="11dc7-103">IApartmentCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11dc7-103">IApartmentCallback Interface</span></span>

<span data-ttu-id="11dc7-104">アパートメント内でコールバックを作成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="11dc7-104">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="11dc7-105">*アパートメント* は、同じスレッドアクセス要件を共有するオブジェクトのプロセス内の論理コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="11dc7-105">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11dc7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="11dc7-106">Methods</span></span>  
  
|<span data-ttu-id="11dc7-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="11dc7-107">Method</span></span>|<span data-ttu-id="11dc7-108">説明</span><span class="sxs-lookup"><span data-stu-id="11dc7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11dc7-109">DoCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="11dc7-109">DoCallback Method</span></span>](iapartmentcallback-docallback-method.md)|<span data-ttu-id="11dc7-110">アパートメント内で指定された関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="11dc7-110">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11dc7-111">要件</span><span class="sxs-lookup"><span data-stu-id="11dc7-111">Requirements</span></span>  

 <span data-ttu-id="11dc7-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11dc7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11dc7-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="11dc7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11dc7-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="11dc7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11dc7-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11dc7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11dc7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="11dc7-116">See also</span></span>

- [<span data-ttu-id="11dc7-117">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11dc7-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
