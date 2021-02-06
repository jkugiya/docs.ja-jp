---
description: '詳細については、次を参照してください: Okthread:: CreateStepper メソッド'
title: ICorDebugThread::CreateStepper メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: 378ce28281f4f284c36194f993a53598a9de3854
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659362"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="6e3ae-103">ICorDebugThread::CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="6e3ae-103">ICorDebugThread::CreateStepper Method</span></span>

<span data-ttu-id="6e3ae-104">この ICorDebugStepper スレッドのアクティブなフレームをステップ実行できるようにする、オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6e3ae-104">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e3ae-105">構文</span><span class="sxs-lookup"><span data-stu-id="6e3ae-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e3ae-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e3ae-106">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="6e3ae-107">入出力 `ICorDebugStepper` このスレッドのアクティブフレームのステップ実行を可能にするオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6e3ae-107">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e3ae-108">解説</span><span class="sxs-lookup"><span data-stu-id="6e3ae-108">Remarks</span></span>  

 <span data-ttu-id="6e3ae-109">アクティブなフレームはアンマネージコードである場合があります。</span><span class="sxs-lookup"><span data-stu-id="6e3ae-109">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="6e3ae-110">`ICorDebugStepper`実際のステップ実行には、インターフェイスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e3ae-110">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e3ae-111">要件</span><span class="sxs-lookup"><span data-stu-id="6e3ae-111">Requirements</span></span>  

 <span data-ttu-id="6e3ae-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e3ae-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e3ae-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e3ae-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e3ae-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e3ae-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e3ae-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e3ae-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
