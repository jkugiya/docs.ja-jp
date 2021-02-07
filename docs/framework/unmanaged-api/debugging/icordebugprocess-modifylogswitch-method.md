---
description: '詳細については、次の情報を参照してください: いい Process:: ModifyLogSwitch メソッド'
title: ICorDebugProcess::ModifyLogSwitch メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
ms.openlocfilehash: 3c825d6c6b075139793b54526dca696c8fba35a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746774"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="3fdb8-103">ICorDebugProcess::ModifyLogSwitch メソッド</span><span class="sxs-lookup"><span data-stu-id="3fdb8-103">ICorDebugProcess::ModifyLogSwitch Method</span></span>

<span data-ttu-id="3fdb8-104">指定されたログスイッチの重大度レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="3fdb8-104">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fdb8-105">構文</span><span class="sxs-lookup"><span data-stu-id="3fdb8-105">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fdb8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3fdb8-106">Parameters</span></span>  

 `pLogSwitchName`  
 <span data-ttu-id="3fdb8-107">からログスイッチの名前を指定する文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3fdb8-107">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="3fdb8-108">から指定されたログスイッチに設定される重大度レベル。</span><span class="sxs-lookup"><span data-stu-id="3fdb8-108">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fdb8-109">解説</span><span class="sxs-lookup"><span data-stu-id="3fdb8-109">Remarks</span></span>  

 <span data-ttu-id="3fdb8-110">このメソッドは、によって実行される場合にのみ有効です: [: CreateProcess managedcallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) コールバックが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3fdb8-110">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fdb8-111">要件</span><span class="sxs-lookup"><span data-stu-id="3fdb8-111">Requirements</span></span>  

 <span data-ttu-id="3fdb8-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fdb8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fdb8-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fdb8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fdb8-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fdb8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fdb8-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fdb8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
