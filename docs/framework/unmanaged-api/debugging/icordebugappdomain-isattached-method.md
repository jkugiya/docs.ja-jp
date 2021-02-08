---
description: '詳細については、次を参照してください: いいね::、IsAttached メソッド'
title: ICorDebugAppDomain::IsAttached メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
ms.openlocfilehash: 79427d08be9ffea253695b67767d68589edf6979
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772384"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="03365-103">ICorDebugAppDomain::IsAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="03365-103">ICorDebugAppDomain::IsAttached Method</span></span>

<span data-ttu-id="03365-104">デバッガーがアプリケーションドメインにアタッチされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="03365-104">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03365-105">構文</span><span class="sxs-lookup"><span data-stu-id="03365-105">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03365-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03365-106">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="03365-107">[出力] `true` デバッガーがアプリケーションドメインにアタッチされている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="03365-107">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03365-108">解説</span><span class="sxs-lookup"><span data-stu-id="03365-108">Remarks</span></span>  

 <span data-ttu-id="03365-109">このデバッガーがアプリケーションドメインにアタッチされるまでは、このコントロールメソッドを使用できません。</span><span class="sxs-lookup"><span data-stu-id="03365-109">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03365-110">要件</span><span class="sxs-lookup"><span data-stu-id="03365-110">Requirements</span></span>  

 <span data-ttu-id="03365-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03365-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03365-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03365-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03365-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03365-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03365-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03365-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
