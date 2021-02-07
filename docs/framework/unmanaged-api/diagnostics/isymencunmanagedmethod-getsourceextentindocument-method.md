---
description: '詳細について: ISymENCUnmanagedMethod:: GetSourceExtentInDocument メソッド'
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: 6fa9edb524a59b4420ebc737eb8d34eaf0c5c873
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737884"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="18ca6-103">ISymENCUnmanagedMethod::GetSourceExtentInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="18ca6-103">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>

<span data-ttu-id="18ca6-104">特定のドキュメント内のメソッドの最小の開始行と最大の終了行を取得します。</span><span class="sxs-lookup"><span data-stu-id="18ca6-104">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ca6-105">構文</span><span class="sxs-lookup"><span data-stu-id="18ca6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18ca6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="18ca6-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="18ca6-107">からドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="18ca6-107">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="18ca6-108">入出力開始行を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="18ca6-108">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="18ca6-109">入出力終了行を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="18ca6-109">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18ca6-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="18ca6-110">Return Value</span></span>  

 <span data-ttu-id="18ca6-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="18ca6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18ca6-112">要件</span><span class="sxs-lookup"><span data-stu-id="18ca6-112">Requirements</span></span>  

 <span data-ttu-id="18ca6-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="18ca6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ca6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="18ca6-114">See also</span></span>

- [<span data-ttu-id="18ca6-115">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18ca6-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
