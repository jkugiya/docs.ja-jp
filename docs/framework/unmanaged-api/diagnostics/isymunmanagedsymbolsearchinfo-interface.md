---
description: 詳細については、「ISymUnmanagedSymbolSearchInfo インターフェイス」を参照してください。
title: ISymUnmanagedSymbolSearchInfo インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: 2f2ab198d2c54a9fcc5fa2e24b9196a38c583f81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762982"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="d66b0-103">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d66b0-103">ISymUnmanagedSymbolSearchInfo Interface</span></span>

<span data-ttu-id="d66b0-104">検索パスに関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d66b0-104">Provides methods that get information about the search path.</span></span> <span data-ttu-id="d66b0-105">このインターフェイスを取得するには `QueryInterface` 、 [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスを実装するオブジェクトに対してを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d66b0-105">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d66b0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d66b0-106">Methods</span></span>  
  
|<span data-ttu-id="d66b0-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="d66b0-107">Method</span></span>|<span data-ttu-id="d66b0-108">説明</span><span class="sxs-lookup"><span data-stu-id="d66b0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d66b0-109">GetHRESULT メソッド</span><span class="sxs-lookup"><span data-stu-id="d66b0-109">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="d66b0-110">HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="d66b0-110">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="d66b0-111">GetSearchPath メソッド</span><span class="sxs-lookup"><span data-stu-id="d66b0-111">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="d66b0-112">検索パスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d66b0-112">Gets the search path.</span></span>|  
|[<span data-ttu-id="d66b0-113">GetSearchPathLength メソッド</span><span class="sxs-lookup"><span data-stu-id="d66b0-113">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="d66b0-114">検索パスの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="d66b0-114">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d66b0-115">要件</span><span class="sxs-lookup"><span data-stu-id="d66b0-115">Requirements</span></span>  

 <span data-ttu-id="d66b0-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d66b0-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66b0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d66b0-117">See also</span></span>

- [<span data-ttu-id="d66b0-118">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d66b0-118">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
