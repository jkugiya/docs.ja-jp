---
description: 詳細については、「ISymUnmanagedWriter5 インターフェイス」を参照してください。
title: ISymUnmanagedWriter5 インターフェイス
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 0902385576e1eed17cea672b04858c7e3ef7add8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761630"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="7dd20-103">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dd20-103">ISymUnmanagedWriter5 Interface</span></span>

<span data-ttu-id="7dd20-104">ISymUnmanagedWriter5 インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="7dd20-104">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd20-105">構文</span><span class="sxs-lookup"><span data-stu-id="7dd20-105">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="7dd20-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7dd20-106">Methods</span></span>  

 <span data-ttu-id="7dd20-107">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7dd20-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="7dd20-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="7dd20-108">Method</span></span>|<span data-ttu-id="7dd20-109">説明</span><span class="sxs-lookup"><span data-stu-id="7dd20-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7dd20-110">CloseMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="7dd20-110">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="7dd20-111">トークンとソースの間のマッピング情報については、特別なカスタムデータセクションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7dd20-111">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="7dd20-112">閉じた後は、マッピング情報を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="7dd20-112">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="7dd20-113">MapTokenToSourceSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="7dd20-113">MapTokenToSourceSpan Method</span></span>](isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="7dd20-114">指定されたメタデータトークンを、指定されたソースファイル内の指定されたソース行スパンにマップします。</span><span class="sxs-lookup"><span data-stu-id="7dd20-114">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="7dd20-115">[Openmaptokenstosourcespans メソッド](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)の呼び出しの間で、を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dd20-115">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="7dd20-116">OpenMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="7dd20-116">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="7dd20-117">特別なカスタムデータセクションを開き、トークンからソースまでの範囲マッピング情報をに出力します。</span><span class="sxs-lookup"><span data-stu-id="7dd20-117">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="7dd20-118">メソッドが既に開いている場合や、その逆の場合にこのセクションを開くと、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="7dd20-118">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7dd20-119">要件</span><span class="sxs-lookup"><span data-stu-id="7dd20-119">Requirements</span></span>  

 <span data-ttu-id="7dd20-120">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="7dd20-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd20-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="7dd20-121">See also</span></span>

- [<span data-ttu-id="7dd20-122">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dd20-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7dd20-123">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dd20-123">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
