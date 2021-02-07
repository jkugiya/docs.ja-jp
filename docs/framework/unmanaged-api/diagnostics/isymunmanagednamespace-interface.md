---
description: 詳細については、「ISymUnmanagedNamespace インターフェイス」を参照してください。
title: ISymUnmanagedNamespace インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace
helpviewer_keywords:
- ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: d42bea4e-5848-4e43-a883-69af7a313ce9
topic_type:
- apiref
ms.openlocfilehash: ff2cd2286ab006411a70ff9aa32c4f0265a73995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709842"
---
# <a name="isymunmanagednamespace-interface"></a><span data-ttu-id="563cc-103">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="563cc-103">ISymUnmanagedNamespace Interface</span></span>

<span data-ttu-id="563cc-104">名前空間を表します。</span><span class="sxs-lookup"><span data-stu-id="563cc-104">Represents a namespace.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="563cc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="563cc-105">Methods</span></span>  
  
|<span data-ttu-id="563cc-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="563cc-106">Method</span></span>|<span data-ttu-id="563cc-107">説明</span><span class="sxs-lookup"><span data-stu-id="563cc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="563cc-108">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="563cc-108">GetName Method</span></span>](isymunmanagednamespace-getname-method.md)|<span data-ttu-id="563cc-109">この名前空間の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="563cc-109">Gets the name of this namespace.</span></span>|  
|[<span data-ttu-id="563cc-110">GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="563cc-110">GetNamespaces Method</span></span>](isymunmanagednamespace-getnamespaces-method.md)|<span data-ttu-id="563cc-111">この名前空間の子を取得します。</span><span class="sxs-lookup"><span data-stu-id="563cc-111">Gets the children of this namespace.</span></span>|  
|[<span data-ttu-id="563cc-112">GetVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="563cc-112">GetVariables Method</span></span>](isymunmanagednamespace-getvariables-method.md)|<span data-ttu-id="563cc-113">この名前空間内のグローバルスコープで定義されているすべての変数を返します。</span><span class="sxs-lookup"><span data-stu-id="563cc-113">Returns all variables defined at global scope within this namespace.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="563cc-114">要件</span><span class="sxs-lookup"><span data-stu-id="563cc-114">Requirements</span></span>  

 <span data-ttu-id="563cc-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="563cc-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563cc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="563cc-116">See also</span></span>

- [<span data-ttu-id="563cc-117">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="563cc-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
