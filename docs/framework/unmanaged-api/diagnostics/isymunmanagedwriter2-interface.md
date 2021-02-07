---
description: 詳細については、「ISymUnmanagedWriter2 インターフェイス」を参照してください。
title: ISymUnmanagedWriter2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 228bae40e12376b3b5e8ca3bbd3463ba70a6d67b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761779"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="5d8fe-103">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d8fe-103">ISymUnmanagedWriter2 Interface</span></span>

<span data-ttu-id="5d8fe-104">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d8fe-104">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="5d8fe-105">このインターフェイスは、 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="5d8fe-105">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d8fe-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5d8fe-106">Methods</span></span>  
  
|<span data-ttu-id="5d8fe-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="5d8fe-107">Method</span></span>|<span data-ttu-id="5d8fe-108">説明</span><span class="sxs-lookup"><span data-stu-id="5d8fe-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d8fe-109">DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="5d8fe-109">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="5d8fe-110">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="5d8fe-110">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="5d8fe-111">DefineGlobalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="5d8fe-111">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="5d8fe-112">グローバル変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="5d8fe-112">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="5d8fe-113">DefineLocalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="5d8fe-113">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="5d8fe-114">現在の構文のスコープの変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="5d8fe-114">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d8fe-115">要件</span><span class="sxs-lookup"><span data-stu-id="5d8fe-115">Requirements</span></span>  

 <span data-ttu-id="5d8fe-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="5d8fe-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d8fe-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d8fe-117">See also</span></span>

- [<span data-ttu-id="5d8fe-118">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d8fe-118">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="5d8fe-119">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d8fe-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="5d8fe-120">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d8fe-120">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
