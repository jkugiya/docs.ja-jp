---
description: 詳細については、「ISymUnmanagedReaderSymbolSearchInfo インターフェイス」を参照してください。
title: ISymUnmanagedReaderSymbolSearchInfo インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
ms.openlocfilehash: f5d13027709698df735af5fceac31f7b73741440
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763567"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="36a65-103">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36a65-103">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>

<span data-ttu-id="36a65-104">シンボル検索情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="36a65-104">Provides methods that get symbol search information.</span></span> <span data-ttu-id="36a65-105">このインターフェイスを取得するには `QueryInterface` 、 [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスを実装するオブジェクトに対してを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="36a65-105">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36a65-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="36a65-106">Methods</span></span>  
  
|<span data-ttu-id="36a65-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="36a65-107">Method</span></span>|<span data-ttu-id="36a65-108">説明</span><span class="sxs-lookup"><span data-stu-id="36a65-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36a65-109">GetSymbolSearchInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="36a65-109">GetSymbolSearchInfo Method</span></span>](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="36a65-110">シンボルの検索情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="36a65-110">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="36a65-111">GetSymbolSearchInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="36a65-111">GetSymbolSearchInfoCount Method</span></span>](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="36a65-112">シンボル検索情報の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="36a65-112">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36a65-113">要件</span><span class="sxs-lookup"><span data-stu-id="36a65-113">Requirements</span></span>  

 <span data-ttu-id="36a65-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="36a65-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a65-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="36a65-115">See also</span></span>

- [<span data-ttu-id="36a65-116">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36a65-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
