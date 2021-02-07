---
description: 詳細については、「ISymUnmanagedWriter3 インターフェイス」を参照してください。
title: ISymUnmanagedWriter3 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: 586220af85f193b43acf0578706d9f67e3e83386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761734"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="ee79b-103">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee79b-103">ISymUnmanagedWriter3 Interface</span></span>

<span data-ttu-id="ee79b-104">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee79b-104">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="ee79b-105">このインターフェイスは、 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="ee79b-105">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee79b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ee79b-106">Methods</span></span>  
  
|<span data-ttu-id="ee79b-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="ee79b-107">Method</span></span>|<span data-ttu-id="ee79b-108">説明</span><span class="sxs-lookup"><span data-stu-id="ee79b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee79b-109">Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="ee79b-109">Commit Method</span></span>](isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="ee79b-110">これまでに書き込まれた変更をストリームにコミットします。</span><span class="sxs-lookup"><span data-stu-id="ee79b-110">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="ee79b-111">OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="ee79b-111">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="ee79b-112">メソッドを開き、イメージ内の実際のセクションオフセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee79b-112">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee79b-113">要件</span><span class="sxs-lookup"><span data-stu-id="ee79b-113">Requirements</span></span>  

 <span data-ttu-id="ee79b-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="ee79b-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee79b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee79b-115">See also</span></span>

- [<span data-ttu-id="ee79b-116">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee79b-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="ee79b-117">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee79b-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="ee79b-118">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee79b-118">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
