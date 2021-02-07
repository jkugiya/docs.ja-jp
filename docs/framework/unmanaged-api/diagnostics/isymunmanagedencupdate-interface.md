---
description: 詳細については、「ISymUnmanagedENCUpdate インターフェイス」を参照してください。
title: ISymUnmanagedENCUpdate インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: 4527dfbba840be00cf87a80cdcef3cbde6f275df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721425"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="a19a0-103">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a19a0-103">ISymUnmanagedENCUpdate Interface</span></span>

<span data-ttu-id="a19a0-104">エディットコンティニュ機能の関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="a19a0-104">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a19a0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a19a0-105">Methods</span></span>  
  
|<span data-ttu-id="a19a0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a19a0-106">Method</span></span>|<span data-ttu-id="a19a0-107">説明</span><span class="sxs-lookup"><span data-stu-id="a19a0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a19a0-108">GetLocalVariableCount メソッド</span><span class="sxs-lookup"><span data-stu-id="a19a0-108">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="a19a0-109">ローカル変数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="a19a0-109">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="a19a0-110">GetLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="a19a0-110">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="a19a0-111">ローカル変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="a19a0-111">Gets the local variables.</span></span>|  
|[<span data-ttu-id="a19a0-112">InitializeForEnc メソッド</span><span class="sxs-lookup"><span data-stu-id="a19a0-112">InitializeForEnc Method</span></span>](isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="a19a0-113">[ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md)メソッドの最初の呼び出しの前にメソッドの境界を計算できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a19a0-113">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="a19a0-114">UpdateMethodLines メソッド</span><span class="sxs-lookup"><span data-stu-id="a19a0-114">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="a19a0-115">再コンパイルされていないが、行が個別に移動したメソッドの行情報を更新できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a19a0-115">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="a19a0-116">各ステートメントのデルタが許可されます。</span><span class="sxs-lookup"><span data-stu-id="a19a0-116">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="a19a0-117">UpdateSymbolStore2 メソッド</span><span class="sxs-lookup"><span data-stu-id="a19a0-117">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="a19a0-118">行情報が要件を満たしている場合に、コンパイラがプログラムデータベース (PDB) ストリームから変更されていない関数を省略できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a19a0-118">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="a19a0-119">正しい行情報は、古い PDB 行情報と、関数内のすべての行に対して1つのデルタで判別できます。</span><span class="sxs-lookup"><span data-stu-id="a19a0-119">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a19a0-120">要件</span><span class="sxs-lookup"><span data-stu-id="a19a0-120">Requirements</span></span>  

 <span data-ttu-id="a19a0-121">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a19a0-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19a0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a19a0-122">See also</span></span>

- [<span data-ttu-id="a19a0-123">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a19a0-123">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
