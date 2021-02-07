---
description: '詳細について: ISymUnmanagedVariable:: GetAddressKind メソッド'
title: ISymUnmanagedVariable::GetAddressKind メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
ms.openlocfilehash: 4b090560335432ad39157fee987ce15728fece63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762852"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="b0f5f-103">ISymUnmanagedVariable::GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="b0f5f-103">ISymUnmanagedVariable::GetAddressKind Method</span></span>

<span data-ttu-id="b0f5f-104">この変数のアドレスの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="b0f5f-104">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0f5f-105">構文</span><span class="sxs-lookup"><span data-stu-id="b0f5f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0f5f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0f5f-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="b0f5f-107">入出力値を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="b0f5f-107">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="b0f5f-108">使用可能な値は、 [Corsymaddrkind](corsymaddrkind-enumeration.md) 列挙体で定義されています。</span><span class="sxs-lookup"><span data-stu-id="b0f5f-108">The possible values are defined in the [CorSymAddrKind](corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0f5f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="b0f5f-109">Return Value</span></span>  

 <span data-ttu-id="b0f5f-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b0f5f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0f5f-111">要件</span><span class="sxs-lookup"><span data-stu-id="b0f5f-111">Requirements</span></span>  

 <span data-ttu-id="b0f5f-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="b0f5f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f5f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0f5f-113">See also</span></span>

- [<span data-ttu-id="b0f5f-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0f5f-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
