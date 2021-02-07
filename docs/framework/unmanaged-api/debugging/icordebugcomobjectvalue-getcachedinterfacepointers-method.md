---
description: '詳細については、次を参照してください: GetCachedInterfacePointers メソッド'
title: ICorDebugComObjectValue::GetCachedInterfacePointers メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: 737d71f6aa903a3dfa97f583b47a322ec074147f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710856"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="b00b5-103">ICorDebugComObjectValue::GetCachedInterfacePointers メソッド</span><span class="sxs-lookup"><span data-stu-id="b00b5-103">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>

<span data-ttu-id="b00b5-104">現在のランタイム呼び出し可能ラッパー (RCW) にキャッシュされている生のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b00b5-104">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b00b5-105">構文</span><span class="sxs-lookup"><span data-stu-id="b00b5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b00b5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b00b5-106">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="b00b5-107">からメソッドが、 `IInspectable` ランタイム呼び出し可能ラッパー (RCW) によってキャッシュされた Windows ランタイムインターフェイス (インターフェイス) またはすべての COM インターフェイスだけを返すかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="b00b5-107">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="b00b5-108">からアドレスを取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="b00b5-108">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b00b5-109">入出力 `CORDB_ADDRESS` で実際に返される値の数へのポインター `ptrs` 。</span><span class="sxs-lookup"><span data-stu-id="b00b5-109">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="b00b5-110">キャッシュされた `CORDB_ADDRESS` インターフェイスオブジェクトのアドレスを格納している値の配列の開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b00b5-110">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b00b5-111">解説</span><span class="sxs-lookup"><span data-stu-id="b00b5-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b00b5-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="b00b5-112">Requirements</span></span>  

 <span data-ttu-id="b00b5-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b00b5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b00b5-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b00b5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b00b5-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b00b5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b00b5-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b00b5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00b5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b00b5-117">See also</span></span>

- [<span data-ttu-id="b00b5-118">ICorDebugComObjectValue のインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b00b5-118">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="b00b5-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b00b5-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
