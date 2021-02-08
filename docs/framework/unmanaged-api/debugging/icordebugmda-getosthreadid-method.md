---
description: '詳細については、次を参照してください: GetOSThreadId:: メソッド'
title: ICorDebugMDA::GetOSThreadId メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: f965585a6e6060a14f0cbc2a80b46124b2751e0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801151"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="d73a2-103">ICorDebugMDA::GetOSThreadId メソッド</span><span class="sxs-lookup"><span data-stu-id="d73a2-103">ICorDebugMDA::GetOSThreadId Method</span></span>

<span data-ttu-id="d73a2-104">によって表されるマネージデバッグアシスタント (MDA) が実行さ [れている](icordebugmda-interface.md) オペレーティングシステム (os) スレッド識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d73a2-104">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d73a2-105">構文</span><span class="sxs-lookup"><span data-stu-id="d73a2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d73a2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d73a2-106">Parameters</span></span>  

 `pOsTid`  
 <span data-ttu-id="d73a2-107">入出力OS スレッド識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d73a2-107">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d73a2-108">解説</span><span class="sxs-lookup"><span data-stu-id="d73a2-108">Remarks</span></span>  

 <span data-ttu-id="d73a2-109">システムスレッドを使用すると、ネイティブスレッドで、またはまだマネージコードを入力していないマネージスレッド上で MDA が発生する状況に対応できます。</span><span class="sxs-lookup"><span data-stu-id="d73a2-109">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d73a2-110">要件</span><span class="sxs-lookup"><span data-stu-id="d73a2-110">Requirements</span></span>  

 <span data-ttu-id="d73a2-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d73a2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d73a2-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d73a2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d73a2-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d73a2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d73a2-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d73a2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d73a2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d73a2-115">See also</span></span>

- [<span data-ttu-id="d73a2-116">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d73a2-116">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="d73a2-117">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="d73a2-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
