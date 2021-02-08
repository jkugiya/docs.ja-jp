---
description: '詳細について: INotifySink2:: OnSyncCallReturn メソッド'
title: INotifySink2::OnSyncCallReturn メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
ms.openlocfilehash: 01518de4e5a9e1374edddadb3c49f16e8fe679a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800254"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="5ed33-103">INotifySink2::OnSyncCallReturn メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed33-103">INotifySink2::OnSyncCallReturn Method</span></span>

<span data-ttu-id="5ed33-104">呼び出しから制御が戻ったときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5ed33-104">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed33-105">構文</span><span class="sxs-lookup"><span data-stu-id="5ed33-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ed33-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ed33-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="5ed33-107">からから返される呼び出しの ID。</span><span class="sxs-lookup"><span data-stu-id="5ed33-107">[in] ID of the call being returned from.</span></span> <span data-ttu-id="5ed33-108">「 [CALL_ID 構造](call-id-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ed33-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="5ed33-109">から呼び出しバッファー。</span><span class="sxs-lookup"><span data-stu-id="5ed33-109">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="5ed33-110">から呼び出しバッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5ed33-110">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ed33-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="5ed33-111">Return Value</span></span>  

 <span data-ttu-id="5ed33-112">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="5ed33-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed33-113">要件</span><span class="sxs-lookup"><span data-stu-id="5ed33-113">Requirements</span></span>  

 <span data-ttu-id="5ed33-114">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="5ed33-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed33-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ed33-115">See also</span></span>

- [<span data-ttu-id="5ed33-116">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ed33-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="5ed33-117">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ed33-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="5ed33-118">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ed33-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
