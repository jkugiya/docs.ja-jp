---
description: '詳細について: ISymUnmanagedScope:: GetChildren メソッド'
title: ISymUnmanagedScope::GetChildren メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: 55d72c98d34fcb30a479611895228fbc1b9f7f55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763502"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="8d47f-103">ISymUnmanagedScope::GetChildren メソッド</span><span class="sxs-lookup"><span data-stu-id="8d47f-103">ISymUnmanagedScope::GetChildren Method</span></span>

<span data-ttu-id="8d47f-104">このスコープの子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8d47f-104">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d47f-105">構文</span><span class="sxs-lookup"><span data-stu-id="8d47f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d47f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d47f-106">Parameters</span></span>  

 `cChildren`  
 <span data-ttu-id="8d47f-107">から `ULONG32` 配列のサイズを示す `children` 。</span><span class="sxs-lookup"><span data-stu-id="8d47f-107">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="8d47f-108">入出力 `ULONG32` 子を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8d47f-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="8d47f-109">入出力返された子の配列。</span><span class="sxs-lookup"><span data-stu-id="8d47f-109">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d47f-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="8d47f-110">Return Value</span></span>  

 <span data-ttu-id="8d47f-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8d47f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d47f-112">要件</span><span class="sxs-lookup"><span data-stu-id="8d47f-112">Requirements</span></span>  

 <span data-ttu-id="8d47f-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="8d47f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d47f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d47f-114">See also</span></span>

- [<span data-ttu-id="8d47f-115">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d47f-115">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="8d47f-116">GetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="8d47f-116">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)
