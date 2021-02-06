---
description: '詳細について: 「GetEHClauses メソッド」を参照してください。'
title: ICorDebugILCode::GetEHClauses メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
ms.openlocfilehash: e790f0f1f69a38d3a1be9e98eacfc5e37be0fd05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660662"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="b8030-103">ICorDebugILCode::GetEHClauses メソッド</span><span class="sxs-lookup"><span data-stu-id="b8030-103">ICorDebugILCode::GetEHClauses Method</span></span>

<span data-ttu-id="b8030-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="b8030-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b8030-105">この中間言語 (IL) に対して定義されている例外処理 (EH) 句のリストへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="b8030-105">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8030-106">構文</span><span class="sxs-lookup"><span data-stu-id="b8030-106">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8030-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8030-107">Parameters</span></span>  

 `cClauses`  
 <span data-ttu-id="b8030-108">[入力] `clauses` 配列の記憶容量。</span><span class="sxs-lookup"><span data-stu-id="b8030-108">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="b8030-109">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8030-109">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="b8030-110">[out] 情報が `clauses` アレイに書き込まれる場合に、対象となる句の数。</span><span class="sxs-lookup"><span data-stu-id="b8030-110">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="b8030-111">句</span><span class="sxs-lookup"><span data-stu-id="b8030-111">clauses</span></span>  
 <span data-ttu-id="b8030-112">入出力この IL に対して定義されている例外処理句に関する情報を格納する [CorDebugEHClause](cordebugehclause-structure.md) オブジェクトの配列。</span><span class="sxs-lookup"><span data-stu-id="b8030-112">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8030-113">解説</span><span class="sxs-lookup"><span data-stu-id="b8030-113">Remarks</span></span>  

 <span data-ttu-id="b8030-114">`cClauses`が0で、 `pcClauses` が **null** 以外の場合、 `pcClauses` は使用可能な例外処理句の数に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b8030-114">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="b8030-115">`cClauses` が 0 以外の場合は、`clauses` アレイの記憶容量を表します。</span><span class="sxs-lookup"><span data-stu-id="b8030-115">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="b8030-116">メソッドが戻るとき、`clauses` には、`cClauses` の最大項目が含まれ、`pcClauses` は、実際に`clauses` アレイに書き込まれる句の数が設定されます。</span><span class="sxs-lookup"><span data-stu-id="b8030-116">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8030-117">要件</span><span class="sxs-lookup"><span data-stu-id="b8030-117">Requirements</span></span>  

 <span data-ttu-id="b8030-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8030-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8030-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8030-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8030-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8030-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8030-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8030-121">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8030-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8030-122">See also</span></span>

- [<span data-ttu-id="b8030-123">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8030-123">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="b8030-124">CorDebugEHClause 構造体</span><span class="sxs-lookup"><span data-stu-id="b8030-124">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="b8030-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8030-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
