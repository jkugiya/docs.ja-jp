---
description: '詳細について: ISymUnmanagedDispose::D estroy メソッド'
title: ISymUnmanagedDispose::Destroy メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
ms.openlocfilehash: 3c13f90e08f2ba0dd7c70acc3321913b14195f1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790205"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="f844f-103">ISymUnmanagedDispose::Destroy メソッド</span><span class="sxs-lookup"><span data-stu-id="f844f-103">ISymUnmanagedDispose::Destroy Method</span></span>

<span data-ttu-id="f844f-104">基になるオブジェクトがすべての内部参照を解放し、後続のメソッド呼び出しの失敗を返します。</span><span class="sxs-lookup"><span data-stu-id="f844f-104">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f844f-105">構文</span><span class="sxs-lookup"><span data-stu-id="f844f-105">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f844f-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="f844f-106">Return Value</span></span>  

 <span data-ttu-id="f844f-107">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f844f-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f844f-108">要件</span><span class="sxs-lookup"><span data-stu-id="f844f-108">Requirements</span></span>  

 <span data-ttu-id="f844f-109">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f844f-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f844f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="f844f-110">See also</span></span>

- [<span data-ttu-id="f844f-111">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f844f-111">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)
