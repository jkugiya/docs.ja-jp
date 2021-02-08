---
description: '詳細について: INotifySink2:: OnSyncCallOut メソッド'
title: INotifySink2::OnSyncCallOut メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: 03028b138a7d95c618ae20530f66aa692d314cab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800241"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="5dc61-103">INotifySink2::OnSyncCallOut メソッド</span><span class="sxs-lookup"><span data-stu-id="5dc61-103">INotifySink2::OnSyncCallOut Method</span></span>

<span data-ttu-id="5dc61-104">呼び出しがタイムアウトしたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5dc61-104">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dc61-105">構文</span><span class="sxs-lookup"><span data-stu-id="5dc61-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dc61-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5dc61-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="5dc61-107">から発信する呼び出しの ID。「 [CALL_ID 構造](call-id-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dc61-107">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="5dc61-108">入出力呼び出しバッファー。</span><span class="sxs-lookup"><span data-stu-id="5dc61-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="5dc61-109">入出力呼び出しバッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5dc61-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5dc61-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="5dc61-110">Return Value</span></span>  

 <span data-ttu-id="5dc61-111">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="5dc61-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dc61-112">要件</span><span class="sxs-lookup"><span data-stu-id="5dc61-112">Requirements</span></span>  

 <span data-ttu-id="5dc61-113">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="5dc61-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc61-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5dc61-114">See also</span></span>

- [<span data-ttu-id="5dc61-115">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5dc61-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="5dc61-116">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5dc61-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="5dc61-117">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5dc61-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
