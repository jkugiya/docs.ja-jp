---
description: 詳細については、「AssemblyBindInfo 構造体」を参照してください。
title: AssemblyBindInfo 構造体
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 3e11e05924ee6818737f84d9ca92394ee5313292
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799981"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="4edc8-103">AssemblyBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="4edc8-103">AssemblyBindInfo Structure</span></span>

<span data-ttu-id="4edc8-104">参照アセンブリに関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="4edc8-104">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4edc8-105">構文</span><span class="sxs-lookup"><span data-stu-id="4edc8-105">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="4edc8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4edc8-106">Members</span></span>  
  
|<span data-ttu-id="4edc8-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="4edc8-107">Member</span></span>|<span data-ttu-id="4edc8-108">説明</span><span class="sxs-lookup"><span data-stu-id="4edc8-108">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="4edc8-109">`IStream` [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md)への呼び出しによって返されるの一意の識別子。参照されるアセンブリが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="4edc8-109">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="4edc8-110">参照アセンブリの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="4edc8-110">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="4edc8-111">バインドポリシー値の適用後に参照されるアセンブリの識別子。</span><span class="sxs-lookup"><span data-stu-id="4edc8-111">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="4edc8-112">参照先のアセンブリに適用するバージョン管理ポリシーを示す [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="4edc8-112">One of the [EPolicyAction](epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4edc8-113">解説</span><span class="sxs-lookup"><span data-stu-id="4edc8-113">Remarks</span></span>  

 <span data-ttu-id="4edc8-114">ホストは、一意の識別子 `dwAppDomainId` を共通言語ランタイム (CLR) に提供します。</span><span class="sxs-lookup"><span data-stu-id="4edc8-114">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="4edc8-115">の呼び出しが戻ると、 `IHostAssemblyStore::ProvideAssembly` ランタイムは識別子を使用して、の内容が `IStream` マップされているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="4edc8-115">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="4edc8-116">その場合、ランタイムはストリームを再マップするのではなく、既存のコピーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="4edc8-116">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="4edc8-117">ランタイムは、 [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md)への呼び出しから返されたストリームの参照キーとしても、この識別子を使用します。</span><span class="sxs-lookup"><span data-stu-id="4edc8-117">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="4edc8-118">このため、識別子はモジュール要求とアセンブリ要求に対して一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4edc8-118">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4edc8-119">要件</span><span class="sxs-lookup"><span data-stu-id="4edc8-119">Requirements</span></span>  

 <span data-ttu-id="4edc8-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4edc8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4edc8-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4edc8-121">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4edc8-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4edc8-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4edc8-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4edc8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4edc8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="4edc8-124">See also</span></span>

- [<span data-ttu-id="4edc8-125">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="4edc8-125">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="4edc8-126">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4edc8-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="4edc8-127">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4edc8-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4edc8-128">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4edc8-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="4edc8-129">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4edc8-129">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="4edc8-130">ModuleBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="4edc8-130">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)
