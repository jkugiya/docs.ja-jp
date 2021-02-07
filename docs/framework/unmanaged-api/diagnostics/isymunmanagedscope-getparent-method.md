---
description: '詳細について: ISymUnmanagedScope:: GetParent メソッド'
title: ISymUnmanagedScope::GetParent メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
ms.openlocfilehash: c6a056c828bfaefd171ef3f0c546d93d30fb6863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763333"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="d5501-103">ISymUnmanagedScope::GetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="d5501-103">ISymUnmanagedScope::GetParent Method</span></span>

<span data-ttu-id="d5501-104">このスコープの親スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5501-104">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5501-105">構文</span><span class="sxs-lookup"><span data-stu-id="d5501-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5501-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5501-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="d5501-107">入出力返された [ISymUnmanagedScope](isymunmanagedscope-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d5501-107">[out] A pointer to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5501-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="d5501-108">Return Value</span></span>  

 <span data-ttu-id="d5501-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d5501-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5501-110">要件</span><span class="sxs-lookup"><span data-stu-id="d5501-110">Requirements</span></span>  

 <span data-ttu-id="d5501-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d5501-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5501-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5501-112">See also</span></span>

- [<span data-ttu-id="d5501-113">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5501-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="d5501-114">GetChildren メソッド</span><span class="sxs-lookup"><span data-stu-id="d5501-114">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)
