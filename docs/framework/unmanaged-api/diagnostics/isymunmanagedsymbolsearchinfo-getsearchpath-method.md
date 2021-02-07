---
description: '詳細について: ISymUnmanagedSymbolSearchInfo:: GetSearchPath メソッド'
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
ms.openlocfilehash: 2ae85733ccca8ac63fbca5d2556026221e5681bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763034"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="a4d65-103">ISymUnmanagedSymbolSearchInfo::GetSearchPath メソッド</span><span class="sxs-lookup"><span data-stu-id="a4d65-103">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>

<span data-ttu-id="a4d65-104">検索パスを取得します。</span><span class="sxs-lookup"><span data-stu-id="a4d65-104">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d65-105">構文</span><span class="sxs-lookup"><span data-stu-id="a4d65-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4d65-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4d65-106">Parameters</span></span>  

 `pcchPath`  
 <span data-ttu-id="a4d65-107">入出力 `ULONG32` 検索パスを格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a4d65-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4d65-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="a4d65-108">Return Value</span></span>  

 <span data-ttu-id="a4d65-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d65-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d65-110">要件</span><span class="sxs-lookup"><span data-stu-id="a4d65-110">Requirements</span></span>  

 <span data-ttu-id="a4d65-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a4d65-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d65-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4d65-112">See also</span></span>

- [<span data-ttu-id="a4d65-113">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4d65-113">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
