---
description: '詳細について: INotifySink2:: OnSyncCallExit メソッド'
title: INotifySink2::OnSyncCallExit メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 2de55c3b7956576049e4ad65b2cb6fbc69fa84af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800267"
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="59bc0-103">INotifySink2::OnSyncCallExit メソッド</span><span class="sxs-lookup"><span data-stu-id="59bc0-103">INotifySink2::OnSyncCallExit Method</span></span>

<span data-ttu-id="59bc0-104">呼び出しを終了したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="59bc0-104">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59bc0-105">構文</span><span class="sxs-lookup"><span data-stu-id="59bc0-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59bc0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="59bc0-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="59bc0-107">から終了する呼び出しの ID。</span><span class="sxs-lookup"><span data-stu-id="59bc0-107">[in] ID of the call being exited.</span></span> <span data-ttu-id="59bc0-108">「 [CALL_ID 構造](call-id-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59bc0-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="59bc0-109">入出力呼び出しバッファー。</span><span class="sxs-lookup"><span data-stu-id="59bc0-109">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="59bc0-110">入出力呼び出しバッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="59bc0-110">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59bc0-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="59bc0-111">Return Value</span></span>  

 <span data-ttu-id="59bc0-112">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="59bc0-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59bc0-113">要件</span><span class="sxs-lookup"><span data-stu-id="59bc0-113">Requirements</span></span>  

 <span data-ttu-id="59bc0-114">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="59bc0-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bc0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="59bc0-115">See also</span></span>

- [<span data-ttu-id="59bc0-116">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59bc0-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="59bc0-117">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59bc0-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="59bc0-118">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59bc0-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
