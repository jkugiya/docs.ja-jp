---
description: '詳細について: ISymUnmanagedSymbolSearchInfo:: GetHRESULT メソッド'
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
ms.openlocfilehash: 5d351d84ba4e91ccb9acb531e77407a2d1caceec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763112"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="22285-103">ISymUnmanagedSymbolSearchInfo::GetHRESULT メソッド</span><span class="sxs-lookup"><span data-stu-id="22285-103">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>

<span data-ttu-id="22285-104">HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="22285-104">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22285-105">構文</span><span class="sxs-lookup"><span data-stu-id="22285-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22285-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="22285-106">Parameters</span></span>  

 `phr`  
 <span data-ttu-id="22285-107">入出力HRESULT へのポインター。</span><span class="sxs-lookup"><span data-stu-id="22285-107">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22285-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="22285-108">Return Value</span></span>  

 <span data-ttu-id="22285-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="22285-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22285-110">要件</span><span class="sxs-lookup"><span data-stu-id="22285-110">Requirements</span></span>  

 <span data-ttu-id="22285-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="22285-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22285-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="22285-112">See also</span></span>

- [<span data-ttu-id="22285-113">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22285-113">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
