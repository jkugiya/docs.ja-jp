---
description: '詳細について: ISymUnmanagedWriter5:: CloseMapTokensToSourceSpans メソッド'
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 687a853441a4406c2eb0a9c4b3d5d59df3575e1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761656"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="ad06b-103">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="ad06b-103">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="ad06b-104">トークンとソースの間のマッピング情報については、特別なカスタムデータセクションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ad06b-104">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="ad06b-105">閉じた後は、マッピング情報を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="ad06b-105">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad06b-106">構文</span><span class="sxs-lookup"><span data-stu-id="ad06b-106">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ad06b-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad06b-107">Return Value</span></span>  

 <span data-ttu-id="ad06b-108">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="ad06b-108">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad06b-109">要件</span><span class="sxs-lookup"><span data-stu-id="ad06b-109">Requirements</span></span>  

 <span data-ttu-id="ad06b-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="ad06b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad06b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad06b-111">See also</span></span>

- [<span data-ttu-id="ad06b-112">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad06b-112">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
