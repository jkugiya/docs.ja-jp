---
description: '詳細について: ICorDebugManagedCallback2:: CreateConnection メソッド'
title: ICorDebugManagedCallback2::CreateConnection メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: c7ac91217d43531505dc27a20da9cf4534366119
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790907"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="14fcb-103">ICorDebugManagedCallback2::CreateConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="14fcb-103">ICorDebugManagedCallback2::CreateConnection Method</span></span>

<span data-ttu-id="14fcb-104">新しい接続が作成されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="14fcb-104">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14fcb-105">構文</span><span class="sxs-lookup"><span data-stu-id="14fcb-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14fcb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="14fcb-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="14fcb-107">から接続が作成されたプロセスを表す "いいプロセス" オブジェクトへのポインター</span><span class="sxs-lookup"><span data-stu-id="14fcb-107">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="14fcb-108">から新しい接続の ID。</span><span class="sxs-lookup"><span data-stu-id="14fcb-108">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="14fcb-109">から新しい接続の名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="14fcb-109">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14fcb-110">解説</span><span class="sxs-lookup"><span data-stu-id="14fcb-110">Remarks</span></span>  

 <span data-ttu-id="14fcb-111">`CreateConnection`コールバックは、次のいずれかの場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="14fcb-111">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="14fcb-112">デバッガーが接続を含むプロセスにアタッチする場合。</span><span class="sxs-lookup"><span data-stu-id="14fcb-112">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="14fcb-113">この場合、ランタイムは、 `CreateConnection` プロセス内の各接続に対して、イベントと、 [ICorDebugManagedCallback2:: ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) イベントを生成してディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="14fcb-113">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="14fcb-114">ホストが[ホスティング API](../hosting/index.md)で[ICLRDebugManager:: beginconnection](../hosting/iclrdebugmanager-beginconnection-method.md)を呼び出すとき。</span><span class="sxs-lookup"><span data-stu-id="14fcb-114">When a host calls [ICLRDebugManager::BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14fcb-115">要件</span><span class="sxs-lookup"><span data-stu-id="14fcb-115">Requirements</span></span>  

 <span data-ttu-id="14fcb-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14fcb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14fcb-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14fcb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14fcb-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14fcb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14fcb-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14fcb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14fcb-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="14fcb-120">See also</span></span>

- [<span data-ttu-id="14fcb-121">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="14fcb-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="14fcb-122">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="14fcb-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
