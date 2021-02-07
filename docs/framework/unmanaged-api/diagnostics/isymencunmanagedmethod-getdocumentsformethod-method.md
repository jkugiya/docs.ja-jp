---
description: '詳細については、次を参照してください: ISymENCUnmanagedMethod:: Getドキュメント Formethod メソッド'
title: ISymENCUnmanagedMethod::GetDocumentsForMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
ms.openlocfilehash: 01c7280abe437266618d96c6e195e61a4f830131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721542"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="7dea9-103">ISymENCUnmanagedMethod::GetDocumentsForMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="7dea9-103">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>

<span data-ttu-id="7dea9-104">このメソッドに行が含まれているドキュメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="7dea9-104">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dea9-105">構文</span><span class="sxs-lookup"><span data-stu-id="7dea9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dea9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7dea9-106">Parameters</span></span>  

 `cDocs`  
 <span data-ttu-id="7dea9-107">からが指すバッファーの長さ `pcDocs` 。</span><span class="sxs-lookup"><span data-stu-id="7dea9-107">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="7dea9-108">入出力 `ULONG32` ドキュメントを格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7dea9-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="7dea9-109">からドキュメントを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="7dea9-109">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dea9-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="7dea9-110">Return Value</span></span>  

 <span data-ttu-id="7dea9-111">メソッドが成功した場合は S_OK。それ以外の場合は、エラーコード。</span><span class="sxs-lookup"><span data-stu-id="7dea9-111">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dea9-112">要件</span><span class="sxs-lookup"><span data-stu-id="7dea9-112">Requirements</span></span>  

 <span data-ttu-id="7dea9-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="7dea9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dea9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7dea9-114">See also</span></span>

- [<span data-ttu-id="7dea9-115">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dea9-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
