---
description: '詳細について: ISymUnmanagedReader:: GetDocumentVersion メソッド'
title: ISymUnmanagedReader::GetDocumentVersion メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: e6877a10f0c285186330b320c9b614939f4d9e3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800202"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="12106-103">ISymUnmanagedReader::GetDocumentVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="12106-103">ISymUnmanagedReader::GetDocumentVersion Method</span></span>

<span data-ttu-id="12106-104">指定したドキュメントの指定したバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="12106-104">Gets the specified version of the specified document.</span></span> <span data-ttu-id="12106-105">ドキュメントのバージョンは1から始まり、更新される [たびに増分](isymunmanagedreader-updatesymbolstore-method.md) されます。</span><span class="sxs-lookup"><span data-stu-id="12106-105">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="12106-106">パラメーターがの場合は、 `pbCurrent` `true` ドキュメントの最新バージョンです。</span><span class="sxs-lookup"><span data-stu-id="12106-106">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12106-107">構文</span><span class="sxs-lookup"><span data-stu-id="12106-107">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12106-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12106-108">Parameters</span></span>  

 `pDoc`  
 <span data-ttu-id="12106-109">から指定されたドキュメント。</span><span class="sxs-lookup"><span data-stu-id="12106-109">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="12106-110">入出力指定されたドキュメントのバージョンを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="12106-110">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="12106-111">入出力 `true` このがドキュメントの最新バージョンであるかどうか、または最新バージョンでない場合はを受け取る変数へのポインター `false` 。</span><span class="sxs-lookup"><span data-stu-id="12106-111">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12106-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="12106-112">Return Value</span></span>  

 <span data-ttu-id="12106-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="12106-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12106-114">要件</span><span class="sxs-lookup"><span data-stu-id="12106-114">Requirements</span></span>  

 <span data-ttu-id="12106-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="12106-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12106-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="12106-116">See also</span></span>

- [<span data-ttu-id="12106-117">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12106-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
