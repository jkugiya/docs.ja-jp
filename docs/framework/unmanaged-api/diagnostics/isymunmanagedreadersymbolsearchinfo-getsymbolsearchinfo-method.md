---
description: '詳細について: ISymUnmanagedReaderSymbolSearchInfo:: Getシンボル Searchinfo メソッド'
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
ms.openlocfilehash: e14f78d6736684205b3f86150ce1fbb44a8112b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763606"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="507cf-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="507cf-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>

<span data-ttu-id="507cf-104">シンボルの検索情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="507cf-104">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="507cf-105">構文</span><span class="sxs-lookup"><span data-stu-id="507cf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="507cf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="507cf-106">Parameters</span></span>  

 `cSearchInfo`  
 <span data-ttu-id="507cf-107">から `ULONG32` のサイズを示す `rgpSearchInfo` です。</span><span class="sxs-lookup"><span data-stu-id="507cf-107">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="507cf-108">入出力 `ULONG32` 検索情報を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="507cf-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="507cf-109">入出力返された [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="507cf-109">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="507cf-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="507cf-110">Return Value</span></span>  

 <span data-ttu-id="507cf-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="507cf-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="507cf-112">要件</span><span class="sxs-lookup"><span data-stu-id="507cf-112">Requirements</span></span>  

 <span data-ttu-id="507cf-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="507cf-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="507cf-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="507cf-114">See also</span></span>

- [<span data-ttu-id="507cf-115">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="507cf-115">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
