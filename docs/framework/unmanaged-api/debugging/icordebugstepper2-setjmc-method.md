---
description: '詳細について: ICorDebugStepper2:: SetJMC メソッド'
title: ICorDebugStepper2::SetJMC メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
ms.openlocfilehash: 07178ab90bb392e64c9d8a8fddf961efbb268002
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717538"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="d32a4-103">ICorDebugStepper2::SetJMC メソッド</span><span class="sxs-lookup"><span data-stu-id="d32a4-103">ICorDebugStepper2::SetJMC Method</span></span>

<span data-ttu-id="d32a4-104">この ICorDebugStepper が、アプリケーションの開発者によって作成されたコードのみを使用するかどうかを指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d32a4-104">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="d32a4-105">このプロセスは、"マイコードのみ" (JMC) デバッグとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d32a4-105">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d32a4-106">構文</span><span class="sxs-lookup"><span data-stu-id="d32a4-106">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d32a4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d32a4-107">Parameters</span></span>  

 `fIsJMCStepper`  
 <span data-ttu-id="d32a4-108">から `true` アプリケーションの開発者によって作成されたコードのみをステップ実行するには、をに設定します。それ以外の場合はに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="d32a4-108">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d32a4-109">要件</span><span class="sxs-lookup"><span data-stu-id="d32a4-109">Requirements</span></span>  

 <span data-ttu-id="d32a4-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d32a4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d32a4-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d32a4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d32a4-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d32a4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d32a4-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d32a4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
