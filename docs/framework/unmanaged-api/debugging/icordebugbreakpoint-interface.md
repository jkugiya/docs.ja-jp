---
description: 詳細については、「ICorDebugBreakpoint インターフェイス」を参照してください。
title: ICorDebugBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 63917512cceeccedea37acdf2ba7ab3b849d9fad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711805"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="cac19-103">ICorDebugBreakpoint インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cac19-103">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="cac19-104">関数内のブレークポイント、または値のウォッチポイントを表します。</span><span class="sxs-lookup"><span data-stu-id="cac19-104">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cac19-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cac19-105">Methods</span></span>  
  
|<span data-ttu-id="cac19-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cac19-106">Method</span></span>|<span data-ttu-id="cac19-107">説明</span><span class="sxs-lookup"><span data-stu-id="cac19-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cac19-108">Activate メソッド</span><span class="sxs-lookup"><span data-stu-id="cac19-108">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="cac19-109">こののアクティブな状態を設定 `ICorDebugBreakpoint` します。</span><span class="sxs-lookup"><span data-stu-id="cac19-109">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="cac19-110">IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="cac19-110">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="cac19-111">このがアクティブかどうかを示す値を取得し `ICorDebugBreakpoint` ます。</span><span class="sxs-lookup"><span data-stu-id="cac19-111">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cac19-112">解説</span><span class="sxs-lookup"><span data-stu-id="cac19-112">Remarks</span></span>  

 <span data-ttu-id="cac19-113">ブレークポイントは、条件式を直接サポートしません。</span><span class="sxs-lookup"><span data-stu-id="cac19-113">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="cac19-114">このような機能が必要な場合は、デバッガーでを上に実装する必要があり `ICorDebugBreakpoint` ます。</span><span class="sxs-lookup"><span data-stu-id="cac19-114">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="cac19-115">は、 `ICorDebugBreakpoint` 関数内のブレークポイントをサポートするために、によって拡張されます。</span><span class="sxs-lookup"><span data-stu-id="cac19-115">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cac19-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cac19-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cac19-117">要件</span><span class="sxs-lookup"><span data-stu-id="cac19-117">Requirements</span></span>  

 <span data-ttu-id="cac19-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cac19-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cac19-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cac19-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cac19-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cac19-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cac19-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cac19-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac19-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="cac19-122">See also</span></span>

- [<span data-ttu-id="cac19-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cac19-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
