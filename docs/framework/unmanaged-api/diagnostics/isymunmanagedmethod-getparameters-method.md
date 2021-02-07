---
description: '詳細について: ISymUnmanagedMethod:: GetParameters メソッド'
title: ISymUnmanagedMethod::GetParameters メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
ms.openlocfilehash: c8860a4d42019aaacef01879b175fd45ea837f2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721373"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="f6730-103">ISymUnmanagedMethod::GetParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="f6730-103">ISymUnmanagedMethod::GetParameters Method</span></span>

<span data-ttu-id="f6730-104">このメソッドのパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f6730-104">Gets the parameters for this method.</span></span> <span data-ttu-id="f6730-105">パラメーターは、メソッドのシグネチャ内で定義されている順序で返されます。</span><span class="sxs-lookup"><span data-stu-id="f6730-105">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6730-106">構文</span><span class="sxs-lookup"><span data-stu-id="f6730-106">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6730-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f6730-107">Parameters</span></span>  

 `cParams`  
 <span data-ttu-id="f6730-108">[in] `params` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f6730-108">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="f6730-109">から `ULONG32` パラメーターを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f6730-109">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="f6730-110">入出力パラメーターを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f6730-110">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6730-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="f6730-111">Return Value</span></span>  

 <span data-ttu-id="f6730-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6730-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6730-113">要件</span><span class="sxs-lookup"><span data-stu-id="f6730-113">Requirements</span></span>  

 <span data-ttu-id="f6730-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f6730-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6730-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6730-115">See also</span></span>

- [<span data-ttu-id="f6730-116">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6730-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
