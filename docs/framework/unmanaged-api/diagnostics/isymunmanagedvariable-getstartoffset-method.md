---
description: '詳細について: ISymUnmanagedVariable:: GetStartOffset メソッド'
title: ISymUnmanagedVariable::GetStartOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
ms.openlocfilehash: 96ff27cfaf53c7a63c819b1a423e62478cf74832
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762722"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="8e47f-103">ISymUnmanagedVariable::GetStartOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="8e47f-103">ISymUnmanagedVariable::GetStartOffset Method</span></span>

<span data-ttu-id="8e47f-104">親内のこの変数の開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="8e47f-104">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="8e47f-105">スコープ内のローカル変数の場合、開始オフセットはスコープに対して定義されたオフセット内になります。</span><span class="sxs-lookup"><span data-stu-id="8e47f-105">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e47f-106">構文</span><span class="sxs-lookup"><span data-stu-id="8e47f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e47f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8e47f-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="8e47f-108">入出力開始オフセットを受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="8e47f-108">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e47f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="8e47f-109">Return Value</span></span>  

 <span data-ttu-id="8e47f-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8e47f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e47f-111">要件</span><span class="sxs-lookup"><span data-stu-id="8e47f-111">Requirements</span></span>  

 <span data-ttu-id="8e47f-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="8e47f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e47f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e47f-113">See also</span></span>

- [<span data-ttu-id="8e47f-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8e47f-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="8e47f-115">GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="8e47f-115">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)
