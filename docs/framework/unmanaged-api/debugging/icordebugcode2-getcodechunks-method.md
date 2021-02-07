---
description: '詳細について: ICorDebugCode2:: GetCodeChunks メソッド'
title: ICorDebugCode2::GetCodeChunks メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
ms.openlocfilehash: 371d077466ff2390293d9d4e320d4c95a992fe54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764969"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="94fb8-103">ICorDebugCode2::GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="94fb8-103">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="94fb8-104">このコード オブジェクトを構成しているコード チャンクを取得します。</span><span class="sxs-lookup"><span data-stu-id="94fb8-104">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="94fb8-105">構文</span><span class="sxs-lookup"><span data-stu-id="94fb8-105">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="94fb8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94fb8-106">Parameters</span></span>

`cbufSize`  
<span data-ttu-id="94fb8-107">から配列のサイズ `chunks` 。</span><span class="sxs-lookup"><span data-stu-id="94fb8-107">[in] Size of the `chunks` array.</span></span>

`pcnumChunks`  
<span data-ttu-id="94fb8-108">入出力配列で返されたチャンクの数 `chunks` 。</span><span class="sxs-lookup"><span data-stu-id="94fb8-108">[out] The number of chunks returned in the `chunks` array.</span></span>

`chunks`  
<span data-ttu-id="94fb8-109">入出力"CodeChunkInfo" 構造体の配列。それぞれが1つのコードチャンクを表します。</span><span class="sxs-lookup"><span data-stu-id="94fb8-109">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="94fb8-110">の値 `cbufSize` が0の場合、このパラメーターには null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="94fb8-110">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="94fb8-111">解説</span><span class="sxs-lookup"><span data-stu-id="94fb8-111">Remarks</span></span>

<span data-ttu-id="94fb8-112">コードチャンクは重複しません。コードチャンクは、「 [コード:: GetCode](icordebugcode-getcode-method.md)」によって連結された順序に従います。</span><span class="sxs-lookup"><span data-stu-id="94fb8-112">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="94fb8-113">.NET Framework バージョン2.0 の Microsoft 中間言語 (MSIL) コードオブジェクトは、1つのコードチャンクを構成します。</span><span class="sxs-lookup"><span data-stu-id="94fb8-113">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="94fb8-114">要件</span><span class="sxs-lookup"><span data-stu-id="94fb8-114">Requirements</span></span>

<span data-ttu-id="94fb8-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94fb8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="94fb8-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94fb8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="94fb8-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94fb8-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="94fb8-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94fb8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
