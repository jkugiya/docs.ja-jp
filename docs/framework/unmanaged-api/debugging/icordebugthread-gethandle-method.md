---
description: '詳細については、次を参照してください: GetHandle メソッド'
title: ICorDebugThread::GetHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 378bb395e56f0fc287a480d67d2047e082d0796f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659102"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="8f5a4-103">ICorDebugThread::GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="8f5a4-103">ICorDebugThread::GetHandle Method</span></span>

<span data-ttu-id="8f5a4-104">このスレッドのアクティブな部分の現在のハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="8f5a4-104">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5a4-105">構文</span><span class="sxs-lookup"><span data-stu-id="8f5a4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f5a4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8f5a4-106">Parameters</span></span>  

 `phThreadHandle`  
 <span data-ttu-id="8f5a4-107">入出力このスレッドのアクティブな部分のハンドルである HTHREAD へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8f5a4-107">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f5a4-108">解説</span><span class="sxs-lookup"><span data-stu-id="8f5a4-108">Remarks</span></span>  

 <span data-ttu-id="8f5a4-109">ハンドルは、プロセスが実行されると変化する場合があり、スレッドのさまざまな部分で異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8f5a4-109">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="8f5a4-110">このハンドルは、デバッグ API によって所有されています。</span><span class="sxs-lookup"><span data-stu-id="8f5a4-110">This handle is owned by the debugging API.</span></span> <span data-ttu-id="8f5a4-111">使用する前に、デバッガーがそれを複製する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f5a4-111">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f5a4-112">要件</span><span class="sxs-lookup"><span data-stu-id="8f5a4-112">Requirements</span></span>  

 <span data-ttu-id="8f5a4-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f5a4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f5a4-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f5a4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f5a4-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f5a4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f5a4-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f5a4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
