---
description: '詳細について: ISymUnmanagedReaderSymbolSearchInfo:: Getシンボル Searchinfocount メソッド'
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
ms.openlocfilehash: b8bfa61397850c3f960fe30c0136e0a8b074cf1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763593"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="4ad0b-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="4ad0b-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>

<span data-ttu-id="4ad0b-104">シンボル検索情報の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-104">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad0b-105">構文</span><span class="sxs-lookup"><span data-stu-id="4ad0b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ad0b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4ad0b-106">Parameters</span></span>  

 `pcSearchInfo`  
 <span data-ttu-id="4ad0b-107">] out] `ULONG32` 検索情報を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-107">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ad0b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4ad0b-108">Return Value</span></span>  

 <span data-ttu-id="4ad0b-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ad0b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ad0b-110">要件</span><span class="sxs-lookup"><span data-stu-id="4ad0b-110">Requirements</span></span>  

 <span data-ttu-id="4ad0b-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="4ad0b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad0b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ad0b-112">See also</span></span>

- [<span data-ttu-id="4ad0b-113">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ad0b-113">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
