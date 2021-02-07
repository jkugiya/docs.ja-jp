---
description: 詳細については、「ISymUnmanagedReader2 インターフェイス」を参照してください。
title: ISymUnmanagedReader2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: 2e6d994a3252b7fb09b2915266e3142255878a88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763619"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="d3e54-103">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3e54-103">ISymUnmanagedReader2 Interface</span></span>

<span data-ttu-id="d3e54-104">シンボル ストア内のドキュメント、メソッド、および変数へのアクセスを提供するシンボル リーダーを表します。</span><span class="sxs-lookup"><span data-stu-id="d3e54-104">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="d3e54-105">このインターフェイスは、 [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="d3e54-105">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3e54-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d3e54-106">Methods</span></span>  
  
|<span data-ttu-id="d3e54-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="d3e54-107">Method</span></span>|<span data-ttu-id="d3e54-108">説明</span><span class="sxs-lookup"><span data-stu-id="d3e54-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3e54-109">GetMethodByVersionPreRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="d3e54-109">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="d3e54-110">メソッドトークンとエディットコンティニュバージョン番号を指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="d3e54-110">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="d3e54-111">GetMethodsInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="d3e54-111">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="d3e54-112">指定されたドキュメントに行情報が含まれるすべてのメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="d3e54-112">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="d3e54-113">GetSymAttributePreRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="d3e54-113">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="d3e54-114">名前に基づいてカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="d3e54-114">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3e54-115">要件</span><span class="sxs-lookup"><span data-stu-id="d3e54-115">Requirements</span></span>  

 <span data-ttu-id="d3e54-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d3e54-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e54-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3e54-117">See also</span></span>

- [<span data-ttu-id="d3e54-118">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3e54-118">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d3e54-119">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3e54-119">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
