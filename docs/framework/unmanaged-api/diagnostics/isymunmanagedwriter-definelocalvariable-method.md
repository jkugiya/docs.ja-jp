---
description: '詳細について: ISymUnmanagedWriter::D efineLocalVariable メソッド'
title: ISymUnmanagedWriter::DefineLocalVariable メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
ms.openlocfilehash: cd817e3002c2a55fd8bbd7e565283752926f746b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762371"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="823d1-103">ISymUnmanagedWriter::DefineLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="823d1-103">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>

<span data-ttu-id="823d1-104">現在の構文のスコープの変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="823d1-104">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="823d1-105">このメソッドは、スコープ全体で複数のホームを持つ同じ名前の変数に対して複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="823d1-105">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="823d1-106">ただし、この場合は、 `startOffset` パラメーターとパラメーターの値 `endOffset` が重複していてはなりません。</span><span class="sxs-lookup"><span data-stu-id="823d1-106">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="823d1-107">構文</span><span class="sxs-lookup"><span data-stu-id="823d1-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="823d1-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="823d1-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="823d1-109">から `WCHAR` ローカル変数名を定義するへのポインター。</span><span class="sxs-lookup"><span data-stu-id="823d1-109">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="823d1-110">からローカル変数の属性。</span><span class="sxs-lookup"><span data-stu-id="823d1-110">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="823d1-111">から `ULONG32` バッファーのサイズ (バイト単位) を示す `signature` 。</span><span class="sxs-lookup"><span data-stu-id="823d1-111">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="823d1-112">からローカル変数シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="823d1-112">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="823d1-113">からアドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="823d1-113">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="823d1-114">からパラメーター指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="823d1-114">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="823d1-115">からパラメーター指定の2番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="823d1-115">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="823d1-116">からパラメーター指定の3番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="823d1-116">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="823d1-117">から変数の開始オフセット。</span><span class="sxs-lookup"><span data-stu-id="823d1-117">[in] The start offset for the variable.</span></span> <span data-ttu-id="823d1-118">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="823d1-118">This parameter is optional.</span></span> <span data-ttu-id="823d1-119">0の場合、このパラメーターは無視され、スコープ全体にわたって変数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="823d1-119">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="823d1-120">0以外の値の場合、変数は現在のスコープのオフセット内になります。</span><span class="sxs-lookup"><span data-stu-id="823d1-120">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="823d1-121">から変数の終了オフセット。</span><span class="sxs-lookup"><span data-stu-id="823d1-121">[in] The end offset for the variable.</span></span> <span data-ttu-id="823d1-122">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="823d1-122">This parameter is optional.</span></span> <span data-ttu-id="823d1-123">0の場合、このパラメーターは無視され、スコープ全体にわたって変数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="823d1-123">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="823d1-124">0以外の値の場合、変数は現在のスコープのオフセット内になります。</span><span class="sxs-lookup"><span data-stu-id="823d1-124">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="823d1-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="823d1-125">Return Value</span></span>  

 <span data-ttu-id="823d1-126">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="823d1-126">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="823d1-127">要件</span><span class="sxs-lookup"><span data-stu-id="823d1-127">Requirements</span></span>  

 <span data-ttu-id="823d1-128">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="823d1-128">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="823d1-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="823d1-129">See also</span></span>

- [<span data-ttu-id="823d1-130">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="823d1-130">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="823d1-131">DefineGlobalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="823d1-131">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="823d1-132">DefineLocalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="823d1-132">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)
