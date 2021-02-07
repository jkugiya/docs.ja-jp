---
description: '詳細について: ICorDebugMutableDataTarget:: SetThreadContext メソッド'
title: ICorDebugMutableDataTarget::SetThreadContext メソッド
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 4674df92b72b44e19eff663c9a17dd8ca4b5a1b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722478"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="6e41c-103">ICorDebugMutableDataTarget::SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="6e41c-103">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>

<span data-ttu-id="6e41c-104">スレッドのコンテキスト (レジスタの値) を設定します。</span><span class="sxs-lookup"><span data-stu-id="6e41c-104">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e41c-105">構文</span><span class="sxs-lookup"><span data-stu-id="6e41c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e41c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e41c-106">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="6e41c-107">[in] オペレーティング システム定義のスレッド識別子。</span><span class="sxs-lookup"><span data-stu-id="6e41c-107">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6e41c-108">[in]書き込まれる `pContext` バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="6e41c-108">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="6e41c-109">[in]書き込まれるバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6e41c-109">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e41c-110">解説</span><span class="sxs-lookup"><span data-stu-id="6e41c-110">Remarks</span></span>  

 <span data-ttu-id="6e41c-111">`SetThreadContext` メソッドは、オペレーティング システム定義の `dwThreadID` 引数で指定されるスレッドの現在のコンテキストを更新します。</span><span class="sxs-lookup"><span data-stu-id="6e41c-111">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="6e41c-112">コンテキストレコードの形式は、のプラットフォームによって決定されます。このプラットフォームでは、次 [のように](icordebugdatatarget-getplatform-method.md) 指定します。</span><span class="sxs-lookup"><span data-stu-id="6e41c-112">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="6e41c-113">Windows では、これは [コンテキスト](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) 構造です。</span><span class="sxs-lookup"><span data-stu-id="6e41c-113">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e41c-114">要件</span><span class="sxs-lookup"><span data-stu-id="6e41c-114">Requirements</span></span>  

 <span data-ttu-id="6e41c-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e41c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e41c-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e41c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e41c-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e41c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e41c-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e41c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e41c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e41c-119">See also</span></span>

- [<span data-ttu-id="6e41c-120">ICorDebugMutableDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e41c-120">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="6e41c-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e41c-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
