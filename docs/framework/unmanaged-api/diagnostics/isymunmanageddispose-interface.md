---
description: 詳細については、「ISymUnmanagedDispose インターフェイス」を参照してください。
title: ISymUnmanagedDispose インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose
helpviewer_keywords:
- ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type:
- apiref
ms.openlocfilehash: a94a8e8e462b5031cac3f0a8702a5685f993910d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790179"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="d19fc-103">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d19fc-103">ISymUnmanagedDispose Interface</span></span>

<span data-ttu-id="d19fc-104">アンマネージリソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="d19fc-104">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d19fc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d19fc-105">Methods</span></span>  
  
|<span data-ttu-id="d19fc-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d19fc-106">Method</span></span>|<span data-ttu-id="d19fc-107">説明</span><span class="sxs-lookup"><span data-stu-id="d19fc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d19fc-108">destroy メソッド</span><span class="sxs-lookup"><span data-stu-id="d19fc-108">Destroy Method</span></span>](isymunmanageddispose-destroy-method.md)|<span data-ttu-id="d19fc-109">基になるオブジェクトがすべての内部参照を解放し、後続のメソッド呼び出しの失敗を返します。</span><span class="sxs-lookup"><span data-stu-id="d19fc-109">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d19fc-110">要件</span><span class="sxs-lookup"><span data-stu-id="d19fc-110">Requirements</span></span>  

 <span data-ttu-id="d19fc-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d19fc-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d19fc-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d19fc-112">See also</span></span>

- [<span data-ttu-id="d19fc-113">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d19fc-113">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
