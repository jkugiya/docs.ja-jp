---
description: '詳細情報: ISymUnmanagedReader:: GetDocuments メソッド'
title: ISymUnmanagedReader::GetDocuments メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
ms.openlocfilehash: 8ee2a2d8e83fcbe2f5b39960fa99e11de2ab4cd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800215"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="63f4b-103">ISymUnmanagedReader::GetDocuments メソッド</span><span class="sxs-lookup"><span data-stu-id="63f4b-103">ISymUnmanagedReader::GetDocuments Method</span></span>

<span data-ttu-id="63f4b-104">シンボルストアに定義されているすべてのドキュメントの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="63f4b-104">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f4b-105">構文</span><span class="sxs-lookup"><span data-stu-id="63f4b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63f4b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63f4b-106">Parameters</span></span>  

 `cDocs`  
 <span data-ttu-id="63f4b-107">[in] `pDocs` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="63f4b-107">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="63f4b-108">入出力配列長を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="63f4b-108">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="63f4b-109">入出力ドキュメント配列を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="63f4b-109">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63f4b-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="63f4b-110">Return Value</span></span>  

 <span data-ttu-id="63f4b-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="63f4b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63f4b-112">要件</span><span class="sxs-lookup"><span data-stu-id="63f4b-112">Requirements</span></span>  

 <span data-ttu-id="63f4b-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="63f4b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f4b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="63f4b-114">See also</span></span>

- [<span data-ttu-id="63f4b-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63f4b-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
