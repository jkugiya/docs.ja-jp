---
description: '詳細について: ISymUnmanagedENCUpdate:: UpdateMethodLines メソッド'
title: ISymUnmanagedENCUpdate::UpdateMethodLines メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
ms.openlocfilehash: 6174f3aa980ccf2cdc07720e3aa90b7bb74a77af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710063"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="c0c8b-103">ISymUnmanagedENCUpdate::UpdateMethodLines メソッド</span><span class="sxs-lookup"><span data-stu-id="c0c8b-103">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>

<span data-ttu-id="c0c8b-104">再コンパイルされていないが、行が個別に移動したメソッドの行情報を更新できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c0c8b-104">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="c0c8b-105">各ステートメントのデルタが許可されます。</span><span class="sxs-lookup"><span data-stu-id="c0c8b-105">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0c8b-106">構文</span><span class="sxs-lookup"><span data-stu-id="c0c8b-106">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0c8b-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c0c8b-107">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="c0c8b-108">からメソッドトークンのメタデータ。</span><span class="sxs-lookup"><span data-stu-id="c0c8b-108">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="c0c8b-109">から `INT32` メソッド内の各シーケンスポイントのデルタを示す値の配列。</span><span class="sxs-lookup"><span data-stu-id="c0c8b-109">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="c0c8b-110">から `ULONG` パラメーターのサイズを格納している `pDeltas` 。</span><span class="sxs-lookup"><span data-stu-id="c0c8b-110">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0c8b-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="c0c8b-111">Return Value</span></span>  

 <span data-ttu-id="c0c8b-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0c8b-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0c8b-113">要件</span><span class="sxs-lookup"><span data-stu-id="c0c8b-113">Requirements</span></span>  

 <span data-ttu-id="c0c8b-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c0c8b-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c8b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0c8b-115">See also</span></span>

- [<span data-ttu-id="c0c8b-116">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0c8b-116">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
