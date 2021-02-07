---
description: 詳細については、「ICorDebugStepper2 インターフェイス」を参照してください。
title: ICorDebugStepper2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
ms.openlocfilehash: 31e9216535da239573a7a4ecde8cb2e670ad5418
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717551"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="fa1d7-103">ICorDebugStepper2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa1d7-103">ICorDebugStepper2 Interface</span></span>

<span data-ttu-id="fa1d7-104">マイコードのみ (JMC) デバッグのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="fa1d7-104">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa1d7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="fa1d7-105">Methods</span></span>  
  
|<span data-ttu-id="fa1d7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="fa1d7-106">Method</span></span>|<span data-ttu-id="fa1d7-107">説明</span><span class="sxs-lookup"><span data-stu-id="fa1d7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa1d7-108">SetJMC メソッド</span><span class="sxs-lookup"><span data-stu-id="fa1d7-108">SetJMC Method</span></span>](icordebugstepper2-setjmc-method.md)|<span data-ttu-id="fa1d7-109">この ICorDebugStepper が、アプリケーションの開発者によって作成されたコードのみを使用するかどうかを指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="fa1d7-109">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa1d7-110">解説</span><span class="sxs-lookup"><span data-stu-id="fa1d7-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa1d7-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="fa1d7-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa1d7-112">要件</span><span class="sxs-lookup"><span data-stu-id="fa1d7-112">Requirements</span></span>  

 <span data-ttu-id="fa1d7-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa1d7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa1d7-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa1d7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa1d7-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa1d7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa1d7-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa1d7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1d7-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa1d7-117">See also</span></span>

- [<span data-ttu-id="fa1d7-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa1d7-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
