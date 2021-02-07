---
description: 詳細については、「ICLRErrorReportingManager インターフェイス」を参照してください。
title: ICLRErrorReportingManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
ms.openlocfilehash: 094fe52858983fd0e1e5826e823932cb150b6087
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689275"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="b0ee3-103">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0ee3-103">ICLRErrorReportingManager Interface</span></span>

<span data-ttu-id="b0ee3-104">エラー報告のためにホストがカスタムスタックダンプを構成できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b0ee3-104">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0ee3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b0ee3-105">Methods</span></span>  
  
|<span data-ttu-id="b0ee3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b0ee3-106">Method</span></span>|<span data-ttu-id="b0ee3-107">説明</span><span class="sxs-lookup"><span data-stu-id="b0ee3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0ee3-108">BeginCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="b0ee3-108">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="b0ee3-109">エラー報告用のカスタムスタックダンプの構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0ee3-109">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="b0ee3-110">EndCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="b0ee3-110">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="b0ee3-111">以前のの呼び出しで設定されたカスタムスタックダンプ構成を消去し `BeginCustomDump` ます。</span><span class="sxs-lookup"><span data-stu-id="b0ee3-111">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="b0ee3-112">GetBucketParametersForCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="b0ee3-112">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="b0ee3-113">呼び出し元のスレッドで現在の例外の Watson バケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="b0ee3-113">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0ee3-114">解説</span><span class="sxs-lookup"><span data-stu-id="b0ee3-114">Remarks</span></span>  

 <span data-ttu-id="b0ee3-115">メソッドは、 `BeginCustomDump` カスタムスタックダンプ構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="b0ee3-115">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="b0ee3-116">メソッドは、 `EndCustomDump` カスタムスタックダンプ構成をクリアし、関連付けられているすべての状態を解放します。</span><span class="sxs-lookup"><span data-stu-id="b0ee3-116">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="b0ee3-117">カスタムダンプの完了後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0ee3-117">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b0ee3-118">を呼び出さない `EndCustomDump` と、メモリがリークします。</span><span class="sxs-lookup"><span data-stu-id="b0ee3-118">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ee3-119">要件</span><span class="sxs-lookup"><span data-stu-id="b0ee3-119">Requirements</span></span>  

 <span data-ttu-id="b0ee3-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0ee3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ee3-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b0ee3-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0ee3-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b0ee3-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0ee3-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ee3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ee3-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0ee3-124">See also</span></span>

- [<span data-ttu-id="b0ee3-125">ECustomDumpItemKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="b0ee3-125">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="b0ee3-126">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0ee3-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
