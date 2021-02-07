---
description: '詳細について: ISymUnmanagedVariable:: GetAddressField3 メソッド'
title: ISymUnmanagedVariable::GetAddressField3 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: 286d8382857e941173c22a7aebe65adc22ab779b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762917"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="16bfe-103">ISymUnmanagedVariable::GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="16bfe-103">ISymUnmanagedVariable::GetAddressField3 Method</span></span>

<span data-ttu-id="16bfe-104">この変数の3番目のアドレスフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="16bfe-104">Gets the third address field for this variable.</span></span> <span data-ttu-id="16bfe-105">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="16bfe-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16bfe-106">構文</span><span class="sxs-lookup"><span data-stu-id="16bfe-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16bfe-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16bfe-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="16bfe-108">入出力 `ULONG32` 3 番目のアドレスフィールドを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="16bfe-108">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16bfe-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="16bfe-109">Return Value</span></span>  

 <span data-ttu-id="16bfe-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="16bfe-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16bfe-111">要件</span><span class="sxs-lookup"><span data-stu-id="16bfe-111">Requirements</span></span>  

 <span data-ttu-id="16bfe-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="16bfe-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16bfe-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="16bfe-113">See also</span></span>

- [<span data-ttu-id="16bfe-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16bfe-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="16bfe-115">GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="16bfe-115">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="16bfe-116">GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="16bfe-116">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="16bfe-117">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="16bfe-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
