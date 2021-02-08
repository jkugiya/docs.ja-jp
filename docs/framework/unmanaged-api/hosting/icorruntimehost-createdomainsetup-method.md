---
description: '詳細情報: ICorRuntimeHost:: CreateDomainSetup メソッド'
title: ICorRuntimeHost::CreateDomainSetup メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
ms.openlocfilehash: b7c2dc55fa9f0d3d5a5c18e38c2c825048ae5f53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789685"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="09f1f-103">ICorRuntimeHost::CreateDomainSetup メソッド</span><span class="sxs-lookup"><span data-stu-id="09f1f-103">ICorRuntimeHost::CreateDomainSetup Method</span></span>

<span data-ttu-id="09f1f-104">インスタンスへの IAppDomainSetup 型のインターフェイスポインターを取得し <xref:System.AppDomainSetup?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="09f1f-104">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="09f1f-105">`IAppDomainSetup` アプリケーションドメインを作成する前に構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="09f1f-105">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09f1f-106">構文</span><span class="sxs-lookup"><span data-stu-id="09f1f-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09f1f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="09f1f-107">Parameters</span></span>  

 `pAppDomainSetup`  
 <span data-ttu-id="09f1f-108">入出力インスタンスへのインターフェイスポインター <xref:System.AppDomainSetup?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="09f1f-108">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="09f1f-109">このパラメーターはとして型指定さ `IUnknown` れるため、通常、呼び出し元は `QueryInterface` このポインターを呼び出して、型のインターフェイスポインターを取得する必要があり `IAppDomainSetup` ます。</span><span class="sxs-lookup"><span data-stu-id="09f1f-109">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09f1f-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="09f1f-110">Return Value</span></span>  
  
|<span data-ttu-id="09f1f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09f1f-111">HRESULT</span></span>|<span data-ttu-id="09f1f-112">説明</span><span class="sxs-lookup"><span data-stu-id="09f1f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09f1f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="09f1f-113">S_OK</span></span>|<span data-ttu-id="09f1f-114">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="09f1f-114">The operation was successful.</span></span>|  
|<span data-ttu-id="09f1f-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="09f1f-115">S_FALSE</span></span>|<span data-ttu-id="09f1f-116">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="09f1f-116">The operation failed to complete.</span></span>|  
|<span data-ttu-id="09f1f-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09f1f-117">E_FAIL</span></span>|<span data-ttu-id="09f1f-118">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="09f1f-118">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="09f1f-119">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="09f1f-119">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="09f1f-120">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="09f1f-120">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="09f1f-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09f1f-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09f1f-122">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="09f1f-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09f1f-123">解説</span><span class="sxs-lookup"><span data-stu-id="09f1f-123">Remarks</span></span>  

 <span data-ttu-id="09f1f-124">このメソッドから返されるポインターは、通常、パラメーターとして [Createdomainex](icorruntimehost-createdomainex-method.md) メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="09f1f-124">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09f1f-125">要件</span><span class="sxs-lookup"><span data-stu-id="09f1f-125">Requirements</span></span>  

 <span data-ttu-id="09f1f-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09f1f-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09f1f-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="09f1f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09f1f-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="09f1f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09f1f-129">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="09f1f-129">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09f1f-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="09f1f-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="09f1f-131">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09f1f-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
