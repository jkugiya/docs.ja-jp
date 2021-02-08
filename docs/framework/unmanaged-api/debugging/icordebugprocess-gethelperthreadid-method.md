---
description: '詳細については、次の情報を参照してください: いい Process:: Geb Perthreadid メソッド'
title: ICorDebugProcess::GetHelperThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: ee7bd2106a37c5c67df48a54ff9ab7fa49a03f80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801021"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="d1794-103">ICorDebugProcess::GetHelperThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="d1794-103">ICorDebugProcess::GetHelperThreadID Method</span></span>

<span data-ttu-id="d1794-104">デバッガーの内部ヘルパースレッドのオペレーティングシステム (OS) スレッド ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="d1794-104">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1794-105">構文</span><span class="sxs-lookup"><span data-stu-id="d1794-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1794-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d1794-106">Parameters</span></span>  

 `pThreadID`  
 <span data-ttu-id="d1794-107">入出力デバッガーの内部ヘルパースレッドの OS スレッド ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d1794-107">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1794-108">解説</span><span class="sxs-lookup"><span data-stu-id="d1794-108">Remarks</span></span>  

 <span data-ttu-id="d1794-109">マネージデバッグおよびアンマネージデバッグ中は、デバッガーによって設定されたブレークポイントにヒットした場合に、指定した ID を持つスレッドが実行された状態を維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1794-109">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="d1794-110">デバッガーでは、このスレッドをユーザーに対して非表示にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d1794-110">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="d1794-111">まだプロセスにヘルパースレッドが存在しない場合、 `GetHelperThreadID` メソッドは \* で0を返し `pThreadID` ます。</span><span class="sxs-lookup"><span data-stu-id="d1794-111">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="d1794-112">ヘルパースレッドのスレッド ID は、時間の経過と共に変更される可能性があるため、キャッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d1794-112">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="d1794-113">停止イベントが発生するたびにスレッド ID を再照会する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1794-113">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="d1794-114">デバッガーのヘルパースレッドのスレッド ID は、すべてのアンマネージコードに対して、すべてのアンマネージ [コールバック:: CreateThread](icordebugmanagedcallback-createthread-method.md) イベントに対して適切になります。これにより、デバッガーはヘルパースレッドのスレッド id を判断し、ユーザーに対して非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d1794-114">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="d1794-115">アンマネージイベント中にヘルパースレッドとして識別されたスレッド `ICorDebugManagedCallback::CreateThread` は、マネージユーザーコードを実行しません。</span><span class="sxs-lookup"><span data-stu-id="d1794-115">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1794-116">要件</span><span class="sxs-lookup"><span data-stu-id="d1794-116">Requirements</span></span>  

 <span data-ttu-id="d1794-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1794-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1794-118">**ヘッダー:** CorDebug。</span><span class="sxs-lookup"><span data-stu-id="d1794-118">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="d1794-119">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1794-119">CorDebug.h</span></span>  
  
 <span data-ttu-id="d1794-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1794-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1794-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1794-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
