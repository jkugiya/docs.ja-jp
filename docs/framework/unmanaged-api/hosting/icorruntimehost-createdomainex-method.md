---
description: '詳細について: ICorRuntimeHost:: CreateDomainEx メソッド'
title: ICorRuntimeHost::CreateDomainEx メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
ms.openlocfilehash: aec759cec4fd68fff4bdfaaf3403a0da026fb9ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789698"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="9cf65-103">ICorRuntimeHost::CreateDomainEx メソッド</span><span class="sxs-lookup"><span data-stu-id="9cf65-103">ICorRuntimeHost::CreateDomainEx Method</span></span>

<span data-ttu-id="9cf65-104">アプリケーションドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="9cf65-104">Creates an application domain.</span></span> <span data-ttu-id="9cf65-105">呼び出し元は、型のインターフェイスポインターを <xref:System._AppDomain> 型のインスタンスに受信し <xref:System.AppDomain?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="9cf65-105">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9cf65-106">このメソッドを使用すると、呼び出し元は IAppDomainSetup インスタンスを渡して、返されたインスタンスの追加の機能を構成でき <xref:System._AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="9cf65-106">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cf65-107">構文</span><span class="sxs-lookup"><span data-stu-id="9cf65-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cf65-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9cf65-108">Parameters</span></span>  

 `pwzFriendlyName`  
 <span data-ttu-id="9cf65-109">からドメインのフレンドリ名を指定するために使用される省略可能なパラメーター。</span><span class="sxs-lookup"><span data-stu-id="9cf65-109">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="9cf65-110">このフレンドリ名は、ドメインを識別するためのデバッガーなどのユーザーインターフェイスに表示できます。</span><span class="sxs-lookup"><span data-stu-id="9cf65-110">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="9cf65-111">から `IAppDomainSetup` [ICorRuntimeHost:: CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) メソッドの呼び出しによって取得される、型の省略可能なインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="9cf65-111">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="9cf65-112">から `IIdentity` アクセス許可セットを確立するためにセキュリティポリシーによってマップされた証拠を表す、インスタンスへのポインターの配列 (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="9cf65-112">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="9cf65-113">`IIdentity`オブジェクトは、 [createevidence](icorruntimehost-createevidence-method.md)メソッドを呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="9cf65-113">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="9cf65-114">入出力 <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> ドメインをさらに制御するために使用できるのインスタンスへの型のインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="9cf65-114">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cf65-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="9cf65-115">Return Value</span></span>  
  
|<span data-ttu-id="9cf65-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9cf65-116">HRESULT</span></span>|<span data-ttu-id="9cf65-117">説明</span><span class="sxs-lookup"><span data-stu-id="9cf65-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cf65-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cf65-118">S_OK</span></span>|<span data-ttu-id="9cf65-119">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="9cf65-119">The operation was successful.</span></span>|  
|<span data-ttu-id="9cf65-120">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9cf65-120">S_FALSE</span></span>|<span data-ttu-id="9cf65-121">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="9cf65-121">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9cf65-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9cf65-122">E_FAIL</span></span>|<span data-ttu-id="9cf65-123">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9cf65-123">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9cf65-124">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9cf65-124">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9cf65-125">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9cf65-125">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9cf65-126">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9cf65-126">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9cf65-127">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9cf65-127">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cf65-128">解説</span><span class="sxs-lookup"><span data-stu-id="9cf65-128">Remarks</span></span>  

 <span data-ttu-id="9cf65-129">`CreateDomainEx` は、呼び出し元がインスタンスにアプリケーションドメインを構成するためのプロパティ値を渡すことができるようにすることで、 [Createdomain](icorruntimehost-createdomain-method.md) の機能を拡張し `IAppDomainSetup` ます。</span><span class="sxs-lookup"><span data-stu-id="9cf65-129">`CreateDomainEx` extends the capabilities of [CreateDomain](icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cf65-130">要件</span><span class="sxs-lookup"><span data-stu-id="9cf65-130">Requirements</span></span>  

 <span data-ttu-id="9cf65-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cf65-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cf65-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9cf65-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cf65-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9cf65-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cf65-134">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="9cf65-134">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf65-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cf65-135">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="9cf65-136">CreateDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="9cf65-136">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="9cf65-137">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9cf65-137">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
