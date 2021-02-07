---
description: '詳細情報: ISymUnmanagedConstant:: GetValue メソッド'
title: ISymUnmanagedConstant::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 05818028deb804bf2a2426285b5185b01776199d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689691"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="e2a36-103">ISymUnmanagedConstant::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="e2a36-103">ISymUnmanagedConstant::GetValue Method</span></span>

<span data-ttu-id="e2a36-104">定数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e2a36-104">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a36-105">構文</span><span class="sxs-lookup"><span data-stu-id="e2a36-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2a36-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e2a36-106">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="e2a36-107">入出力値を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e2a36-107">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2a36-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e2a36-108">Return Value</span></span>  

 <span data-ttu-id="e2a36-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e2a36-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2a36-110">要件</span><span class="sxs-lookup"><span data-stu-id="e2a36-110">Requirements</span></span>  

 <span data-ttu-id="e2a36-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e2a36-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a36-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2a36-112">See also</span></span>

- [<span data-ttu-id="e2a36-113">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e2a36-113">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="e2a36-114">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="e2a36-114">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="e2a36-115">GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="e2a36-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
