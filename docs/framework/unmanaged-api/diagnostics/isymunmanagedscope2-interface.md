---
description: 詳細については、「ISymUnmanagedScope2 インターフェイス」を参照してください。
title: ISymUnmanagedScope2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: a15094da68b00dbec454b2f6a642ac333f9a34ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763151"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="9499f-103">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9499f-103">ISymUnmanagedScope2 Interface</span></span>

<span data-ttu-id="9499f-104">メソッド内の構文のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="9499f-104">Represents a lexical scope within a method.</span></span> <span data-ttu-id="9499f-105">このインターフェイスは、スコープ内で定義された定数に関する情報を取得するメソッドを使用して、 [ISymUnmanagedScope](isymunmanagedscope-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="9499f-105">This interface extends the [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9499f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9499f-106">Methods</span></span>  
  
|<span data-ttu-id="9499f-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="9499f-107">Method</span></span>|<span data-ttu-id="9499f-108">説明</span><span class="sxs-lookup"><span data-stu-id="9499f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9499f-109">GetConstantCount メソッド</span><span class="sxs-lookup"><span data-stu-id="9499f-109">GetConstantCount Method</span></span>](isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="9499f-110">このスコープ内で定義されている定数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="9499f-110">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="9499f-111">GetConstants メソッド</span><span class="sxs-lookup"><span data-stu-id="9499f-111">GetConstants Method</span></span>](isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="9499f-112">このスコープ内で定義されているローカル定数を取得します。</span><span class="sxs-lookup"><span data-stu-id="9499f-112">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9499f-113">要件</span><span class="sxs-lookup"><span data-stu-id="9499f-113">Requirements</span></span>  

 <span data-ttu-id="9499f-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="9499f-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9499f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9499f-115">See also</span></span>

- [<span data-ttu-id="9499f-116">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9499f-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="9499f-117">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9499f-117">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
