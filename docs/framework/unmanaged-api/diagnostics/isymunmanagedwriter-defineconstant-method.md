---
description: '詳細について: ISymUnmanagedWriter::D efineConstant メソッド'
title: ISymUnmanagedWriter::DefineConstant メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
ms.openlocfilehash: 4c3fd3986d42061272406150422f037236c4b9bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762527"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="3cccd-103">ISymUnmanagedWriter::DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="3cccd-103">ISymUnmanagedWriter::DefineConstant Method</span></span>

<span data-ttu-id="3cccd-104">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="3cccd-104">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cccd-105">構文</span><span class="sxs-lookup"><span data-stu-id="3cccd-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cccd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3cccd-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="3cccd-107">から `WCHAR` 定数名を定義するへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3cccd-107">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="3cccd-108">から定数の値。</span><span class="sxs-lookup"><span data-stu-id="3cccd-108">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="3cccd-109">[in] `signature` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="3cccd-109">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="3cccd-110">から定数の型シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="3cccd-110">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cccd-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="3cccd-111">Return Value</span></span>  

 <span data-ttu-id="3cccd-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3cccd-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cccd-113">要件</span><span class="sxs-lookup"><span data-stu-id="3cccd-113">Requirements</span></span>  

 <span data-ttu-id="3cccd-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="3cccd-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cccd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cccd-115">See also</span></span>

- [<span data-ttu-id="3cccd-116">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cccd-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="3cccd-117">DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="3cccd-117">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)
