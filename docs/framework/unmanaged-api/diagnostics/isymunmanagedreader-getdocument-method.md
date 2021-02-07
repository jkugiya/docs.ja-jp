---
description: '詳細情報: ISymUnmanagedReader:: GetDocument メソッド'
title: ISymUnmanagedReader::GetDocument メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
ms.openlocfilehash: 7f2f31467cfd00de68737224a2c1af5b1e78efed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764100"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="6685e-103">ISymUnmanagedReader::GetDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="6685e-103">ISymUnmanagedReader::GetDocument Method</span></span>

<span data-ttu-id="6685e-104">ドキュメントを検索します。</span><span class="sxs-lookup"><span data-stu-id="6685e-104">Finds a document.</span></span> <span data-ttu-id="6685e-105">ドキュメントの言語、ベンダ、および種類はオプションです。</span><span class="sxs-lookup"><span data-stu-id="6685e-105">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6685e-106">構文</span><span class="sxs-lookup"><span data-stu-id="6685e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6685e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6685e-107">Parameters</span></span>  

 `url`  
 <span data-ttu-id="6685e-108">からドキュメントを識別する URL。</span><span class="sxs-lookup"><span data-stu-id="6685e-108">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="6685e-109">からドキュメントの言語。</span><span class="sxs-lookup"><span data-stu-id="6685e-109">[in] The document language.</span></span> <span data-ttu-id="6685e-110">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6685e-110">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="6685e-111">からドキュメント言語のベンダの id。</span><span class="sxs-lookup"><span data-stu-id="6685e-111">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="6685e-112">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6685e-112">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="6685e-113">からドキュメントの種類。</span><span class="sxs-lookup"><span data-stu-id="6685e-113">[in] The type of the document.</span></span> <span data-ttu-id="6685e-114">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6685e-114">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6685e-115">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6685e-115">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6685e-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="6685e-116">Return Value</span></span>  

 <span data-ttu-id="6685e-117">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="6685e-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6685e-118">要件</span><span class="sxs-lookup"><span data-stu-id="6685e-118">Requirements</span></span>  

 <span data-ttu-id="6685e-119">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="6685e-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6685e-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="6685e-120">See also</span></span>

- [<span data-ttu-id="6685e-121">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6685e-121">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
