---
description: '詳細について: INotifyConnection2:: UnregisterNotifySource メソッド'
title: INotifyConnection2::UnregisterNotifySource メソッド
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: d3b82665375f54d33b6a5581241788d828060a83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800306"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="e860f-103">INotifyConnection2::UnregisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="e860f-103">INotifyConnection2::UnregisterNotifySource Method</span></span>

<span data-ttu-id="e860f-104">指定された通知ソースオブジェクトを接続から削除します。</span><span class="sxs-lookup"><span data-stu-id="e860f-104">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e860f-105">構文</span><span class="sxs-lookup"><span data-stu-id="e860f-105">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e860f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e860f-106">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="e860f-107">から登録を解除する通知オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e860f-107">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e860f-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e860f-108">Return Value</span></span>  

 <span data-ttu-id="e860f-109">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="e860f-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e860f-110">要件</span><span class="sxs-lookup"><span data-stu-id="e860f-110">Requirements</span></span>  

 <span data-ttu-id="e860f-111">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="e860f-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e860f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e860f-112">See also</span></span>

- [<span data-ttu-id="e860f-113">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e860f-113">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="e860f-114">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e860f-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="e860f-115">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e860f-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="e860f-116">RegisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="e860f-116">RegisterNotifySource Method</span></span>](inotifyconnection2-registernotifysource-method.md)
