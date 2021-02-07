---
description: '詳細について: ISymUnmanagedWriter2::D efineLocalVariable2 メソッド'
title: ISymUnmanagedWriter2::DefineLocalVariable2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
ms.openlocfilehash: 169a086b8420b5dbe20af8e16b21d5b41a958ead
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761812"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="c37e0-103">ISymUnmanagedWriter2::DefineLocalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="c37e0-103">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>

<span data-ttu-id="c37e0-104">現在の構文のスコープの変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="c37e0-104">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="c37e0-105">このメソッドは、スコープ全体で複数のホームを持つ同じ名前の変数に対して複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c37e0-105">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="c37e0-106">ただし、この場合は、 `startOffset` パラメーターとパラメーターの値 `endOffset` が重複していてはなりません。</span><span class="sxs-lookup"><span data-stu-id="c37e0-106">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c37e0-107">構文</span><span class="sxs-lookup"><span data-stu-id="c37e0-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c37e0-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c37e0-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="c37e0-109">からローカル変数名。</span><span class="sxs-lookup"><span data-stu-id="c37e0-109">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="c37e0-110">からローカル変数の属性。</span><span class="sxs-lookup"><span data-stu-id="c37e0-110">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="c37e0-111">から署名のメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="c37e0-111">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="c37e0-112">からアドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="c37e0-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="c37e0-113">からパラメーター指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="c37e0-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="c37e0-114">からパラメーター指定の2番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="c37e0-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="c37e0-115">からパラメーター指定の3番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="c37e0-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="c37e0-116">から変数の開始オフセット。</span><span class="sxs-lookup"><span data-stu-id="c37e0-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="c37e0-117">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c37e0-117">This parameter is optional.</span></span> <span data-ttu-id="c37e0-118">0の場合、このパラメーターは無視され、スコープ全体にわたって変数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="c37e0-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="c37e0-119">0以外の値の場合、変数は現在のスコープのオフセット内になります。</span><span class="sxs-lookup"><span data-stu-id="c37e0-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="c37e0-120">から変数の終了オフセット。</span><span class="sxs-lookup"><span data-stu-id="c37e0-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="c37e0-121">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c37e0-121">This parameter is optional.</span></span> <span data-ttu-id="c37e0-122">0の場合、このパラメーターは無視され、スコープ全体にわたって変数が定義されます。</span><span class="sxs-lookup"><span data-stu-id="c37e0-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="c37e0-123">0以外の値の場合、変数は現在のスコープのオフセット内になります。</span><span class="sxs-lookup"><span data-stu-id="c37e0-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c37e0-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="c37e0-124">Return Value</span></span>  

 <span data-ttu-id="c37e0-125">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c37e0-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c37e0-126">要件</span><span class="sxs-lookup"><span data-stu-id="c37e0-126">Requirements</span></span>  

 <span data-ttu-id="c37e0-127">**ヘッダー:** CorSym .idl</span><span class="sxs-lookup"><span data-stu-id="c37e0-127">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37e0-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="c37e0-128">See also</span></span>

- [<span data-ttu-id="c37e0-129">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c37e0-129">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="c37e0-130">DefineLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="c37e0-130">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
