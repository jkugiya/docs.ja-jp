---
description: '詳細について: ISymUnmanagedMethod:: GetRootScope メソッド'
title: ISymUnmanagedMethod::GetRootScope メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
ms.openlocfilehash: b1e490d8e0c5e0d60143202dd0291237685c950f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710006"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="27b79-103">ISymUnmanagedMethod::GetRootScope メソッド</span><span class="sxs-lookup"><span data-stu-id="27b79-103">ISymUnmanagedMethod::GetRootScope Method</span></span>

<span data-ttu-id="27b79-104">このメソッド内のルート構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="27b79-104">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="27b79-105">このスコープはメソッド全体を囲みます。</span><span class="sxs-lookup"><span data-stu-id="27b79-105">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27b79-106">構文</span><span class="sxs-lookup"><span data-stu-id="27b79-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27b79-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27b79-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="27b79-108">入出力返された [ISymUnmanagedScope](isymunmanagedscope-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="27b79-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27b79-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="27b79-109">Return Value</span></span>  

 <span data-ttu-id="27b79-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="27b79-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27b79-111">要件</span><span class="sxs-lookup"><span data-stu-id="27b79-111">Requirements</span></span>  

 <span data-ttu-id="27b79-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="27b79-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b79-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="27b79-113">See also</span></span>

- [<span data-ttu-id="27b79-114">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27b79-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
