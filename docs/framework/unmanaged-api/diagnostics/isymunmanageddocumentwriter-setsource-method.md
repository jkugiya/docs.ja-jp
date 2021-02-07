---
description: '詳細について: ISymUnmanagedDocumentWriter:: SetSource メソッド'
title: ISymUnmanagedDocumentWriter::SetSource メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
ms.openlocfilehash: e24e34a297a9931babf3df4f2bae1b5e8f60db1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721477"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="81299-103">ISymUnmanagedDocumentWriter::SetSource メソッド</span><span class="sxs-lookup"><span data-stu-id="81299-103">ISymUnmanagedDocumentWriter::SetSource Method</span></span>

<span data-ttu-id="81299-104">書き込まれるドキュメントの埋め込み元を設定します。</span><span class="sxs-lookup"><span data-stu-id="81299-104">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81299-105">構文</span><span class="sxs-lookup"><span data-stu-id="81299-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81299-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81299-106">Parameters</span></span>  

 `sourceSize`  
 <span data-ttu-id="81299-107">から `ULONG32` バッファーのサイズを格納している `source` 。</span><span class="sxs-lookup"><span data-stu-id="81299-107">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="81299-108">から埋め込みソースを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="81299-108">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81299-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="81299-109">Return Value</span></span>  

 <span data-ttu-id="81299-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="81299-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81299-111">要件</span><span class="sxs-lookup"><span data-stu-id="81299-111">Requirements</span></span>  

 <span data-ttu-id="81299-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="81299-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81299-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="81299-113">See also</span></span>

- [<span data-ttu-id="81299-114">ISymUnmanagedDocumentWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81299-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
