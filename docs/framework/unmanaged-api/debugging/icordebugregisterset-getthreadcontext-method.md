---
description: '詳細については、次のページを参照してください: いいね!:: GetThreadContext メソッド'
title: ICorDebugRegisterSet::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: be6384562858d04b6e139eda83c172c09f2dfc0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690796"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="7b70a-103">ICorDebugRegisterSet::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="7b70a-103">ICorDebugRegisterSet::GetThreadContext Method</span></span>

<span data-ttu-id="7b70a-104">現在のスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="7b70a-104">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b70a-105">構文</span><span class="sxs-lookup"><span data-stu-id="7b70a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b70a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b70a-106">Parameters</span></span>  

 `contextSize`  
 <span data-ttu-id="7b70a-107">から配列のサイズ (バイト単位) `context` 。</span><span class="sxs-lookup"><span data-stu-id="7b70a-107">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="7b70a-108">[入力、出力] `CONTEXT` 現在のプラットフォームの Win32 構造体を構成するバイト配列。</span><span class="sxs-lookup"><span data-stu-id="7b70a-108">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b70a-109">解説</span><span class="sxs-lookup"><span data-stu-id="7b70a-109">Remarks</span></span>  

 <span data-ttu-id="7b70a-110">`GetThreadContext`スレッドはコンテキストが一時的に変更されている "ハイジャック" 状態になる可能性があるため、デバッガーは Win32 関数の代わりにこの関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b70a-110">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="7b70a-111">返されるデータは、 `CONTEXT` 現在のプラットフォームの Win32 構造体です。</span><span class="sxs-lookup"><span data-stu-id="7b70a-111">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="7b70a-112">非リーフフレームの場合、クライアントは、テキストボックス [:: GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md)を使用して、どのレジスタが有効であるかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b70a-112">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b70a-113">要件</span><span class="sxs-lookup"><span data-stu-id="7b70a-113">Requirements</span></span>  

 <span data-ttu-id="7b70a-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b70a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b70a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b70a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b70a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b70a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b70a-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b70a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b70a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b70a-118">See also</span></span>

- [<span data-ttu-id="7b70a-119">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b70a-119">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="7b70a-120">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b70a-120">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
