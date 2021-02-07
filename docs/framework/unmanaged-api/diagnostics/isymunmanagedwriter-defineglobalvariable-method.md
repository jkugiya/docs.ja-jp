---
description: '詳細について: ISymUnmanagedWriter::D efineGlobalVariable メソッド'
title: ISymUnmanagedWriter::DefineGlobalVariable メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: 70dccfed054a9ac79baf3f28683edc9a14d3cdf7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762384"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="d943f-103">ISymUnmanagedWriter::DefineGlobalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="d943f-103">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>

<span data-ttu-id="d943f-104">グローバル変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="d943f-104">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d943f-105">構文</span><span class="sxs-lookup"><span data-stu-id="d943f-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d943f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d943f-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="d943f-107">から `WCHAR` グローバル変数名を定義するへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d943f-107">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="d943f-108">からグローバル変数属性。</span><span class="sxs-lookup"><span data-stu-id="d943f-108">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="d943f-109">から `ULONG32` バッファーのサイズ (文字数) を示す `signature` 。</span><span class="sxs-lookup"><span data-stu-id="d943f-109">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="d943f-110">からグローバル変数シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="d943f-110">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="d943f-111">からアドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="d943f-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="d943f-112">からパラメーター指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="d943f-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="d943f-113">からパラメーター指定の2番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="d943f-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="d943f-114">からパラメーター指定の3番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="d943f-114">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d943f-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="d943f-115">Return Value</span></span>  

 <span data-ttu-id="d943f-116">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d943f-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d943f-117">要件</span><span class="sxs-lookup"><span data-stu-id="d943f-117">Requirements</span></span>  

 <span data-ttu-id="d943f-118">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d943f-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d943f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d943f-119">See also</span></span>

- [<span data-ttu-id="d943f-120">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d943f-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d943f-121">DefineLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="d943f-121">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="d943f-122">DefineGlobalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="d943f-122">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
