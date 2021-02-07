---
description: '詳細について: ISymUnmanagedWriter2::D efineConstant2 メソッド'
title: ISymUnmanagedWriter2::DefineConstant2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: 9a0c444909055e18bdcd0b54fefbc8534ff8681e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761929"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="381a6-103">ISymUnmanagedWriter2::DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="381a6-103">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>

<span data-ttu-id="381a6-104">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="381a6-104">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="381a6-105">構文</span><span class="sxs-lookup"><span data-stu-id="381a6-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="381a6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="381a6-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="381a6-107">から定数名。</span><span class="sxs-lookup"><span data-stu-id="381a6-107">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="381a6-108">から定数の値。</span><span class="sxs-lookup"><span data-stu-id="381a6-108">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="381a6-109">から定数のメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="381a6-109">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="381a6-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="381a6-110">Return Value</span></span>  

 <span data-ttu-id="381a6-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="381a6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="381a6-112">要件</span><span class="sxs-lookup"><span data-stu-id="381a6-112">Requirements</span></span>  

 <span data-ttu-id="381a6-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="381a6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="381a6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="381a6-114">See also</span></span>

- [<span data-ttu-id="381a6-115">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="381a6-115">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="381a6-116">DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="381a6-116">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
