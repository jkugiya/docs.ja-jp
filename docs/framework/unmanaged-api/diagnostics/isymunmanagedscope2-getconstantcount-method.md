---
description: '詳細について: ISymUnmanagedScope2:: GetConstantCount メソッド'
title: ISymUnmanagedScope2::GetConstantCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: e5b084edb116432aa43360db72ca2528dd3cc6a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763255"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="57ac0-103">ISymUnmanagedScope2::GetConstantCount メソッド</span><span class="sxs-lookup"><span data-stu-id="57ac0-103">ISymUnmanagedScope2::GetConstantCount Method</span></span>

<span data-ttu-id="57ac0-104">このスコープ内で定義されている定数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="57ac0-104">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ac0-105">構文</span><span class="sxs-lookup"><span data-stu-id="57ac0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57ac0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="57ac0-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="57ac0-107">入出力 `ULONG32` 定数を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="57ac0-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57ac0-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="57ac0-108">Return Value</span></span>  

 <span data-ttu-id="57ac0-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="57ac0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57ac0-110">要件</span><span class="sxs-lookup"><span data-stu-id="57ac0-110">Requirements</span></span>  

 <span data-ttu-id="57ac0-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="57ac0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ac0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="57ac0-112">See also</span></span>

- [<span data-ttu-id="57ac0-113">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57ac0-113">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
