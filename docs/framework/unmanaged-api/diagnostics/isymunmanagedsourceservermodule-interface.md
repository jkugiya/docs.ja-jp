---
description: 詳細については、「ISymUnmanagedSourceServerModule インターフェイス」を参照してください。
title: ISymUnmanagedSourceServerModule インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule
helpviewer_keywords:
- ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type:
- apiref
ms.openlocfilehash: c837af4cda443ec93bfbaa2d73feeb2b8f8a2803
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763125"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="3d3de-103">ISymUnmanagedSourceServerModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d3de-103">ISymUnmanagedSourceServerModule Interface</span></span>

<span data-ttu-id="3d3de-104">モジュールのソースサーバーデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="3d3de-104">Provides source server data for a module.</span></span> <span data-ttu-id="3d3de-105">このインターフェイスを取得するには `QueryInterface` 、 [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスを実装するオブジェクトに対してを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3d3de-105">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3d3de-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3d3de-106">Methods</span></span>  
  
|<span data-ttu-id="3d3de-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="3d3de-107">Method</span></span>|<span data-ttu-id="3d3de-108">説明</span><span class="sxs-lookup"><span data-stu-id="3d3de-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3d3de-109">GetSourceServerData メソッド</span><span class="sxs-lookup"><span data-stu-id="3d3de-109">GetSourceServerData Method</span></span>](isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="3d3de-110">モジュールのソースサーバーデータを返します。</span><span class="sxs-lookup"><span data-stu-id="3d3de-110">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d3de-111">要件</span><span class="sxs-lookup"><span data-stu-id="3d3de-111">Requirements</span></span>  

 <span data-ttu-id="3d3de-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="3d3de-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3de-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d3de-113">See also</span></span>

- [<span data-ttu-id="3d3de-114">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d3de-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
