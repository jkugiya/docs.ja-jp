---
description: '詳細について: ICLRDataTarget:: GetCurrentThreadID メソッド'
title: ICLRDataTarget::GetCurrentThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
ms.openlocfilehash: ae1ef00fd6afbecf741d1e4ed215c816dcf6af8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801359"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="31304-103">ICLRDataTarget::GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="31304-103">ICLRDataTarget::GetCurrentThreadID Method</span></span>

<span data-ttu-id="31304-104">現在のスレッドのオペレーティングシステム id を取得します。</span><span class="sxs-lookup"><span data-stu-id="31304-104">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31304-105">構文</span><span class="sxs-lookup"><span data-stu-id="31304-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31304-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31304-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="31304-107">入出力ターゲットプロセスの現在のスレッドのオペレーティングシステム識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="31304-107">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31304-108">解説</span><span class="sxs-lookup"><span data-stu-id="31304-108">Remarks</span></span>  

 <span data-ttu-id="31304-109">ターゲットプロセスの現在のスレッドが存在しない場合、 `GetCurrentThreadID` メソッドは失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="31304-109">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31304-110">要件</span><span class="sxs-lookup"><span data-stu-id="31304-110">Requirements</span></span>  

 <span data-ttu-id="31304-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31304-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31304-112">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="31304-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="31304-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31304-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31304-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31304-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31304-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="31304-115">See also</span></span>

- [<span data-ttu-id="31304-116">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31304-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
