---
description: '詳細について: ICLRDomainManager:: SetPropertiesForDefaultAppDomain メソッド'
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
ms.openlocfilehash: 08e6c885d5d089fa22c30a4e3cef69480b840031
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689444"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="4ef87-103">ICLRDomainManager::SetPropertiesForDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="4ef87-103">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>

<span data-ttu-id="4ef87-104">既定のアプリケーションドメインを初期化するために使用されるプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4ef87-104">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ef87-105">構文</span><span class="sxs-lookup"><span data-stu-id="4ef87-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ef87-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4ef87-106">Parameters</span></span>  

 `nProperties`  
 <span data-ttu-id="4ef87-107">からとのエントリの数 `pwszPropertyNames` `pwszPropertyValues` 。</span><span class="sxs-lookup"><span data-stu-id="4ef87-107">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="4ef87-108">からプロパティ名の配列。プロパティがない場合は null。</span><span class="sxs-lookup"><span data-stu-id="4ef87-108">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="4ef87-109">現時点では、このメソッドによって認識される唯一のプロパティ名は "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" です。</span><span class="sxs-lookup"><span data-stu-id="4ef87-109">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="4ef87-110">からプロパティ値の配列。プロパティがない場合は null。</span><span class="sxs-lookup"><span data-stu-id="4ef87-110">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ef87-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="4ef87-111">Return Value</span></span>  

 <span data-ttu-id="4ef87-112">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="4ef87-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4ef87-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ef87-113">HRESULT</span></span>|<span data-ttu-id="4ef87-114">説明</span><span class="sxs-lookup"><span data-stu-id="4ef87-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ef87-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ef87-115">S_OK</span></span>|<span data-ttu-id="4ef87-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="4ef87-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="4ef87-117">HRESULT_FROM_WIN32 (ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="4ef87-117">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="4ef87-118">`pwszPropertyNames` には、このメソッドで認識されないプロパティ名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4ef87-118">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ef87-119">解説</span><span class="sxs-lookup"><span data-stu-id="4ef87-119">Remarks</span></span>  

 <span data-ttu-id="4ef87-120">"PARTIAL_TRUST_VISIBLE_ASSEMBLIES" のプロパティ値は、条件付き (APTCA) 属性を持つアセンブリのリストです。このフラグは、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> 既定のアプリケーションドメインの部分的に信頼された呼び出し元に対して表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ef87-120">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ef87-121">要件</span><span class="sxs-lookup"><span data-stu-id="4ef87-121">Requirements</span></span>  

 <span data-ttu-id="4ef87-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ef87-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ef87-123">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="4ef87-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4ef87-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4ef87-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ef87-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ef87-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef87-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ef87-126">See also</span></span>

- [<span data-ttu-id="4ef87-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="4ef87-127">Hosting</span></span>](index.md)
- [<span data-ttu-id="4ef87-128">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ef87-128">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
