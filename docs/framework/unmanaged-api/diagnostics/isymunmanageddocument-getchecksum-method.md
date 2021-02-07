---
description: '詳細情報: ISymUnmanagedDocument:: GetCheckSum メソッド'
title: ISymUnmanagedDocument::GetCheckSum メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 9f9a42e58b22661a2233fcb457b9b42b0d6a3d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737689"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="f43d9-103">ISymUnmanagedDocument::GetCheckSum メソッド</span><span class="sxs-lookup"><span data-stu-id="f43d9-103">ISymUnmanagedDocument::GetCheckSum Method</span></span>

<span data-ttu-id="f43d9-104">チェックサムを取得します。</span><span class="sxs-lookup"><span data-stu-id="f43d9-104">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f43d9-105">構文</span><span class="sxs-lookup"><span data-stu-id="f43d9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f43d9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f43d9-106">Parameters</span></span>  

 `cData`  
 <span data-ttu-id="f43d9-107">からパラメーターによって指定されたバッファーの長さ `data`</span><span class="sxs-lookup"><span data-stu-id="f43d9-107">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="f43d9-108">入出力チェックサムのサイズと長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="f43d9-108">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="f43d9-109">入出力チェックサムを受け取るバッファー。</span><span class="sxs-lookup"><span data-stu-id="f43d9-109">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f43d9-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="f43d9-110">Return Value</span></span>  

 <span data-ttu-id="f43d9-111">メソッドが成功した場合は S_OK。それ以外の場合は、エラーコード。</span><span class="sxs-lookup"><span data-stu-id="f43d9-111">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43d9-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f43d9-112">See also</span></span>

- [<span data-ttu-id="f43d9-113">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f43d9-113">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
