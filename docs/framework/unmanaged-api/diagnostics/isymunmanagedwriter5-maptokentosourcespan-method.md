---
description: '詳細については、次を参照してください: ISymUnmanagedWriter5:: MapTokenToSourceSpan メソッド'
title: ISymUnmanagedWriter5::MapTokenToSourceSpan メソッド
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: b30d8051f5d2872488639ce999cccd4248af367f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761617"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="c307a-103">ISymUnmanagedWriter5::MapTokenToSourceSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="c307a-103">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>

<span data-ttu-id="c307a-104">指定されたメタデータトークンを、指定されたソースファイル内の指定されたソース行スパンにマップします。</span><span class="sxs-lookup"><span data-stu-id="c307a-104">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="c307a-105">[Openmaptokenstosourcespans メソッド](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)の呼び出しの間で、を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c307a-105">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c307a-106">構文</span><span class="sxs-lookup"><span data-stu-id="c307a-106">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c307a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c307a-107">Parameters</span></span>  
  
|<span data-ttu-id="c307a-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c307a-108">Parameter</span></span>|<span data-ttu-id="c307a-109">説明</span><span class="sxs-lookup"><span data-stu-id="c307a-109">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="c307a-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="c307a-110">Return Value</span></span>  

 <span data-ttu-id="c307a-111">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="c307a-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c307a-112">要件</span><span class="sxs-lookup"><span data-stu-id="c307a-112">Requirements</span></span>  

 <span data-ttu-id="c307a-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c307a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c307a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c307a-114">See also</span></span>

- [<span data-ttu-id="c307a-115">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c307a-115">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
