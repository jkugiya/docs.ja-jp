---
description: '詳細について: ICorDebugAssembly2:: IsFullyTrusted メソッド'
title: ICorDebugAssembly2::IsFullyTrusted メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: bc1c4d9a4fa84bac3469aafe8aaa061473e50413
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754109"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="765c0-103">ICorDebugAssembly2::IsFullyTrusted メソッド</span><span class="sxs-lookup"><span data-stu-id="765c0-103">ICorDebugAssembly2::IsFullyTrusted Method</span></span>

<span data-ttu-id="765c0-104">アセンブリにランタイムセキュリティシステムによる完全信頼が付与されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="765c0-104">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="765c0-105">構文</span><span class="sxs-lookup"><span data-stu-id="765c0-105">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="765c0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="765c0-106">Parameters</span></span>  

 `pbFullyTrusted`  
 <span data-ttu-id="765c0-107">[出力] `true` アセンブリにランタイムセキュリティシステムによる完全信頼が付与されている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="765c0-107">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="765c0-108">解説</span><span class="sxs-lookup"><span data-stu-id="765c0-108">Remarks</span></span>  

 <span data-ttu-id="765c0-109">このメソッドは、アセンブリのセキュリティポリシーがまだ解決されていない場合、つまりアセンブリ内のコードがまだ実行されていない場合に、CORDBG_E_NOTREADY の HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="765c0-109">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="765c0-110">要件</span><span class="sxs-lookup"><span data-stu-id="765c0-110">Requirements</span></span>  

 <span data-ttu-id="765c0-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="765c0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="765c0-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="765c0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="765c0-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="765c0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="765c0-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="765c0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
