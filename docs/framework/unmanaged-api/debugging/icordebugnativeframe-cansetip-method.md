---
description: '詳細情報: ICorDebugNativeFrame::CanSetIP メソッド'
title: ICorDebugNativeFrame::CanSetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: ec8f257b44143332063d7579b62dcc2afe0fccdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637860"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="2f8e6-103">ICorDebugNativeFrame::CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="2f8e6-103">ICorDebugNativeFrame::CanSetIP Method</span></span>

<span data-ttu-id="2f8e6-104">命令ポインター (IP) をネイティブ コードで指定したオフセット位置に安全に設定できるかどうかを示す HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="2f8e6-104">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f8e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f8e6-105">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f8e6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f8e6-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="2f8e6-107">[in] 命令ポインターに必要な設定。</span><span class="sxs-lookup"><span data-stu-id="2f8e6-107">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f8e6-108">解説</span><span class="sxs-lookup"><span data-stu-id="2f8e6-108">Remarks</span></span>  

 <span data-ttu-id="2f8e6-109">`CanSetIP` メソッドは、[ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) メソッドを呼び出す前に使用します。</span><span class="sxs-lookup"><span data-stu-id="2f8e6-109">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="2f8e6-110">`CanSetIP` が S_OK 以外の HRESULT を返した場合でも、`ICorDebugNativeFrame::SetIP` を呼び出すことはできますが、デバッグ対象のコードがデバッガーによって引き続き安全かつ適切に実行される保証はありません。</span><span class="sxs-lookup"><span data-stu-id="2f8e6-110">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f8e6-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="2f8e6-111">Requirements</span></span>  

 <span data-ttu-id="2f8e6-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f8e6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f8e6-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f8e6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f8e6-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f8e6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f8e6-115">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f8e6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8e6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f8e6-116">See also</span></span>
