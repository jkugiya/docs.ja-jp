---
description: '詳細について: ISymUnmanagedDocument:: FindClosestLine メソッド'
title: ISymUnmanagedDocument::FindClosestLine メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
ms.openlocfilehash: 0409a5cc29bf148a49a5267d34662f763fc302d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737832"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="a831e-103">ISymUnmanagedDocument::FindClosestLine メソッド</span><span class="sxs-lookup"><span data-stu-id="a831e-103">ISymUnmanagedDocument::FindClosestLine Method</span></span>

<span data-ttu-id="a831e-104">このドキュメント内の行が指定されている場合は、シーケンスポイントで最も近い行を返します。</span><span class="sxs-lookup"><span data-stu-id="a831e-104">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a831e-105">構文</span><span class="sxs-lookup"><span data-stu-id="a831e-105">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a831e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a831e-106">Parameters</span></span>  

 `line`  
 <span data-ttu-id="a831e-107">からこのドキュメント内の行。</span><span class="sxs-lookup"><span data-stu-id="a831e-107">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a831e-108">入出力行を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a831e-108">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a831e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="a831e-109">Return Value</span></span>  

 <span data-ttu-id="a831e-110">メソッドが成功した場合は S_OK。それ以外の場合は、エラーコード。</span><span class="sxs-lookup"><span data-stu-id="a831e-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a831e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a831e-111">See also</span></span>

- [<span data-ttu-id="a831e-112">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a831e-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
