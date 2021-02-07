---
description: '詳細情報: NOTIFY_FILTER 列挙型'
title: NOTIFY_FILTER 列挙体
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
ms.openlocfilehash: 0ed09af0af302b08102b7b08fa72a2d255c5b231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761487"
---
# <a name="notify_filter-enumeration"></a><span data-ttu-id="b0897-103">NOTIFY_FILTER 列挙体</span><span class="sxs-lookup"><span data-stu-id="b0897-103">NOTIFY_FILTER Enumeration</span></span>

<span data-ttu-id="b0897-104">デバッガー関数のコールバックを識別します。</span><span class="sxs-lookup"><span data-stu-id="b0897-104">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="b0897-105">詳細については、 [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0897-105">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0897-106">構文</span><span class="sxs-lookup"><span data-stu-id="b0897-106">Syntax</span></span>  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="b0897-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b0897-107">Members</span></span>  
  
|<span data-ttu-id="b0897-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="b0897-108">Member</span></span>|<span data-ttu-id="b0897-109">説明</span><span class="sxs-lookup"><span data-stu-id="b0897-109">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="b0897-110">[INotifySink2:: OnSyncCallOut](inotifysink2-onsynccallout-method.md)メソッドを呼び出す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="b0897-110">Indicates that the [INotifySink2::OnSyncCallOut](inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="b0897-111">[INotifySink2:: OnSyncCallEnter](inotifysink2-onsynccallenter-method.md)メソッドを呼び出す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="b0897-111">Indicates that the [INotifySink2::OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="b0897-112">[INotifySink2:: OnSyncCallExit](inotifysink2-onsynccallexit-method.md)メソッドを呼び出す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="b0897-112">Indicates that the [INotifySink2::OnSyncCallExit](inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="b0897-113">[INotifySink2:: OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md)メソッドを呼び出す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="b0897-113">Indicates that the [INotifySink2::OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="b0897-114">すべての [INotifySink2](inotifysink2-interface.md) メソッドを呼び出す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="b0897-114">Indicates that all of the [INotifySink2](inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="b0897-115">既存の通知と今後の通知をすべてアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="b0897-115">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="b0897-116">通知メソッドを呼び出さないことを示します。</span><span class="sxs-lookup"><span data-stu-id="b0897-116">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0897-117">要件</span><span class="sxs-lookup"><span data-stu-id="b0897-117">Requirements</span></span>  

 <span data-ttu-id="b0897-118">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="b0897-118">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0897-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0897-119">See also</span></span>

- [<span data-ttu-id="b0897-120">シンボル ストア診断列挙型</span><span class="sxs-lookup"><span data-stu-id="b0897-120">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
