---
description: '詳細について: ISymUnmanagedSymbolSearchInfo:: GetSearchPathLength メソッド'
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
ms.openlocfilehash: 3d5faf9d972881ff9c1eaf71bcaa6f68da46dae6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763021"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="f4d6b-103">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength メソッド</span><span class="sxs-lookup"><span data-stu-id="f4d6b-103">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>

<span data-ttu-id="f4d6b-104">検索パスの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="f4d6b-104">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4d6b-105">構文</span><span class="sxs-lookup"><span data-stu-id="f4d6b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4d6b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4d6b-106">Parameters</span></span>  

 `pcchPath`  
 <span data-ttu-id="f4d6b-107">入出力 `ULONG32` 検索パスの長さを格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f4d6b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4d6b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f4d6b-108">Return Value</span></span>  

 <span data-ttu-id="f4d6b-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f4d6b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4d6b-110">要件</span><span class="sxs-lookup"><span data-stu-id="f4d6b-110">Requirements</span></span>  

 <span data-ttu-id="f4d6b-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f4d6b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d6b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4d6b-112">See also</span></span>

- [<span data-ttu-id="f4d6b-113">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4d6b-113">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
