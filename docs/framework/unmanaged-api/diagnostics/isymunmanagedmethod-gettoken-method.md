---
description: '詳細について: ISymUnmanagedMethod:: GetToken メソッド'
title: ISymUnmanagedMethod::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
ms.openlocfilehash: fde9936a6e79b9d1fff5b38ee7242cf5bb71369d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721308"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="7e86c-103">ISymUnmanagedMethod::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="7e86c-103">ISymUnmanagedMethod::GetToken Method</span></span>

<span data-ttu-id="7e86c-104">このメソッドのメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="7e86c-104">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e86c-105">構文</span><span class="sxs-lookup"><span data-stu-id="7e86c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e86c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7e86c-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="7e86c-107">入出力 `mdMethodDef` メタデータを格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7e86c-107">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e86c-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7e86c-108">Return Value</span></span>  

 <span data-ttu-id="7e86c-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e86c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e86c-110">要件</span><span class="sxs-lookup"><span data-stu-id="7e86c-110">Requirements</span></span>  

 <span data-ttu-id="7e86c-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="7e86c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e86c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e86c-112">See also</span></span>

- [<span data-ttu-id="7e86c-113">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e86c-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
