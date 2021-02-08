---
description: '詳細情報: ICorDebugRegisterSet2:: SetRegisters メソッド'
title: ICorDebugRegisterSet2::SetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
ms.openlocfilehash: d58717be34e146def2a54bb49d6cd58dde7564c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794755"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="1284e-103">ICorDebugRegisterSet2::SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="1284e-103">ICorDebugRegisterSet2::SetRegisters Method</span></span>

<span data-ttu-id="1284e-104">`SetRegisters` は .NET Framework バージョン2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="1284e-104">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="1284e-105">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="1284e-105">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1284e-106">「いいね!: [: setip](icordebugilframe-setip-method.md) 」や「いいね!: [: setip](icordebugnativeframe-setip-method.md)」などの上位レベルの操作を使用します。</span><span class="sxs-lookup"><span data-stu-id="1284e-106">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1284e-107">構文</span><span class="sxs-lookup"><span data-stu-id="1284e-107">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1284e-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="1284e-108">Requirements</span></span>  

 <span data-ttu-id="1284e-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1284e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1284e-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1284e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1284e-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1284e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1284e-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1284e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1284e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1284e-113">See also</span></span>

- [<span data-ttu-id="1284e-114">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1284e-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="1284e-115">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1284e-115">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
