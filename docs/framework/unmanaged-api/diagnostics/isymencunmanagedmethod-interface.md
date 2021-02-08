---
description: 詳細については、「ISymENCUnmanagedMethod インターフェイス」を参照してください。
title: ISymENCUnmanagedMethod インターフェイス
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: 59dd56c20279b2507fc4432182d0abb5b3e9c289
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790322"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="08801-103">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08801-103">ISymENCUnmanagedMethod Interface</span></span>

<span data-ttu-id="08801-104">エディットコンティニュ機能に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="08801-104">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08801-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="08801-105">Methods</span></span>  
  
|<span data-ttu-id="08801-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="08801-106">Method</span></span>|<span data-ttu-id="08801-107">説明</span><span class="sxs-lookup"><span data-stu-id="08801-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08801-108">GetDocumentsForMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="08801-108">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="08801-109">このメソッドに行が含まれているドキュメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="08801-109">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="08801-110">GetDocumentsForMethodCount メソッド</span><span class="sxs-lookup"><span data-stu-id="08801-110">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="08801-111">このメソッドに行があるドキュメントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="08801-111">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="08801-112">GetFileNameFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="08801-112">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="08801-113">オフセットに関連付けられた行のファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="08801-113">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="08801-114">GetLineFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="08801-114">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="08801-115">オフセットに関連付けられている行情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="08801-115">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="08801-116">GetSourceExtentInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="08801-116">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="08801-117">特定のドキュメント内のメソッドの最小の開始行と最大の終了行を取得します。</span><span class="sxs-lookup"><span data-stu-id="08801-117">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08801-118">要件</span><span class="sxs-lookup"><span data-stu-id="08801-118">Requirements</span></span>  

 <span data-ttu-id="08801-119">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="08801-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08801-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="08801-120">See also</span></span>

- [<span data-ttu-id="08801-121">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08801-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
