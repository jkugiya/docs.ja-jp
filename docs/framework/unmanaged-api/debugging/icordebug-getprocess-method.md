---
description: '詳細について: ICorDebug:: GetProcess メソッド'
title: ICorDebug::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
ms.openlocfilehash: a24bb0ec645a337b1202b954c165a76bcf8fad9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801307"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="5388b-103">ICorDebug::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="5388b-103">ICorDebug::GetProcess Method</span></span>

<span data-ttu-id="5388b-104">指定されたプロセスの "いいプロセス" インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5388b-104">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5388b-105">構文</span><span class="sxs-lookup"><span data-stu-id="5388b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5388b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5388b-106">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="5388b-107">からプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="5388b-107">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="5388b-108">入出力 `ICorDebugProcess` 指定されたプロセスのインスタンスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5388b-108">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5388b-109">要件</span><span class="sxs-lookup"><span data-stu-id="5388b-109">Requirements</span></span>  

 <span data-ttu-id="5388b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5388b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5388b-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5388b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5388b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5388b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5388b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5388b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5388b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5388b-114">See also</span></span>

- [<span data-ttu-id="5388b-115">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5388b-115">ICorDebug Interface</span></span>](icordebug-interface.md)
