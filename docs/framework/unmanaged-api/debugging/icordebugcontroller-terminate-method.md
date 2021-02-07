---
description: '詳細については、次を参照してください: いいね:: 終了メソッド'
title: ICorDebugController::Terminate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: 15cc832205ebfe86e521d4a45124808e0f3fe128
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710713"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="063bc-103">ICorDebugController::Terminate メソッド</span><span class="sxs-lookup"><span data-stu-id="063bc-103">ICorDebugController::Terminate Method</span></span>

<span data-ttu-id="063bc-104">指定された終了コードを使用してプロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="063bc-104">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="063bc-105">このメソッドは、Win32 関数のラッパーです `TerminateProcess` 。</span><span class="sxs-lookup"><span data-stu-id="063bc-105">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="063bc-106">したがって、は、 `Terminate` Win32 関数が使用するのと同じ方法で終了コードを使用し `TerminateProcess` ます。</span><span class="sxs-lookup"><span data-stu-id="063bc-106">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="063bc-107">構文</span><span class="sxs-lookup"><span data-stu-id="063bc-107">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="063bc-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="063bc-108">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="063bc-109">から終了コードを表す数値。</span><span class="sxs-lookup"><span data-stu-id="063bc-109">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="063bc-110">有効な数値は、Winbase. h で定義されています。</span><span class="sxs-lookup"><span data-stu-id="063bc-110">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="063bc-111">解説</span><span class="sxs-lookup"><span data-stu-id="063bc-111">Remarks</span></span>  

 <span data-ttu-id="063bc-112">が呼び出されたときにプロセスが停止された場合は、このプロセスを続行 `Terminate` する必要があります。これを行うに[は、](icordebugcontroller-continue-method.md)デバッガーが、"ExitProcess" または " [](icordebugmanagedcallback-exitprocess-method.md) [managedcallback:: exitappdomain](icordebugmanagedcallback-exitappdomain-method.md) callback" を使用して終了の確認を受け取るようにします。</span><span class="sxs-lookup"><span data-stu-id="063bc-112">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="063bc-113">このメソッドは、アプリケーションドメインによって実装されていません。</span><span class="sxs-lookup"><span data-stu-id="063bc-113">This method is not implemented by an application domain.</span></span> <span data-ttu-id="063bc-114">つまり、レベルでは実装されていません <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="063bc-114">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="063bc-115">要件</span><span class="sxs-lookup"><span data-stu-id="063bc-115">Requirements</span></span>  

 <span data-ttu-id="063bc-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="063bc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="063bc-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="063bc-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="063bc-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="063bc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="063bc-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="063bc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="063bc-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="063bc-120">See also</span></span>
