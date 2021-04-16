---
description: '詳細情報: ICorDebugRegisterSet::SetThreadContext メソッド'
title: ICorDebugRegisterSet::SetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: 8d874b1864e85e477260632ad6012dbbf10aefb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637691"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="fa6a0-103">ICorDebugRegisterSet::SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="fa6a0-103">ICorDebugRegisterSet::SetThreadContext Method</span></span>

<span data-ttu-id="fa6a0-104">`SetThreadContext` は、.NET Framework バージョン 2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="fa6a0-104">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="fa6a0-105">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="fa6a0-105">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa6a0-106">スレッドのコンテキストを設定するには、高レベルの操作の [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="fa6a0-106">Use the higher-level operation [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa6a0-107">構文</span><span class="sxs-lookup"><span data-stu-id="fa6a0-107">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fa6a0-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="fa6a0-108">Requirements</span></span>  

 <span data-ttu-id="fa6a0-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa6a0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa6a0-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa6a0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa6a0-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa6a0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa6a0-112">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="fa6a0-112">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa6a0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa6a0-113">See also</span></span>

- [<span data-ttu-id="fa6a0-114">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa6a0-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="fa6a0-115">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa6a0-115">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
