---
description: '詳細について: ISymUnmanagedBinder:: GetReaderFromStream メソッド'
title: ISymUnmanagedBinder::GetReaderFromStream メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: da238ed8e450250be427ae27c4492c1e091f7997
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689990"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="332a9-103">ISymUnmanagedBinder::GetReaderFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="332a9-103">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>

<span data-ttu-id="332a9-104">メタデータインターフェイスと、シンボルストアを含むストリームが指定された場合、は、指定されたシンボルストアからデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) 構造体を返します。</span><span class="sxs-lookup"><span data-stu-id="332a9-104">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="332a9-105">構文</span><span class="sxs-lookup"><span data-stu-id="332a9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="332a9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="332a9-106">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="332a9-107">からメタデータインポートインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="332a9-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="332a9-108">からシンボルストアが格納されているストリームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="332a9-108">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="332a9-109">入出力返された [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="332a9-109">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="332a9-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="332a9-110">Return Value</span></span>  

 <span data-ttu-id="332a9-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="332a9-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="332a9-112">要件</span><span class="sxs-lookup"><span data-stu-id="332a9-112">Requirements</span></span>  

 <span data-ttu-id="332a9-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="332a9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="332a9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="332a9-114">See also</span></span>

- [<span data-ttu-id="332a9-115">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="332a9-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
