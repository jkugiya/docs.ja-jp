---
description: '詳細について: ICoreClrDebugTarget:: FreeMemory メソッド'
title: ICoreClrDebugTarget::FreeMemory メソッド
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: 9572e0c3df1fdd064e78ba170d39c1415c68dc85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690003"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="1b9f4-103">ICoreClrDebugTarget::FreeMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="1b9f4-103">ICoreClrDebugTarget::FreeMemory Method</span></span>

<span data-ttu-id="1b9f4-104">[ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md)メソッドおよび[ICoreClrDebugTarget:: enumruntimes](icoreclrdebugtarget-enumruntimes-method.md)メソッドによって割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="1b9f4-104">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9f4-105">構文</span><span class="sxs-lookup"><span data-stu-id="1b9f4-105">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b9f4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b9f4-106">Parameters</span></span>  

 `pMemory`  
 <span data-ttu-id="1b9f4-107">から [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) または [ICoreClrDebugTarget:: enumruntimes](icoreclrdebugtarget-enumruntimes-method.md) メソッドによって返される配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1b9f4-107">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b9f4-108">要件</span><span class="sxs-lookup"><span data-stu-id="1b9f4-108">Requirements</span></span>  

 <span data-ttu-id="1b9f4-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b9f4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b9f4-110">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="1b9f4-110">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="1b9f4-111">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="1b9f4-111">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="1b9f4-112">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="1b9f4-112">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9f4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b9f4-113">See also</span></span>

- [<span data-ttu-id="1b9f4-114">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b9f4-114">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
