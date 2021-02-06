---
description: '詳細について: ICorDebugModule2:: GetJITCompilerFlags メソッド'
title: ICorDebugModule2::GetJITCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.GetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type:
- apiref
ms.openlocfilehash: f1aa01bf2bc92a6fc20687b726ef1c0a6f860a97
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659973"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="24c50-103">ICorDebugModule2::GetJITCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="24c50-103">ICorDebugModule2::GetJITCompilerFlags Method</span></span>

<span data-ttu-id="24c50-104">この ICorDebugModule2 の just-in-time (JIT) コンパイルを制御するフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="24c50-104">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24c50-105">構文</span><span class="sxs-lookup"><span data-stu-id="24c50-105">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24c50-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="24c50-106">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="24c50-107">入出力JIT コンパイルを制御する [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙体の値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="24c50-107">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24c50-108">要件</span><span class="sxs-lookup"><span data-stu-id="24c50-108">Requirements</span></span>  

 <span data-ttu-id="24c50-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24c50-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24c50-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24c50-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24c50-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24c50-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24c50-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24c50-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
