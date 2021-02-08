---
description: '詳細情報: ICorDebugVirtualUnwinder:: Next メソッド'
title: ICorDebugVirtualUnwinder::Next メソッド
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: b509e8e4fb24c66764999e67ba7e36299ce7f570
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790517"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="7e659-103">ICorDebugVirtualUnwinder::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="7e659-103">ICorDebugVirtualUnwinder::Next Method</span></span>

<span data-ttu-id="7e659-104">呼び出し元のコンテキストに進みます。</span><span class="sxs-lookup"><span data-stu-id="7e659-104">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e659-105">構文</span><span class="sxs-lookup"><span data-stu-id="7e659-105">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e659-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7e659-106">Parameters</span></span>  

 <span data-ttu-id="7e659-107">[なし] :</span><span class="sxs-lookup"><span data-stu-id="7e659-107">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e659-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7e659-108">Return Value</span></span>  

 <span data-ttu-id="7e659-109">アンワインドが正常に発生した場合は `S_OK`、フレームがないためにアンワインドが完了できなかった場合は `CORDBG_S_AT_END_OF_STACK`。</span><span class="sxs-lookup"><span data-stu-id="7e659-109">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="7e659-110">失敗を示す HRESULT が返される場合、ICorDebug API は `CORDBG_E_DATA_TARGET_ERROR` を返します。</span><span class="sxs-lookup"><span data-stu-id="7e659-110">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e659-111">解説</span><span class="sxs-lookup"><span data-stu-id="7e659-111">Remarks</span></span>  

 <span data-ttu-id="7e659-112">スタック ウォーカーにより、前へ進んでいることが確認されます。これにより、最終的に `Next` の呼び出しによって、失敗を示す HRESULT または `CORDBG_S_AT_END_OF_STACK` が返されます。</span><span class="sxs-lookup"><span data-stu-id="7e659-112">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="7e659-113">無制限 `S_OK` に戻ると、無限ループが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7e659-113">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e659-114">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e659-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e659-115">要件</span><span class="sxs-lookup"><span data-stu-id="7e659-115">Requirements</span></span>  

 <span data-ttu-id="7e659-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e659-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e659-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e659-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e659-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e659-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e659-119">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e659-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e659-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e659-120">See also</span></span>

- [<span data-ttu-id="7e659-121">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e659-121">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="7e659-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e659-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
