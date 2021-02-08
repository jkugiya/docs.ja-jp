---
description: '詳細については、次を参照してください: を参照'
title: ICorDebugManagedCallback::ControlCTrap メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: 9fa71dacb20ff6df21d8aabb687c2601f27643c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791068"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="56db8-103">ICorDebugManagedCallback::ControlCTrap メソッド</span><span class="sxs-lookup"><span data-stu-id="56db8-103">ICorDebugManagedCallback::ControlCTrap Method</span></span>

<span data-ttu-id="56db8-104">デバッグ対象のプロセスで CTRL + C がトラップされることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="56db8-104">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56db8-105">構文</span><span class="sxs-lookup"><span data-stu-id="56db8-105">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56db8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="56db8-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="56db8-107">からCTRL + C キーがトラップされるプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="56db8-107">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56db8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="56db8-108">Return Value</span></span>  
  
|<span data-ttu-id="56db8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56db8-109">HRESULT</span></span>|<span data-ttu-id="56db8-110">説明</span><span class="sxs-lookup"><span data-stu-id="56db8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56db8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="56db8-111">S_OK</span></span>|<span data-ttu-id="56db8-112">デバッガーは CTRL + C トラップを処理します。</span><span class="sxs-lookup"><span data-stu-id="56db8-112">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="56db8-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="56db8-113">S_FALSE</span></span>|<span data-ttu-id="56db8-114">デバッガーは CTRL + C トラップを処理しません。</span><span class="sxs-lookup"><span data-stu-id="56db8-114">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56db8-115">解説</span><span class="sxs-lookup"><span data-stu-id="56db8-115">Remarks</span></span>  

 <span data-ttu-id="56db8-116">プロセス内のすべてのアプリケーションドメインがこのコールバックに対して停止されています。</span><span class="sxs-lookup"><span data-stu-id="56db8-116">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56db8-117">要件</span><span class="sxs-lookup"><span data-stu-id="56db8-117">Requirements</span></span>  

 <span data-ttu-id="56db8-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56db8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56db8-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56db8-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56db8-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56db8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56db8-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56db8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56db8-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="56db8-122">See also</span></span>

- [<span data-ttu-id="56db8-123">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56db8-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
