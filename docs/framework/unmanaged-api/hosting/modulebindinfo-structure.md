---
description: 詳細については、「ModuleBindInfo 構造体」を参照してください。
title: ModuleBindInfo 構造体
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
ms.openlocfilehash: 0969c0ecc459414336800e8e7da5817ac0c1a8ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679624"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="2dfe4-103">ModuleBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="2dfe4-103">ModuleBindInfo Structure</span></span>

<span data-ttu-id="2dfe4-104">参照されるモジュールとそれを含むアセンブリに関する詳細情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-104">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dfe4-105">構文</span><span class="sxs-lookup"><span data-stu-id="2dfe4-105">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="2dfe4-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2dfe4-106">Members</span></span>  
  
|<span data-ttu-id="2dfe4-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="2dfe4-107">Member</span></span>|<span data-ttu-id="2dfe4-108">説明</span><span class="sxs-lookup"><span data-stu-id="2dfe4-108">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="2dfe4-109">参照先の `IStream` モジュールの読み込み元である [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md) メソッドへの呼び出しによって返されるの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-109">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="2dfe4-110">参照されたモジュールを含むアセンブリの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-110">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="2dfe4-111">参照されているモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-111">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dfe4-112">解説</span><span class="sxs-lookup"><span data-stu-id="2dfe4-112">Remarks</span></span>  

 <span data-ttu-id="2dfe4-113">`ModuleBindInfo` は、にパラメーターとして渡され `IHostAssemblyStore::ProvideModule` ます。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-113">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="2dfe4-114">ホストは、一意の識別子 `dwAppDomainId` を共通言語ランタイム (CLR) に提供します。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-114">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="2dfe4-115">[IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md)メソッドの呼び出しが返されると、ランタイムは識別子を使用して、の内容が `IStream` マップされているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-115">After a call to the [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="2dfe4-116">その場合、ランタイムはストリームを再マップするのではなく、既存のコピーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-116">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="2dfe4-117">ランタイムは、メソッドへの呼び出しから返されるストリームの参照キーとしても、この識別子を使用し `IHostAssemblyStore::ProvideAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-117">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="2dfe4-118">このため、識別子は、モジュール要求とアセンブリ要求に対して一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-118">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dfe4-119">要件</span><span class="sxs-lookup"><span data-stu-id="2dfe4-119">Requirements</span></span>  

 <span data-ttu-id="2dfe4-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dfe4-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dfe4-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2dfe4-121">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="2dfe4-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2dfe4-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2dfe4-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dfe4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dfe4-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="2dfe4-124">See also</span></span>

- [<span data-ttu-id="2dfe4-125">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="2dfe4-125">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="2dfe4-126">AssemblyBindInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="2dfe4-126">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)
- [<span data-ttu-id="2dfe4-127">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2dfe4-127">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="2dfe4-128">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2dfe4-128">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2dfe4-129">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2dfe4-129">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
