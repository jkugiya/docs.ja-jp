---
description: '詳細について: ICorDebugStepper:: Step メソッド'
title: ICorDebugStepper::Step メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: cb45575f7818784addf67eacda35442764e706af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717629"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="64609-103">ICorDebugStepper::Step メソッド</span><span class="sxs-lookup"><span data-stu-id="64609-103">ICorDebugStepper::Step Method</span></span>

<span data-ttu-id="64609-104">この ICorDebugStepper は、含まれるスレッドを1ステップずつ実行します。また、必要に応じて、スレッド内で呼び出される関数を使用したシングルステップ実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="64609-104">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64609-105">構文</span><span class="sxs-lookup"><span data-stu-id="64609-105">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64609-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64609-106">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="64609-107">から `true` スレッド内で呼び出される関数にステップインするには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="64609-107">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="64609-108">関数を `false` ステップオーバーするには、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="64609-108">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64609-109">解説</span><span class="sxs-lookup"><span data-stu-id="64609-109">Remarks</span></span>  

 <span data-ttu-id="64609-110">共通言語ランタイムがこのステッパのフレームで次のマネージ命令を実行すると、手順が完了します。</span><span class="sxs-lookup"><span data-stu-id="64609-110">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="64609-111">`Step`マネージコードに含まれていないステッパでが呼び出された場合、次のマネージコード命令がスレッドによって実行されると、手順が完了します。</span><span class="sxs-lookup"><span data-stu-id="64609-111">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64609-112">要件</span><span class="sxs-lookup"><span data-stu-id="64609-112">Requirements</span></span>  

 <span data-ttu-id="64609-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64609-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64609-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64609-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64609-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64609-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64609-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64609-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
