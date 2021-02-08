---
description: 詳細については、「INotifySink2 インターフェイス」を参照してください。
title: INotifySink2 インターフェイス
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
ms.openlocfilehash: 4d046c5566d9cb1641426f6a990f39449c33bc4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800293"
---
# <a name="inotifysink2-interface"></a><span data-ttu-id="b930d-103">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b930d-103">INotifySink2 Interface</span></span>

<span data-ttu-id="b930d-104">シンク通知のメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="b930d-104">Declares methods for sink notification.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b930d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b930d-105">Methods</span></span>  
  
|<span data-ttu-id="b930d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b930d-106">Method</span></span>|<span data-ttu-id="b930d-107">説明</span><span class="sxs-lookup"><span data-stu-id="b930d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b930d-108">OnSyncCallEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="b930d-108">OnSyncCallEnter Method</span></span>](inotifysink2-onsynccallenter-method.md)|<span data-ttu-id="b930d-109">呼び出しを入力したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b930d-109">Gets invoked when entering a call.</span></span>|  
|[<span data-ttu-id="b930d-110">OnSyncCallExit メソッド</span><span class="sxs-lookup"><span data-stu-id="b930d-110">OnSyncCallExit Method</span></span>](inotifysink2-onsynccallexit-method.md)|<span data-ttu-id="b930d-111">呼び出しを終了したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b930d-111">Gets invoked when exiting a call.</span></span>|  
|[<span data-ttu-id="b930d-112">OnSyncCallOut メソッド</span><span class="sxs-lookup"><span data-stu-id="b930d-112">OnSyncCallOut Method</span></span>](inotifysink2-onsynccallout-method.md)|<span data-ttu-id="b930d-113">呼び出しがタイムアウトしたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b930d-113">Gets invoked when a call is out.</span></span>|  
|[<span data-ttu-id="b930d-114">OnSyncCallReturn メソッド</span><span class="sxs-lookup"><span data-stu-id="b930d-114">OnSyncCallReturn Method</span></span>](inotifysink2-onsynccallreturn-method.md)|<span data-ttu-id="b930d-115">呼び出しから制御が戻ったときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b930d-115">Gets invoked when a call returns.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b930d-116">要件</span><span class="sxs-lookup"><span data-stu-id="b930d-116">Requirements</span></span>  

 <span data-ttu-id="b930d-117">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="b930d-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b930d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b930d-118">See also</span></span>

- [<span data-ttu-id="b930d-119">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b930d-119">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="b930d-120">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b930d-120">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="b930d-121">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b930d-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
