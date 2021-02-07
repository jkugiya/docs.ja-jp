---
description: '詳細については、次の情報を参照してください: の関数:: GetLocalVarSigToken メソッド'
title: ICorDebugFunction::GetLocalVarSigToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
ms.openlocfilehash: cd7fb03829285ddcb1da2f1a93985fa1f98d3d39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692499"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="11c48-103">ICorDebugFunction::GetLocalVarSigToken メソッド</span><span class="sxs-lookup"><span data-stu-id="11c48-103">ICorDebugFunction::GetLocalVarSigToken Method</span></span>

<span data-ttu-id="11c48-104">このによって表される関数の、ローカル変数シグネチャのメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="11c48-104">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c48-105">構文</span><span class="sxs-lookup"><span data-stu-id="11c48-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11c48-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11c48-106">Parameters</span></span>  

 `pmdSig`  
 <span data-ttu-id="11c48-107">入出力 `mdSignature` この関数のローカル変数シグネチャのトークンへのポインター `mdSignatureNil` 。この関数にローカル変数がない場合は。</span><span class="sxs-lookup"><span data-stu-id="11c48-107">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c48-108">要件</span><span class="sxs-lookup"><span data-stu-id="11c48-108">Requirements</span></span>  

 <span data-ttu-id="11c48-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11c48-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c48-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11c48-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11c48-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11c48-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11c48-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c48-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
