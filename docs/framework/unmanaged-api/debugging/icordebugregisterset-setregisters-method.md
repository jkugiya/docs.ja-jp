---
description: '詳細については、次のページを参照してください: いいね!:: SetRegisters メソッド'
title: ICorDebugRegisterSet::SetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: 7a83d9d01a392d7ed435292f45ee0c75765ced36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690679"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="df4ae-103">ICorDebugRegisterSet::SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="df4ae-103">ICorDebugRegisterSet::SetRegisters Method</span></span>

<span data-ttu-id="df4ae-104">`SetRegisters` は .NET Framework バージョン2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="df4ae-104">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="df4ae-105">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="df4ae-105">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df4ae-106">「いいね!: [: setip](icordebugilframe-setip-method.md) 」や「いいね!: [: setip](icordebugnativeframe-setip-method.md)」などの上位レベルの操作を使用します。</span><span class="sxs-lookup"><span data-stu-id="df4ae-106">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df4ae-107">構文</span><span class="sxs-lookup"><span data-stu-id="df4ae-107">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="df4ae-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="df4ae-108">Requirements</span></span>  

 <span data-ttu-id="df4ae-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df4ae-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df4ae-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df4ae-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df4ae-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df4ae-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df4ae-112">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="df4ae-112">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df4ae-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="df4ae-113">See also</span></span>

- [<span data-ttu-id="df4ae-114">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df4ae-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="df4ae-115">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df4ae-115">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
