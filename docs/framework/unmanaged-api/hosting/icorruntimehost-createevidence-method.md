---
description: '詳細について: ICorRuntimeHost:: CreateEvidence メソッド'
title: ICorRuntimeHost::CreateEvidence メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 34694f7e867066430a28120b412237ef9c64c740
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789672"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="a5a1c-103">ICorRuntimeHost::CreateEvidence メソッド</span><span class="sxs-lookup"><span data-stu-id="a5a1c-103">ICorRuntimeHost::CreateEvidence Method</span></span>

<span data-ttu-id="a5a1c-104">型のインターフェイスポインターを取得し <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> ます。これにより、ホストは、 [createdomain](icorruntimehost-createdomain-method.md) メソッドまたは [createdomainex](icorruntimehost-createdomainex-method.md) メソッドに渡すセキュリティ証拠を作成できます。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-104">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5a1c-105">構文</span><span class="sxs-lookup"><span data-stu-id="a5a1c-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5a1c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5a1c-106">Parameters</span></span>  

 `pEvidence`  
 <span data-ttu-id="a5a1c-107">入出力 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> セキュリティ証拠の作成に使用されるインスタンスへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-107">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="a5a1c-108">このポインターは型指定され `IUnknown` ているため、呼び出し元はへのポインターを取得するために、通常、このインターフェイスでを呼び出す必要があり `QueryInterface` <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-108">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5a1c-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="a5a1c-109">Return Value</span></span>  
  
|<span data-ttu-id="a5a1c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5a1c-110">HRESULT</span></span>|<span data-ttu-id="a5a1c-111">説明</span><span class="sxs-lookup"><span data-stu-id="a5a1c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5a1c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5a1c-112">S_OK</span></span>|<span data-ttu-id="a5a1c-113">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-113">The operation was successful.</span></span>|  
|<span data-ttu-id="a5a1c-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a5a1c-114">S_FALSE</span></span>|<span data-ttu-id="a5a1c-115">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a5a1c-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a5a1c-116">E_FAIL</span></span>|<span data-ttu-id="a5a1c-117">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a5a1c-118">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a5a1c-119">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a5a1c-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a5a1c-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a5a1c-121">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5a1c-122">解説</span><span class="sxs-lookup"><span data-stu-id="a5a1c-122">Remarks</span></span>  

 <span data-ttu-id="a5a1c-123">このメソッドは、ネイティブコードから設定できない空のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-123">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="a5a1c-124">代わりに、メソッドを使用する必要があり <xref:System.Security.Policy.Evidence> ます。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-124">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5a1c-125">要件</span><span class="sxs-lookup"><span data-stu-id="a5a1c-125">Requirements</span></span>  

 <span data-ttu-id="a5a1c-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5a1c-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5a1c-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a5a1c-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5a1c-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a5a1c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5a1c-129">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="a5a1c-129">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a1c-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5a1c-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="a5a1c-131">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5a1c-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
