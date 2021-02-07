---
description: '詳細について: ISymUnmanagedScope:: GetStartOffset メソッド'
title: ISymUnmanagedScope::GetStartOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
ms.openlocfilehash: c95fbc5229512f08052ffc00f0092f64983ea3f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763320"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="0b8b1-103">ISymUnmanagedScope::GetStartOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="0b8b1-103">ISymUnmanagedScope::GetStartOffset Method</span></span>

<span data-ttu-id="0b8b1-104">このスコープの開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="0b8b1-104">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b8b1-105">構文</span><span class="sxs-lookup"><span data-stu-id="0b8b1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b8b1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b8b1-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="0b8b1-107">入出力 `ULONG32` 開始オフセットを格納しているへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0b8b1-107">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b8b1-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0b8b1-108">Return Value</span></span>  

 <span data-ttu-id="0b8b1-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0b8b1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b8b1-110">要件</span><span class="sxs-lookup"><span data-stu-id="0b8b1-110">Requirements</span></span>  

 <span data-ttu-id="0b8b1-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="0b8b1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8b1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b8b1-112">See also</span></span>

- [<span data-ttu-id="0b8b1-113">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b8b1-113">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="0b8b1-114">GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="0b8b1-114">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)
