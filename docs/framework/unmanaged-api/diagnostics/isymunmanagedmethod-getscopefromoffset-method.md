---
description: '詳細について: ISymUnmanagedMethod:: GetScopeFromOffset メソッド'
title: ISymUnmanagedMethod::GetScopeFromOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: 87dd1f1732ec5d7c8669dbc2bf73b0b6128aafa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721321"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="dad6a-103">ISymUnmanagedMethod::GetScopeFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="dad6a-103">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>

<span data-ttu-id="dad6a-104">指定されたオフセットを囲む、このメソッド内で最も外側にある構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="dad6a-104">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="dad6a-105">これは、ローカル変数の検索を開始するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="dad6a-105">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dad6a-106">構文</span><span class="sxs-lookup"><span data-stu-id="dad6a-106">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dad6a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad6a-107">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="dad6a-108">から `ULONG` オフセットを格納している。</span><span class="sxs-lookup"><span data-stu-id="dad6a-108">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="dad6a-109">入出力返された [ISymUnmanagedScope](isymunmanagedscope-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="dad6a-109">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dad6a-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="dad6a-110">Return Value</span></span>  

 <span data-ttu-id="dad6a-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="dad6a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dad6a-112">要件</span><span class="sxs-lookup"><span data-stu-id="dad6a-112">Requirements</span></span>  

 <span data-ttu-id="dad6a-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="dad6a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad6a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="dad6a-114">See also</span></span>

- [<span data-ttu-id="dad6a-115">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dad6a-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
