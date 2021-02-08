---
description: '詳細について: ICorRuntimeHost:: CreateDomain メソッド'
title: ICorRuntimeHost::CreateDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
ms.openlocfilehash: 6173d74d97ddb9dec619db8583036ec763a9e293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789711"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="ce14a-103">ICorRuntimeHost::CreateDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="ce14a-103">ICorRuntimeHost::CreateDomain Method</span></span>

<span data-ttu-id="ce14a-104">アプリケーションドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="ce14a-104">Creates an application domain.</span></span> <span data-ttu-id="ce14a-105">呼び出し元は、型のインターフェイスポインターを <xref:System._AppDomain> 型のインスタンスに受信し <xref:System.AppDomain?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="ce14a-105">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce14a-106">構文</span><span class="sxs-lookup"><span data-stu-id="ce14a-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce14a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ce14a-107">Parameters</span></span>  

 `pwzFriendlyName`  
 <span data-ttu-id="ce14a-108">からドメインのフレンドリ名を指定するために使用される省略可能なパラメーター。</span><span class="sxs-lookup"><span data-stu-id="ce14a-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="ce14a-109">このフレンドリ名は、ドメインを識別するためのデバッガーなどのユーザーインターフェイスに表示できます。</span><span class="sxs-lookup"><span data-stu-id="ce14a-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="ce14a-110">から `IIdentity` アクセス許可セットを確立するためにセキュリティポリシーによってマップされた証拠を表す、インスタンスへのポインターの配列 (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="ce14a-110">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="ce14a-111">`IIdentity`オブジェクトは、 [createevidence](icorruntimehost-createevidence-method.md)メソッドを呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="ce14a-111">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="ce14a-112">入出力 <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> ドメインをさらに制御するために使用できるのインスタンスへの型のインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="ce14a-112">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce14a-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="ce14a-113">Return Value</span></span>  
  
|<span data-ttu-id="ce14a-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce14a-114">HRESULT</span></span>|<span data-ttu-id="ce14a-115">説明</span><span class="sxs-lookup"><span data-stu-id="ce14a-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce14a-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce14a-116">S_OK</span></span>|<span data-ttu-id="ce14a-117">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="ce14a-117">The operation was successful.</span></span>|  
|<span data-ttu-id="ce14a-118">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ce14a-118">S_FALSE</span></span>|<span data-ttu-id="ce14a-119">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ce14a-119">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ce14a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ce14a-120">E_FAIL</span></span>|<span data-ttu-id="ce14a-121">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ce14a-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ce14a-122">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ce14a-122">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ce14a-123">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ce14a-123">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ce14a-124">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ce14a-124">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ce14a-125">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="ce14a-125">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce14a-126">要件</span><span class="sxs-lookup"><span data-stu-id="ce14a-126">Requirements</span></span>  

 <span data-ttu-id="ce14a-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce14a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce14a-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ce14a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce14a-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ce14a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce14a-130">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="ce14a-130">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce14a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce14a-131">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="ce14a-132">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce14a-132">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
