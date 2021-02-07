---
description: 詳細については、次のメソッドを参照してください:、次のメソッド
title: ICorDebugCodeEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
ms.openlocfilehash: 51d46718891ce3df537c675175eacc4e33b92f79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764750"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="03592-103">ICorDebugCodeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="03592-103">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="03592-104">現在の位置から開始して、指定した数の "コード" インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="03592-104">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="03592-105">構文</span><span class="sxs-lookup"><span data-stu-id="03592-105">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="03592-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03592-106">Parameters</span></span>

`celt`  
<span data-ttu-id="03592-107">から `ICorDebugCode` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="03592-107">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

`values`  
<span data-ttu-id="03592-108">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugCode` ます。</span><span class="sxs-lookup"><span data-stu-id="03592-108">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

`pceltFetched`  
<span data-ttu-id="03592-109">入出力実際に返されたインスタンスの数へのポインター `ICorDebugCode` 。</span><span class="sxs-lookup"><span data-stu-id="03592-109">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="03592-110">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="03592-110">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="03592-111">要件</span><span class="sxs-lookup"><span data-stu-id="03592-111">Requirements</span></span>

<span data-ttu-id="03592-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03592-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="03592-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03592-113">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="03592-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03592-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="03592-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03592-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
