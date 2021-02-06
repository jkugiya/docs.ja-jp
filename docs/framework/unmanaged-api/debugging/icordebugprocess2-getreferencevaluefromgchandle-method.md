---
description: '詳細について: ICorDebugProcess2:: GetReferenceValueFromGCHandle メソッド'
title: ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
ms.openlocfilehash: 02047dee9116d34a365242f2a532766eb60e1c81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650223"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="6f5f2-103">ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="6f5f2-103">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>

<span data-ttu-id="6f5f2-104">ガベージコレクションハンドルを持つ指定したマネージオブジェクトへの参照ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-104">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f5f2-105">構文</span><span class="sxs-lookup"><span data-stu-id="6f5f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f5f2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6f5f2-106">Parameters</span></span>  

 `handle`  
 <span data-ttu-id="6f5f2-107">からガベージコレクションハンドルを持つマネージオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-107">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="6f5f2-108">この値はオブジェクトであり、 <xref:System.IntPtr> <xref:System.Runtime.InteropServices.GCHandle> マネージオブジェクトのから取得できます。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-108">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="6f5f2-109">入出力指定したマネージオブジェクトへの参照を表す、値オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-109">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f5f2-110">解説</span><span class="sxs-lookup"><span data-stu-id="6f5f2-110">Remarks</span></span>  

 <span data-ttu-id="6f5f2-111">返された参照値とガベージコレクション参照値を混同しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-111">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="6f5f2-112">返される参照は、通常の参照のように動作します。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-112">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="6f5f2-113">ブレークポイント後にコードの実行が続行される場合は無効になります。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-113">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="6f5f2-114">ターゲットオブジェクトの有効期間は、参照値の有効期間の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-114">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f5f2-115">メソッドでは `GetReferenceValueFromGCHandle` 、ハンドルは検証されません。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-115">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="6f5f2-116">したがって、 `GetReferenceValueFromGCHandle` メソッドは、無効なハンドルが渡された場合に、デバッガーとデバッグされているコードの両方を破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-116">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f5f2-117">要件</span><span class="sxs-lookup"><span data-stu-id="6f5f2-117">Requirements</span></span>  

 <span data-ttu-id="6f5f2-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f5f2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f5f2-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f5f2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f5f2-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f5f2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f5f2-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f5f2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
