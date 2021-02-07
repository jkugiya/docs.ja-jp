---
description: '詳細については、次のページを参照してください: いい Process:: EnableLogMessages メソッド'
title: ICorDebugProcess::EnableLogMessages メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
ms.openlocfilehash: d44f1a14611493372c7321feaa14329d5d77b01b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753992"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="03e17-103">ICorDebugProcess::EnableLogMessages メソッド</span><span class="sxs-lookup"><span data-stu-id="03e17-103">ICorDebugProcess::EnableLogMessages Method</span></span>

<span data-ttu-id="03e17-104">デバッガーへのログメッセージの転送を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="03e17-104">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e17-105">構文</span><span class="sxs-lookup"><span data-stu-id="03e17-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03e17-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03e17-106">Parameters</span></span>  

 `fOnOff`  
 <span data-ttu-id="03e17-107">[入力] `true` ログメッセージの転送を有効にします。 `false` 転送を無効にします。</span><span class="sxs-lookup"><span data-stu-id="03e17-107">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03e17-108">解説</span><span class="sxs-lookup"><span data-stu-id="03e17-108">Remarks</span></span>  

 <span data-ttu-id="03e17-109">このメソッドは、によって実行される場合にのみ有効です: [: CreateProcess managedcallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) コールバックが発生します。</span><span class="sxs-lookup"><span data-stu-id="03e17-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e17-110">要件</span><span class="sxs-lookup"><span data-stu-id="03e17-110">Requirements</span></span>  

 <span data-ttu-id="03e17-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03e17-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03e17-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03e17-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03e17-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03e17-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03e17-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03e17-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
