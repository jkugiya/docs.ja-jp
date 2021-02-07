---
description: '詳細について: ISymUnmanagedVariable:: GetAttributes メソッド'
title: ISymUnmanagedVariable::GetAttributes メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 0adaeaf512f129f92b7f15cdba375395a0a81855
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762839"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="1a2df-103">ISymUnmanagedVariable::GetAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="1a2df-103">ISymUnmanagedVariable::GetAttributes Method</span></span>

<span data-ttu-id="1a2df-104">この変数の属性フラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="1a2df-104">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a2df-105">構文</span><span class="sxs-lookup"><span data-stu-id="1a2df-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a2df-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1a2df-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="1a2df-107">入出力属性を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="1a2df-107">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="1a2df-108">返される値は、 [Corsymvarflag](corsymvarflag-enumeration.md) 列挙で定義されている値のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="1a2df-108">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a2df-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="1a2df-109">Return Value</span></span>  

 <span data-ttu-id="1a2df-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="1a2df-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a2df-111">要件</span><span class="sxs-lookup"><span data-stu-id="1a2df-111">Requirements</span></span>  

 <span data-ttu-id="1a2df-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="1a2df-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a2df-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a2df-113">See also</span></span>

- [<span data-ttu-id="1a2df-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a2df-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
