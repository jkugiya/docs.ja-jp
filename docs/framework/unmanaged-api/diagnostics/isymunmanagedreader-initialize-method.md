---
description: '詳細情報: ISymUnmanagedReader:: Initialize メソッド'
title: ISymUnmanagedReader::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
ms.openlocfilehash: cf7f5df3efed7823fc36bd6c9fc56e0c49d17443
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763879"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="48a19-103">ISymUnmanagedReader::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="48a19-103">ISymUnmanagedReader::Initialize Method</span></span>

<span data-ttu-id="48a19-104">このリーダーが関連付けられるメタデータインポーターインターフェイスと、モジュールのファイル名を使用して、シンボルリーダーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="48a19-104">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48a19-105">このメソッドを呼び出すことができるのは1回だけです。他のリーダーメソッドの前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="48a19-105">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48a19-106">構文</span><span class="sxs-lookup"><span data-stu-id="48a19-106">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48a19-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48a19-107">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="48a19-108">からこのリーダーが関連付けられるメタデータインポーターインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="48a19-108">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="48a19-109">からモジュールのファイル名。</span><span class="sxs-lookup"><span data-stu-id="48a19-109">[in] The file name of the module.</span></span> <span data-ttu-id="48a19-110">代わりに、パラメーターを使用でき `pIStream` ます。</span><span class="sxs-lookup"><span data-stu-id="48a19-110">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="48a19-111">から検索するパス。</span><span class="sxs-lookup"><span data-stu-id="48a19-111">[in] The path to search.</span></span> <span data-ttu-id="48a19-112">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="48a19-112">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="48a19-113">からファイルストリーム。 filename パラメーターの代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="48a19-113">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48a19-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="48a19-114">Return Value</span></span>  

 <span data-ttu-id="48a19-115">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="48a19-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48a19-116">解説</span><span class="sxs-lookup"><span data-stu-id="48a19-116">Remarks</span></span>  

 <span data-ttu-id="48a19-117">またはパラメーターのいずれか1つだけを指定する必要があります。両方を指定すること `filename` はでき `pIStream` ません。</span><span class="sxs-lookup"><span data-stu-id="48a19-117">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="48a19-118">`searchPath` パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="48a19-118">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48a19-119">要件</span><span class="sxs-lookup"><span data-stu-id="48a19-119">Requirements</span></span>  

 <span data-ttu-id="48a19-120">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="48a19-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a19-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="48a19-121">See also</span></span>

- [<span data-ttu-id="48a19-122">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48a19-122">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
