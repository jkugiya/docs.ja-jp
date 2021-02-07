---
description: '詳細について: ISymUnmanagedWriter5:: OpenMapTokensToSourceSpans メソッド'
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans メソッド
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 1feeecaf943e3eed228ced2b0c968f3fe4b49f62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761513"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="b1472-103">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="b1472-103">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="b1472-104">特別なカスタムデータセクションを開き、トークンからソースまでの範囲マッピング情報をに出力します。</span><span class="sxs-lookup"><span data-stu-id="b1472-104">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="b1472-105">メソッドが既に開いている場合や、その逆の場合にこのセクションを開くと、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="b1472-105">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1472-106">構文</span><span class="sxs-lookup"><span data-stu-id="b1472-106">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b1472-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="b1472-107">Return Value</span></span>  

 <span data-ttu-id="b1472-108">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="b1472-108">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1472-109">要件</span><span class="sxs-lookup"><span data-stu-id="b1472-109">Requirements</span></span>  

 <span data-ttu-id="b1472-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="b1472-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1472-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1472-111">See also</span></span>

- [<span data-ttu-id="b1472-112">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1472-112">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
