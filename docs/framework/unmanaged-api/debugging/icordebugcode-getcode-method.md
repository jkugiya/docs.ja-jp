---
description: '詳細情報: 「コード:: GetCode メソッド」を参照してください。'
title: ICorDebugCode::GetCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: 329770fac4f2b375c01dd68e4ea7114e59c609b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711285"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="7f31d-103">ICorDebugCode::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="7f31d-103">ICorDebugCode::GetCode Method</span></span>

<span data-ttu-id="7f31d-104">指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="7f31d-104">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="7f31d-105">このメソッドは .NET Framework バージョン2.0 では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="7f31d-105">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="7f31d-106">代わりに [ICorDebugCode2:: GetCodeChunks](icordebugcode2-getcodechunks-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="7f31d-106">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f31d-107">構文</span><span class="sxs-lookup"><span data-stu-id="7f31d-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f31d-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f31d-108">Parameters</span></span>  

 `startOffset`  
 <span data-ttu-id="7f31d-109">から関数の開始位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="7f31d-109">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="7f31d-110">から関数の終了位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="7f31d-110">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="7f31d-111">からコードが返される `buffer` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="7f31d-111">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="7f31d-112">入出力コードが返される配列。</span><span class="sxs-lookup"><span data-stu-id="7f31d-112">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="7f31d-113">入出力返されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="7f31d-113">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f31d-114">解説</span><span class="sxs-lookup"><span data-stu-id="7f31d-114">Remarks</span></span>  

 <span data-ttu-id="7f31d-115">関数のコードが複数のチャンクに分割されている場合は、ネイティブオフセットが増加する順序で連結されます。</span><span class="sxs-lookup"><span data-stu-id="7f31d-115">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="7f31d-116">命令の境界はチェックされません。</span><span class="sxs-lookup"><span data-stu-id="7f31d-116">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f31d-117">要件</span><span class="sxs-lookup"><span data-stu-id="7f31d-117">Requirements</span></span>  

 <span data-ttu-id="7f31d-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f31d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f31d-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f31d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f31d-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f31d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f31d-121">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="7f31d-121">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f31d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f31d-122">See also</span></span>

- [<span data-ttu-id="7f31d-123">GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="7f31d-123">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
