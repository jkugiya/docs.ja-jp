---
description: '詳細情報: ISymUnmanagedAsyncMethod:: IsAsyncMethod メソッド'
title: ISymUnmanagedAsyncMethod::IsAsyncMethod メソッド
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 4b151f5367bac5fd92cc8237492cad6dacfb8e88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790257"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="c4f11-103">ISymUnmanagedAsyncMethod::IsAsyncMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="c4f11-103">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>

<span data-ttu-id="c4f11-104">メソッドに非同期情報があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c4f11-104">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="c4f11-105">このメソッドがを返す場合 `FALSE` 、このインターフェイス内の他のメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="c4f11-105">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="c4f11-106">これらはすべて、 `E_UNEXPECTED` この場合はを返します。</span><span class="sxs-lookup"><span data-stu-id="c4f11-106">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4f11-107">構文</span><span class="sxs-lookup"><span data-stu-id="c4f11-107">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4f11-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c4f11-108">Parameters</span></span>  
  
|<span data-ttu-id="c4f11-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c4f11-109">Parameter</span></span>|<span data-ttu-id="c4f11-110">説明</span><span class="sxs-lookup"><span data-stu-id="c4f11-110">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="c4f11-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="c4f11-111">Return Value</span></span>  

 <span data-ttu-id="c4f11-112">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="c4f11-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4f11-113">要件</span><span class="sxs-lookup"><span data-stu-id="c4f11-113">Requirements</span></span>  

 <span data-ttu-id="c4f11-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c4f11-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f11-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4f11-115">See also</span></span>

- [<span data-ttu-id="c4f11-116">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c4f11-116">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
