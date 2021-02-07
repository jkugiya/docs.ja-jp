---
description: '詳細情報: Isoprocess:: IsOSSuspended メソッド'
title: ICorDebugProcess::IsOSSuspended メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
ms.openlocfilehash: aa5e438418330d9fee51fcdb56a617421df06904
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746768"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="2e1cf-103">ICorDebugProcess::IsOSSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="2e1cf-103">ICorDebugProcess::IsOSSuspended Method</span></span>

<span data-ttu-id="2e1cf-104">デバッガーがこのプロセスを停止した結果として、指定されたスレッドが中断されたかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="2e1cf-104">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e1cf-105">構文</span><span class="sxs-lookup"><span data-stu-id="2e1cf-105">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e1cf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e1cf-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="2e1cf-107">から対象のスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="2e1cf-107">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="2e1cf-108">入出力`true`指定したスレッドが中断された場合は、それ以外の場合 `pbSuspended` はとなるブール値へのポインター。 `false`</span><span class="sxs-lookup"><span data-stu-id="2e1cf-108">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e1cf-109">解説</span><span class="sxs-lookup"><span data-stu-id="2e1cf-109">Remarks</span></span>  

 <span data-ttu-id="2e1cf-110">デバッガーがこのプロセスを停止した結果として、指定されたスレッドが中断された場合、指定されたスレッドの Win32 中断カウントは1だけインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="2e1cf-110">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="2e1cf-111">デバッガーのユーザーインターフェイス (UI) では、ユーザーに対してスレッドのオペレーティングシステム (OS) の中断カウントを表示すると、この情報を考慮に入れることができます。</span><span class="sxs-lookup"><span data-stu-id="2e1cf-111">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="2e1cf-112">メソッドは、 `IsOSSuspended` アンマネージデバッグのコンテキストでのみ意味があります。</span><span class="sxs-lookup"><span data-stu-id="2e1cf-112">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="2e1cf-113">マネージデバッグ中に、スレッドは、OS が中断するのではなく協調的に中断されます。</span><span class="sxs-lookup"><span data-stu-id="2e1cf-113">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e1cf-114">要件</span><span class="sxs-lookup"><span data-stu-id="2e1cf-114">Requirements</span></span>  

 <span data-ttu-id="2e1cf-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e1cf-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e1cf-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e1cf-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e1cf-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e1cf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e1cf-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e1cf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
