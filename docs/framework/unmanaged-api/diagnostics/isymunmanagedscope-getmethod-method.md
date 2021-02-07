---
description: '詳細について: ISymUnmanagedScope:: GetMethod メソッド'
title: ISymUnmanagedScope::GetMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: 7dfc5f41d849d47bfaf600e40a7ccc9dd45da676
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763398"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="0cd5a-103">ISymUnmanagedScope::GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="0cd5a-103">ISymUnmanagedScope::GetMethod Method</span></span>

<span data-ttu-id="0cd5a-104">このスコープを格納しているメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="0cd5a-104">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cd5a-105">構文</span><span class="sxs-lookup"><span data-stu-id="0cd5a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cd5a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0cd5a-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="0cd5a-107">入出力返された [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0cd5a-107">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cd5a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0cd5a-108">Return Value</span></span>  

 <span data-ttu-id="0cd5a-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0cd5a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cd5a-110">要件</span><span class="sxs-lookup"><span data-stu-id="0cd5a-110">Requirements</span></span>  

 <span data-ttu-id="0cd5a-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="0cd5a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd5a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cd5a-112">See also</span></span>

- [<span data-ttu-id="0cd5a-113">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0cd5a-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
