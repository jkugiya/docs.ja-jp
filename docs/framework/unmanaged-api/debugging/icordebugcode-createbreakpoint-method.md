---
description: '詳細情報: Okcode:: CreateBreakpoint ポイントメソッド'
title: ICorDebugCode::CreateBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: a9285d59da3e3f34ea303413fca67bc39aff9e32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711376"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="6aea5-103">ICorDebugCode::CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="6aea5-103">ICorDebugCode::CreateBreakpoint Method</span></span>

<span data-ttu-id="6aea5-104">このコードセグメントの指定したオフセット位置にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="6aea5-104">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aea5-105">構文</span><span class="sxs-lookup"><span data-stu-id="6aea5-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aea5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6aea5-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="6aea5-107">からブレークポイントを作成する位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="6aea5-107">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="6aea5-108">入出力ブレークポイントを表す "いいね! ブレークポイント" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6aea5-108">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aea5-109">解説</span><span class="sxs-lookup"><span data-stu-id="6aea5-109">Remarks</span></span>  

 <span data-ttu-id="6aea5-110">ブレークポイントがアクティブになる前に、そのブレークポイントをプロセスオブジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6aea5-110">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="6aea5-111">このコードが Microsoft 中間言語 (MSIL) コードで、just-in-time (JIT) でコンパイルされたネイティブバージョンのコードがある場合、ブレークポイントは JIT コンパイルコードにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="6aea5-111">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="6aea5-112">(コードが後で JIT コンパイルされる場合も同様です)。</span><span class="sxs-lookup"><span data-stu-id="6aea5-112">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aea5-113">要件</span><span class="sxs-lookup"><span data-stu-id="6aea5-113">Requirements</span></span>  

 <span data-ttu-id="6aea5-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6aea5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aea5-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6aea5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6aea5-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6aea5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aea5-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aea5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
