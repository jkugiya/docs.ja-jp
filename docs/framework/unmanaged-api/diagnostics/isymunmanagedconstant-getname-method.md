---
description: '詳細情報: ISymUnmanagedConstant:: GetName メソッド'
title: ISymUnmanagedConstant::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 57531711ed60c9e35e749a3cb1f1ba5d5c48ca66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689821"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="bcea9-103">ISymUnmanagedConstant::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="bcea9-103">ISymUnmanagedConstant::GetName Method</span></span>

<span data-ttu-id="bcea9-104">定数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="bcea9-104">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcea9-105">構文</span><span class="sxs-lookup"><span data-stu-id="bcea9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcea9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bcea9-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="bcea9-107">からパラメーターが指すバッファーの長さ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="bcea9-107">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bcea9-108">入出力 `ULONG32` Null 終了を含む、名前を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bcea9-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="bcea9-109">入出力名前を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="bcea9-109">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bcea9-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="bcea9-110">Return Value</span></span>  

 <span data-ttu-id="bcea9-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcea9-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcea9-112">要件</span><span class="sxs-lookup"><span data-stu-id="bcea9-112">Requirements</span></span>  

 <span data-ttu-id="bcea9-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="bcea9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcea9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcea9-114">See also</span></span>

- [<span data-ttu-id="bcea9-115">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bcea9-115">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="bcea9-116">GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="bcea9-116">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="bcea9-117">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="bcea9-117">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
