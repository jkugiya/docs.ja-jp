---
description: 詳細については、「ISymUnmanagedMethod インターフェイス」を参照してください。
title: ISymUnmanagedMethod インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: 18f87784a959ddc62415592e51d1971ea10f90bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709959"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="e471e-103">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e471e-103">ISymUnmanagedMethod Interface</span></span>

<span data-ttu-id="e471e-104">シンボル ストア内のメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="e471e-104">Represents a method within the symbol store.</span></span> <span data-ttu-id="e471e-105">このインターフェイスは、型関連の属性ではなく、メソッドのシンボル関連の属性にのみアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="e471e-105">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e471e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-106">Methods</span></span>  
  
|<span data-ttu-id="e471e-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-107">Method</span></span>|<span data-ttu-id="e471e-108">説明</span><span class="sxs-lookup"><span data-stu-id="e471e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e471e-109">GetNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-109">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="e471e-110">このメソッドが定義されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="e471e-110">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="e471e-111">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-111">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="e471e-112">ドキュメント内の指定された位置に対応する、このメソッド内のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="e471e-112">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="e471e-113">GetParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-113">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="e471e-114">このメソッドのパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="e471e-114">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="e471e-115">GetRanges メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-115">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="e471e-116">ドキュメント内の位置が指定されている場合、は、位置がこのメソッド内でカバーする Microsoft 中間言語 (MSIL) の範囲に対応する開始オフセットと終了オフセットのペアの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="e471e-116">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="e471e-117">GetRootScope メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-117">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="e471e-118">このメソッド内のルート構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="e471e-118">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="e471e-119">このスコープはメソッド全体を囲みます。</span><span class="sxs-lookup"><span data-stu-id="e471e-119">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="e471e-120">GetScopeFromOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-120">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="e471e-121">指定されたオフセットを囲む、このメソッド内で最も外側にある構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="e471e-121">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="e471e-122">GetSequencePointCount メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-122">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="e471e-123">このメソッド内のシーケンスポイントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="e471e-123">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="e471e-124">GetSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-124">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="e471e-125">このメソッド内のすべてのシーケンスポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="e471e-125">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="e471e-126">GetSourceStartEnd メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-126">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="e471e-127">このメソッドのソースのドキュメントの開始位置と終了位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="e471e-127">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="e471e-128">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="e471e-128">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="e471e-129">このメソッドのメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="e471e-129">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e471e-130">要件</span><span class="sxs-lookup"><span data-stu-id="e471e-130">Requirements</span></span>  

 <span data-ttu-id="e471e-131">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e471e-131">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e471e-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="e471e-132">See also</span></span>

- [<span data-ttu-id="e471e-133">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e471e-133">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
