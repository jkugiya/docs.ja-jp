---
description: '詳細について: ISymUnmanagedDocument:: GetDocumentType メソッド'
title: ISymUnmanagedDocument::GetDocumentType メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetDocumentType
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type:
- apiref
ms.openlocfilehash: cf2ceffccb33eb7cba0d45af203e12d1e4244f60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710323"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="5103b-103">ISymUnmanagedDocument::GetDocumentType メソッド</span><span class="sxs-lookup"><span data-stu-id="5103b-103">ISymUnmanagedDocument::GetDocumentType Method</span></span>

<span data-ttu-id="5103b-104">このドキュメントのドキュメントの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="5103b-104">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5103b-105">構文</span><span class="sxs-lookup"><span data-stu-id="5103b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5103b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5103b-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="5103b-107">入出力ドキュメント型を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5103b-107">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5103b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="5103b-108">Return Value</span></span>  

 <span data-ttu-id="5103b-109">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="5103b-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5103b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5103b-110">See also</span></span>

- [<span data-ttu-id="5103b-111">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5103b-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
