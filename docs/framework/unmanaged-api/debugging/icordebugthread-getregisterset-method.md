---
description: '詳細については、次のページを参照してください: いい Thread:: GetRegisterSet メソッド'
title: ICorDebugThread::GetRegisterSet メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
ms.openlocfilehash: f61ccb34eabc1f4d8b8db8a0b78e3ddde9aa136d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658881"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="896cd-103">ICorDebugThread::GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="896cd-103">ICorDebugThread::GetRegisterSet Method</span></span>

<span data-ttu-id="896cd-104">このコンポーネントオブジェクトのアクティブな部分に関連付けられているレジスタセットへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="896cd-104">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="896cd-105">構文</span><span class="sxs-lookup"><span data-stu-id="896cd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="896cd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="896cd-106">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="896cd-107">入出力このスレッドのアクティブな部分のレジスタセットを [表す、の](icordebugregisterset-interface.md) オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="896cd-107">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="896cd-108">要件</span><span class="sxs-lookup"><span data-stu-id="896cd-108">Requirements</span></span>  

 <span data-ttu-id="896cd-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="896cd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="896cd-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="896cd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="896cd-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="896cd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="896cd-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="896cd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
