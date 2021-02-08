---
description: '詳細情報: IActionOnCLREvent インターフェイス'
title: IActionOnCLREvent インターフェイス
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 9d762635247f897663f4c6f2badf67edf98bd5d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785173"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="d72cd-103">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d72cd-103">IActionOnCLREvent Interface</span></span>

<span data-ttu-id="d72cd-104">[Iactiononclrevent:: OnEvent](iactiononclrevent-onevent-method.md)メソッドを提供します。このメソッドは、 [ICLROnEventManager:: registeractiononevent](iclroneventmanager-registeractiononevent-method.md)メソッドの呼び出しを使用して登録されたイベントに対してコールバックを実行します。</span><span class="sxs-lookup"><span data-stu-id="d72cd-104">Provides the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d72cd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d72cd-105">Methods</span></span>  
  
|<span data-ttu-id="d72cd-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d72cd-106">Method</span></span>|<span data-ttu-id="d72cd-107">説明</span><span class="sxs-lookup"><span data-stu-id="d72cd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d72cd-108">OnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="d72cd-108">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="d72cd-109">登録されているイベントに対してコールバックを実行します。</span><span class="sxs-lookup"><span data-stu-id="d72cd-109">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d72cd-110">要件</span><span class="sxs-lookup"><span data-stu-id="d72cd-110">Requirements</span></span>  

 <span data-ttu-id="d72cd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d72cd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d72cd-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d72cd-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d72cd-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d72cd-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d72cd-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d72cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d72cd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d72cd-115">See also</span></span>

- [<span data-ttu-id="d72cd-116">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="d72cd-116">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="d72cd-117">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d72cd-117">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d72cd-118">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d72cd-118">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="d72cd-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d72cd-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
