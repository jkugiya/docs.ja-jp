---
description: '詳細について: ISymUnmanagedScope:: GetLocalCount メソッド'
title: ISymUnmanagedScope::GetLocalCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 987d161d273b12810988ef30acb703973098d29c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763441"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="b7081-103">ISymUnmanagedScope::GetLocalCount メソッド</span><span class="sxs-lookup"><span data-stu-id="b7081-103">ISymUnmanagedScope::GetLocalCount Method</span></span>

<span data-ttu-id="b7081-104">このスコープ内で定義されているローカル変数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="b7081-104">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7081-105">構文</span><span class="sxs-lookup"><span data-stu-id="b7081-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7081-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7081-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="b7081-107">入出力 `ULONG32` ローカル変数の数を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7081-107">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7081-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="b7081-108">Return Value</span></span>  

 <span data-ttu-id="b7081-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7081-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7081-110">要件</span><span class="sxs-lookup"><span data-stu-id="b7081-110">Requirements</span></span>  

 <span data-ttu-id="b7081-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="b7081-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7081-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7081-112">See also</span></span>

- [<span data-ttu-id="b7081-113">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7081-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
