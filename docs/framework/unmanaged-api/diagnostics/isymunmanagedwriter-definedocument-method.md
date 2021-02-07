---
description: '詳細については、次を参照してください: ISymUnmanagedWriter::D efineDocument メソッド'
title: ISymUnmanagedWriter::DefineDocument メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: 35e918292e6ee50e17932645e003d19513e2397a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762540"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="a3ac7-103">ISymUnmanagedWriter::DefineDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="a3ac7-103">ISymUnmanagedWriter::DefineDocument Method</span></span>

<span data-ttu-id="a3ac7-104">ソース ドキュメントを定義します。</span><span class="sxs-lookup"><span data-stu-id="a3ac7-104">Defines a source document.</span></span> <span data-ttu-id="a3ac7-105">Guid は、既知の言語、ベンダー、およびドキュメントの種類に対して提供されます。</span><span class="sxs-lookup"><span data-stu-id="a3ac7-105">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ac7-106">構文</span><span class="sxs-lookup"><span data-stu-id="a3ac7-106">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3ac7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a3ac7-107">Parameters</span></span>  

 `url`  
 <span data-ttu-id="a3ac7-108">から `WCHAR` ドキュメントを識別する URL (uniform resource locator) を定義するへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a3ac7-108">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="a3ac7-109">からドキュメントの言語を定義する GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a3ac7-109">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="a3ac7-110">からドキュメント言語のベンダの id を定義する GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a3ac7-110">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="a3ac7-111">からドキュメントの種類を定義する GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a3ac7-111">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a3ac7-112">入出力返された [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a3ac7-112">[out] A pointer to the returned [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3ac7-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="a3ac7-113">Return Value</span></span>  

 <span data-ttu-id="a3ac7-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a3ac7-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3ac7-115">要件</span><span class="sxs-lookup"><span data-stu-id="a3ac7-115">Requirements</span></span>  

 <span data-ttu-id="a3ac7-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a3ac7-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ac7-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3ac7-117">See also</span></span>

- [<span data-ttu-id="a3ac7-118">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3ac7-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
