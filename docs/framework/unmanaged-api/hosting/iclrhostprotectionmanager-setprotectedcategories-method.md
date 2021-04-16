---
description: '詳細情報: ICLRHostProtectionManager::SetProtectedCategories メソッド'
title: ICLRHostProtectionManager::SetProtectedCategories メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: 9138c31ea1a2d9b7ebeaeac8ef5ef9305eabef8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637535"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="83dd6-103">ICLRHostProtectionManager::SetProtectedCategories メソッド</span><span class="sxs-lookup"><span data-stu-id="83dd6-103">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>

<span data-ttu-id="83dd6-104">部分的に信頼されたコードでの実行をブロックする必要があるのは、どのカテゴリのマネージド型とメンバーかを指定します。</span><span class="sxs-lookup"><span data-stu-id="83dd6-104">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83dd6-105">構文</span><span class="sxs-lookup"><span data-stu-id="83dd6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83dd6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83dd6-106">Parameters</span></span>  

 `categories`  
 <span data-ttu-id="83dd6-107">[in] [EApiCategories](eapicategories-enumeration.md) の組み合わせ。部分的に信頼されたコードでの実行をブロックする必要があるのは、どのカテゴリのマネージド型とメンバーかを示します。</span><span class="sxs-lookup"><span data-stu-id="83dd6-107">[in] A combination of [EApiCategories](eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83dd6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="83dd6-108">Return Value</span></span>  
  
|<span data-ttu-id="83dd6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83dd6-109">HRESULT</span></span>|<span data-ttu-id="83dd6-110">説明</span><span class="sxs-lookup"><span data-stu-id="83dd6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83dd6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="83dd6-111">S_OK</span></span>|<span data-ttu-id="83dd6-112">`SetProtectedCategories` が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="83dd6-112">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="83dd6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83dd6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83dd6-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージド コードを実行できないまたは呼び出しを正常に処理できない状態です。</span><span class="sxs-lookup"><span data-stu-id="83dd6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83dd6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83dd6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83dd6-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="83dd6-116">The call timed out.</span></span>|  
|<span data-ttu-id="83dd6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83dd6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83dd6-118">呼び出し元はロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="83dd6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83dd6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83dd6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83dd6-120">ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。</span><span class="sxs-lookup"><span data-stu-id="83dd6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83dd6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83dd6-121">E_FAIL</span></span>|<span data-ttu-id="83dd6-122">不明な壊滅的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="83dd6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83dd6-123">メソッドにより E_FAIL が返された後、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="83dd6-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83dd6-124">ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="83dd6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83dd6-125">解説</span><span class="sxs-lookup"><span data-stu-id="83dd6-125">Remarks</span></span>  

 <span data-ttu-id="83dd6-126">各 `EApiCategories` 値では、マネージド型とメンバーの一覧が参照されます。</span><span class="sxs-lookup"><span data-stu-id="83dd6-126">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="83dd6-127">`EApiCategories` 列挙型と `SetProtectedCategories` メソッドは、マネージド <xref:System.Security.Permissions.HostProtectionAttribute> クラスに直接関連付けられます。このクラスは、`EApiCategories` によって記述されたカテゴリに対応する機能を公開するマネージド型とメンバーをマークするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="83dd6-127">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="83dd6-128">詳細については、`EApiCategories` に直接対応する <xref:System.Security.Permissions.HostProtectionAttribute> および <xref:System.Security.Permissions.HostProtectionResource> 列挙型を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83dd6-128">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83dd6-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="83dd6-129">Requirements</span></span>  

 <span data-ttu-id="83dd6-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83dd6-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83dd6-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83dd6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83dd6-132">**ライブラリ:** リソースとして MSCorEE.dll に含まれている</span><span class="sxs-lookup"><span data-stu-id="83dd6-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83dd6-133">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83dd6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83dd6-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="83dd6-134">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="83dd6-135">EApiCategories 列挙型</span><span class="sxs-lookup"><span data-stu-id="83dd6-135">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="83dd6-136">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83dd6-136">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="83dd6-137">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83dd6-137">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
