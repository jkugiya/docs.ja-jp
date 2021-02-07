---
description: '詳細について: ISymUnmanagedMethod:: GetNamespace メソッド'
title: ISymUnmanagedMethod::GetNamespace メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
ms.openlocfilehash: 8cb211b1047aff31cc4f12d538fee414c578155b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721412"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="7ca4d-103">ISymUnmanagedMethod::GetNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="7ca4d-103">ISymUnmanagedMethod::GetNamespace Method</span></span>

<span data-ttu-id="7ca4d-104">このメソッドが定義されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="7ca4d-104">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca4d-105">構文</span><span class="sxs-lookup"><span data-stu-id="7ca4d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ca4d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7ca4d-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="7ca4d-107">入出力返された [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="7ca4d-107">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ca4d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7ca4d-108">Return Value</span></span>  

 <span data-ttu-id="7ca4d-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ca4d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca4d-110">要件</span><span class="sxs-lookup"><span data-stu-id="7ca4d-110">Requirements</span></span>  

 <span data-ttu-id="7ca4d-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="7ca4d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca4d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ca4d-112">See also</span></span>

- [<span data-ttu-id="7ca4d-113">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7ca4d-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
