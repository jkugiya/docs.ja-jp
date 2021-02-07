---
description: '詳細について: ICorDebugProcess2:: SetUnmanagedBreakpoint メソッド'
title: ICorDebugProcess2::SetUnmanagedBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: 7989f0fc9908941513b7d099fde81c79cef82c5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746543"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="18b35-103">ICorDebugProcess2::SetUnmanagedBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="18b35-103">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>

<span data-ttu-id="18b35-104">指定したネイティブイメージオフセットにアンマネージブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="18b35-104">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18b35-105">構文</span><span class="sxs-lookup"><span data-stu-id="18b35-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18b35-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="18b35-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="18b35-107">から `CORDB_ADDRESS` ネイティブイメージオフセットを指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="18b35-107">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="18b35-108">から配列のサイズ (バイト単位) `buffer` 。</span><span class="sxs-lookup"><span data-stu-id="18b35-108">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="18b35-109">入出力ブレークポイントによって置き換えられるオペコードを格納している配列。</span><span class="sxs-lookup"><span data-stu-id="18b35-109">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="18b35-110">入出力配列で返されたバイト数へのポインター `buffer` 。</span><span class="sxs-lookup"><span data-stu-id="18b35-110">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18b35-111">解説</span><span class="sxs-lookup"><span data-stu-id="18b35-111">Remarks</span></span>  

 <span data-ttu-id="18b35-112">ネイティブイメージオフセットが共通言語ランタイム (CLR) 内にある場合、ブレークポイントは無視されます。</span><span class="sxs-lookup"><span data-stu-id="18b35-112">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="18b35-113">これにより、ブレークポイントがデバッガーによって設定されたときに、CLR は帯域外のブレークポイントのディスパッチを回避できます。</span><span class="sxs-lookup"><span data-stu-id="18b35-113">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18b35-114">要件</span><span class="sxs-lookup"><span data-stu-id="18b35-114">Requirements</span></span>  

 <span data-ttu-id="18b35-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18b35-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18b35-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18b35-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18b35-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18b35-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18b35-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18b35-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
