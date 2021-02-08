---
description: '詳細について: ICLRHostProtectionManager:: SetEagerSerializeGrantSets メソッド'
title: ICLRHostProtectionManager::SetEagerSerializeGrantSets メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
ms.openlocfilehash: 04eb00b1422523e8057c3a0fc27dfe7e49f98f08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789914"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="347e7-103">ICLRHostProtectionManager::SetEagerSerializeGrantSets メソッド</span><span class="sxs-lookup"><span data-stu-id="347e7-103">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>

<span data-ttu-id="347e7-104">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="347e7-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="347e7-105">構文</span><span class="sxs-lookup"><span data-stu-id="347e7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="347e7-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="347e7-106">Return Value</span></span>  
  
|<span data-ttu-id="347e7-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="347e7-107">HRESULT</span></span>|<span data-ttu-id="347e7-108">説明</span><span class="sxs-lookup"><span data-stu-id="347e7-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="347e7-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="347e7-109">S_OK</span></span>|<span data-ttu-id="347e7-110">`SetEagerSerializeGrantSets` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="347e7-110">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="347e7-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="347e7-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="347e7-112">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="347e7-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="347e7-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="347e7-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="347e7-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="347e7-114">The call timed out.</span></span>|  
|<span data-ttu-id="347e7-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="347e7-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="347e7-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="347e7-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="347e7-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="347e7-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="347e7-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="347e7-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="347e7-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="347e7-119">E_FAIL</span></span>|<span data-ttu-id="347e7-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="347e7-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="347e7-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="347e7-121">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="347e7-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="347e7-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="347e7-123">要件</span><span class="sxs-lookup"><span data-stu-id="347e7-123">Requirements</span></span>  

 <span data-ttu-id="347e7-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="347e7-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="347e7-125">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="347e7-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="347e7-126">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="347e7-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="347e7-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="347e7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347e7-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="347e7-128">See also</span></span>

- [<span data-ttu-id="347e7-129">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="347e7-129">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="347e7-130">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="347e7-130">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
