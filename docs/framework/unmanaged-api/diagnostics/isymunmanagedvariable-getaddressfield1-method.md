---
description: '詳細について: ISymUnmanagedVariable:: GetAddressField1 メソッド'
title: ISymUnmanagedVariable::GetAddressField1 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
ms.openlocfilehash: 1ff6862cef52ef8fcb449563198c2df1de356530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762995"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="a392e-103">ISymUnmanagedVariable::GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="a392e-103">ISymUnmanagedVariable::GetAddressField1 Method</span></span>

<span data-ttu-id="a392e-104">この変数の最初のアドレスフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="a392e-104">Gets the first address field for this variable.</span></span> <span data-ttu-id="a392e-105">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a392e-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a392e-106">構文</span><span class="sxs-lookup"><span data-stu-id="a392e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a392e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a392e-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="a392e-108">入出力最初のアドレスフィールドを受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="a392e-108">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a392e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="a392e-109">Return Value</span></span>  

 <span data-ttu-id="a392e-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a392e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a392e-111">要件</span><span class="sxs-lookup"><span data-stu-id="a392e-111">Requirements</span></span>  

 <span data-ttu-id="a392e-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a392e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a392e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a392e-113">See also</span></span>

- [<span data-ttu-id="a392e-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a392e-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="a392e-115">GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="a392e-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="a392e-116">GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="a392e-116">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="a392e-117">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="a392e-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
