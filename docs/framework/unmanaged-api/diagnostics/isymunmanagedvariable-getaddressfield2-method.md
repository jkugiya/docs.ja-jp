---
description: '詳細について: ISymUnmanagedVariable:: GetAddressField2 メソッド'
title: ISymUnmanagedVariable::GetAddressField2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
ms.openlocfilehash: 5d9bc226bfc462157e66b1d8fb43762945cdc016
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762969"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="e89b3-103">ISymUnmanagedVariable::GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="e89b3-103">ISymUnmanagedVariable::GetAddressField2 Method</span></span>

<span data-ttu-id="e89b3-104">この変数の2番目のアドレスフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="e89b3-104">Gets the second address field for this variable.</span></span> <span data-ttu-id="e89b3-105">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e89b3-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e89b3-106">構文</span><span class="sxs-lookup"><span data-stu-id="e89b3-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e89b3-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e89b3-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="e89b3-108">入出力 `ULONG32` 2 番目のアドレスフィールドを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e89b3-108">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e89b3-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="e89b3-109">Return Value</span></span>  

 <span data-ttu-id="e89b3-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e89b3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e89b3-111">要件</span><span class="sxs-lookup"><span data-stu-id="e89b3-111">Requirements</span></span>  

 <span data-ttu-id="e89b3-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e89b3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89b3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e89b3-113">See also</span></span>

- [<span data-ttu-id="e89b3-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e89b3-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="e89b3-115">GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="e89b3-115">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="e89b3-116">GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="e89b3-116">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="e89b3-117">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="e89b3-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
