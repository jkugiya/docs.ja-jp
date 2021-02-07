---
description: '詳細については、「GetAssembly Module:: メソッド」を参照してください。'
title: ICorDebugModule::GetAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
ms.openlocfilehash: 88bda923cd4c3ebfa5da6b3343e1cead4cebbad9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722616"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="18061-103">ICorDebugModule::GetAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="18061-103">ICorDebugModule::GetAssembly Method</span></span>

<span data-ttu-id="18061-104">このモジュールの格納アセンブリを取得します。</span><span class="sxs-lookup"><span data-stu-id="18061-104">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18061-105">構文</span><span class="sxs-lookup"><span data-stu-id="18061-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18061-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="18061-106">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="18061-107">入出力このモジュールを格納しているアセンブリを表す、オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="18061-107">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18061-108">要件</span><span class="sxs-lookup"><span data-stu-id="18061-108">Requirements</span></span>  

 <span data-ttu-id="18061-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18061-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18061-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18061-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18061-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18061-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18061-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18061-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
