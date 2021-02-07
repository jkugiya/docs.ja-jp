---
description: '詳細について: ICorDebug:: SetManagedHandler メソッド'
title: ICorDebug::SetManagedHandler メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 5817bd39a2c4e7c71dc12ca8d2d9b1263d116ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754356"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="34f5a-103">ICorDebug::SetManagedHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="34f5a-103">ICorDebug::SetManagedHandler Method</span></span>

<span data-ttu-id="34f5a-104">マネージイベントのイベントハンドラーオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="34f5a-104">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34f5a-105">構文</span><span class="sxs-lookup"><span data-stu-id="34f5a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34f5a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34f5a-106">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="34f5a-107">からイベントハンドラーオブジェクトである、ツール [コールバック](icordebugmanagedcallback-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="34f5a-107">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34f5a-108">解説</span><span class="sxs-lookup"><span data-stu-id="34f5a-108">Remarks</span></span>  

 <span data-ttu-id="34f5a-109">`SetManagedHandler` 作成時にを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="34f5a-109">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="34f5a-110">の実装に、デバッグ `ICorDebugManagedCallback` 対象のアプリケーションのデバッグイベントを処理するための十分なインターフェイスが含まれていない場合は、 `SetManagedHandler` E_NOINTERFACE の HRESULT が返されます。</span><span class="sxs-lookup"><span data-stu-id="34f5a-110">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34f5a-111">要件</span><span class="sxs-lookup"><span data-stu-id="34f5a-111">Requirements</span></span>  

 <span data-ttu-id="34f5a-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34f5a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34f5a-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34f5a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34f5a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34f5a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34f5a-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34f5a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f5a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="34f5a-116">See also</span></span>

- [<span data-ttu-id="34f5a-117">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="34f5a-117">ICorDebug Interface</span></span>](icordebug-interface.md)
