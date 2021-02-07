---
description: 詳細については、「ISymUnmanagedScope インターフェイス」を参照してください。
title: ISymUnmanagedScope インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: f1175656fb49ee16fd1cd676d08f6ebb76f40c6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763268"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="5ecc1-103">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ecc1-103">ISymUnmanagedScope Interface</span></span>

<span data-ttu-id="5ecc1-104">メソッド内の構文のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="5ecc1-104">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ecc1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-105">Methods</span></span>  
  
|<span data-ttu-id="5ecc1-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-106">Method</span></span>|<span data-ttu-id="5ecc1-107">説明</span><span class="sxs-lookup"><span data-stu-id="5ecc1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ecc1-108">GetChildren メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-108">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="5ecc1-109">このスコープの子を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ecc1-109">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="5ecc1-110">GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-110">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="5ecc1-111">このスコープの終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ecc1-111">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="5ecc1-112">GetLocalCount メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-112">GetLocalCount Method</span></span>](isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="5ecc1-113">このスコープ内で定義されているローカル変数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ecc1-113">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="5ecc1-114">GetLocals メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-114">GetLocals Method</span></span>](isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="5ecc1-115">このスコープ内で定義されているローカル変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ecc1-115">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="5ecc1-116">GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-116">GetMethod Method</span></span>](isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="5ecc1-117">このスコープを格納しているメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ecc1-117">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="5ecc1-118">GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-118">GetNamespaces Method</span></span>](isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="5ecc1-119">このスコープ内で使用されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ecc1-119">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="5ecc1-120">GetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-120">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)|<span data-ttu-id="5ecc1-121">このスコープの親スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ecc1-121">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="5ecc1-122">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="5ecc1-122">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="5ecc1-123">このスコープの開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ecc1-123">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ecc1-124">要件</span><span class="sxs-lookup"><span data-stu-id="5ecc1-124">Requirements</span></span>  

 <span data-ttu-id="5ecc1-125">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="5ecc1-125">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ecc1-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ecc1-126">See also</span></span>

- [<span data-ttu-id="5ecc1-127">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ecc1-127">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="5ecc1-128">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ecc1-128">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
