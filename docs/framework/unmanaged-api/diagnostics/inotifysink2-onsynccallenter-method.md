---
description: '詳細について: INotifySink2:: OnSyncCallEnter メソッド'
title: INotifySink2::OnSyncCallEnter メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
ms.openlocfilehash: e7537b16ec8ea8d92ad92498c1bfdac5a9de6475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800280"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="ab9ab-103">INotifySink2::OnSyncCallEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="ab9ab-103">INotifySink2::OnSyncCallEnter Method</span></span>

<span data-ttu-id="ab9ab-104">呼び出しを入力したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ab9ab-104">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab9ab-105">構文</span><span class="sxs-lookup"><span data-stu-id="ab9ab-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab9ab-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab9ab-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="ab9ab-107">から入力されている呼び出しの ID。</span><span class="sxs-lookup"><span data-stu-id="ab9ab-107">[in] ID of the call being entered.</span></span> <span data-ttu-id="ab9ab-108">「 [CALL_ID 構造](call-id-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab9ab-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="ab9ab-109">から呼び出しバッファー。</span><span class="sxs-lookup"><span data-stu-id="ab9ab-109">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="ab9ab-110">から呼び出しバッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="ab9ab-110">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab9ab-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="ab9ab-111">Return Value</span></span>  

 <span data-ttu-id="ab9ab-112">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="ab9ab-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab9ab-113">要件</span><span class="sxs-lookup"><span data-stu-id="ab9ab-113">Requirements</span></span>  

 <span data-ttu-id="ab9ab-114">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="ab9ab-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9ab-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab9ab-115">See also</span></span>

- [<span data-ttu-id="ab9ab-116">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab9ab-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="ab9ab-117">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab9ab-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="ab9ab-118">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab9ab-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
