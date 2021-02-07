---
description: '詳細情報: ISymUnmanagedDocumentWriter:: SetCheckSum メソッド'
title: ISymUnmanagedDocumentWriter::SetCheckSum メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: ac2ba9654f3610dca333cf0e06c20696cf31bd1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710089"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="f5976-103">ISymUnmanagedDocumentWriter::SetCheckSum メソッド</span><span class="sxs-lookup"><span data-stu-id="f5976-103">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>

<span data-ttu-id="f5976-104">チェックサム情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="f5976-104">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5976-105">構文</span><span class="sxs-lookup"><span data-stu-id="f5976-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5976-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5976-106">Parameters</span></span>  

 `algorithmId`  
 <span data-ttu-id="f5976-107">からアルゴリズム識別子を表す GUID。</span><span class="sxs-lookup"><span data-stu-id="f5976-107">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="f5976-108">から `ULONG32` バッファーのサイズ (バイト単位) を示す `checkSum` 。</span><span class="sxs-lookup"><span data-stu-id="f5976-108">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="f5976-109">からチェックサム情報を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="f5976-109">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5976-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="f5976-110">Return Value</span></span>  

 <span data-ttu-id="f5976-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f5976-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5976-112">要件</span><span class="sxs-lookup"><span data-stu-id="f5976-112">Requirements</span></span>  

 <span data-ttu-id="f5976-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f5976-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5976-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5976-114">See also</span></span>

- [<span data-ttu-id="f5976-115">ISymUnmanagedDocumentWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5976-115">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
