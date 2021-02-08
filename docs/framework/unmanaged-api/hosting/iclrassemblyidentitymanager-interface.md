---
description: 詳細については、「ICLRAssemblyIdentityManager インターフェイス」を参照してください。
title: ICLRAssemblyIdentityManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: d6238ec51a8cc1bb61eaa96e5297656c447df785
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790056"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="1b398-103">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b398-103">ICLRAssemblyIdentityManager Interface</span></span>

<span data-ttu-id="1b398-104">ホストと、アセンブリに関する共通言語ランタイム (CLR) 間の通信をサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1b398-104">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b398-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1b398-105">Methods</span></span>  
  
|<span data-ttu-id="1b398-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="1b398-106">Method</span></span>|<span data-ttu-id="1b398-107">説明</span><span class="sxs-lookup"><span data-stu-id="1b398-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b398-108">GetBindingIdentityFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="1b398-108">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="1b398-109">指定したファイルパスにあるアセンブリのアセンブリ id バインドデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b398-109">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="1b398-110">GetBindingIdentityFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="1b398-110">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="1b398-111">指定したストリーム内のアセンブリの正規アセンブリ id データを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b398-111">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="1b398-112">GetCLRAssemblyReferenceList メソッド</span><span class="sxs-lookup"><span data-stu-id="1b398-112">GetCLRAssemblyReferenceList Method</span></span>](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="1b398-113">指定された部分アセンブリ id のリストから [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b398-113">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="1b398-114">GetProbingAssembliesFromReference メソッド</span><span class="sxs-lookup"><span data-stu-id="1b398-114">GetProbingAssembliesFromReference Method</span></span>](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="1b398-115">指定した id を持つアセンブリによって参照されるアセンブリ id の [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) 列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b398-115">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="1b398-116">GetReferencedAssembliesFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="1b398-116">GetReferencedAssembliesFromFile Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="1b398-117">指定したファイルパスにあるアセンブリによって参照されるアセンブリのリストを含む [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b398-117">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="1b398-118">GetReferencedAssembliesFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="1b398-118">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="1b398-119">`ICLRReferenceAssemblyEnum`指定したストリーム内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納しているオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b398-119">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="1b398-120">IsStronglyNamed メソッド</span><span class="sxs-lookup"><span data-stu-id="1b398-120">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="1b398-121">指定したアセンブリに厳密な名前が付けられているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b398-121">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b398-122">解説</span><span class="sxs-lookup"><span data-stu-id="1b398-122">Remarks</span></span>  

 <span data-ttu-id="1b398-123">`ICLRAssemblyIdentityManager`のインスタンスを取得し `ICLRAssemblyReferenceList` 、アセンブリ id を列挙するには、を使用します。</span><span class="sxs-lookup"><span data-stu-id="1b398-123">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b398-124">要件</span><span class="sxs-lookup"><span data-stu-id="1b398-124">Requirements</span></span>  

 <span data-ttu-id="1b398-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b398-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b398-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1b398-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b398-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1b398-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b398-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b398-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b398-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b398-129">See also</span></span>

- [<span data-ttu-id="1b398-130">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b398-130">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1b398-131">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b398-131">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="1b398-132">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b398-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
