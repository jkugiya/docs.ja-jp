---
description: '詳細について: INotifySource2:: SetNotifyFilter メソッド'
title: INotifySource2::SetNotifyFilter メソッド
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 2aaf2a5253f8a9acb67c4b538f109a7a62559d12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800228"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="a9e2f-103">INotifySource2::SetNotifyFilter メソッド</span><span class="sxs-lookup"><span data-stu-id="a9e2f-103">INotifySource2::SetNotifyFilter Method</span></span>

<span data-ttu-id="a9e2f-104">このソースで使用する通知フィルターを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a9e2f-104">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9e2f-105">構文</span><span class="sxs-lookup"><span data-stu-id="a9e2f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9e2f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9e2f-106">Parameters</span></span>  

 `in_NotifyFilter`  
 <span data-ttu-id="a9e2f-107">からデバッガー API のコールバックを識別する [NOTIFY_FILTER](notify-filter-enumeration.md) 列挙値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="a9e2f-107">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="a9e2f-108">からデバッガー API のスレッドを識別する [USER_THREAD](user-thread-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a9e2f-108">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9e2f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="a9e2f-109">Return Value</span></span>  

 <span data-ttu-id="a9e2f-110">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="a9e2f-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9e2f-111">要件</span><span class="sxs-lookup"><span data-stu-id="a9e2f-111">Requirements</span></span>  

 <span data-ttu-id="a9e2f-112">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="a9e2f-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e2f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9e2f-113">See also</span></span>

- [<span data-ttu-id="a9e2f-114">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9e2f-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="a9e2f-115">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9e2f-115">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="a9e2f-116">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9e2f-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
