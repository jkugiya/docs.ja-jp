---
description: '詳細について: ISymUnmanagedDocument:: GetURL メソッド'
title: ISymUnmanagedDocument::GetURL メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: b39b36054d80f9ad2f9dd076e2055ccbc6526973
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710193"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="1d9cc-103">ISymUnmanagedDocument::GetURL メソッド</span><span class="sxs-lookup"><span data-stu-id="1d9cc-103">ISymUnmanagedDocument::GetURL Method</span></span>

<span data-ttu-id="1d9cc-104">このドキュメントの URL (uniform resource locator) を返します。</span><span class="sxs-lookup"><span data-stu-id="1d9cc-104">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d9cc-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d9cc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d9cc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1d9cc-106">Parameters</span></span>  

 `cchUrl`  
 <span data-ttu-id="1d9cc-107">[入力] `szURL` バッファーのサイズ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="1d9cc-107">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="1d9cc-108">入出力Null 終了を含む、URL のサイズを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1d9cc-108">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="1d9cc-109">入出力URL を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="1d9cc-109">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d9cc-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="1d9cc-110">Return Value</span></span>  

 <span data-ttu-id="1d9cc-111">メソッドが成功した場合は S_OK。それ以外の場合は、エラーコード。</span><span class="sxs-lookup"><span data-stu-id="1d9cc-111">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d9cc-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d9cc-112">See also</span></span>

- [<span data-ttu-id="1d9cc-113">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d9cc-113">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
