---
description: '詳細情報: COR_PRF_ASSEMBLY_REFERENCE_INFO 構造'
title: COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: fc384e0a302c83af510deefc6f9f3b9cd5a2f77f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649222"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="713eb-103">COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="713eb-103">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>

<span data-ttu-id="713eb-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="713eb-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="713eb-105">アセンブリ参照クロージャのウォークを実行するときに考慮する必要があるアセンブリ参照の情報を、共通言語ランタイムに提供します。</span><span class="sxs-lookup"><span data-stu-id="713eb-105">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713eb-106">構文</span><span class="sxs-lookup"><span data-stu-id="713eb-106">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="713eb-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="713eb-107">Members</span></span>  
  
|<span data-ttu-id="713eb-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="713eb-108">Member</span></span>|<span data-ttu-id="713eb-109">説明</span><span class="sxs-lookup"><span data-stu-id="713eb-109">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="713eb-110">公開キー、またはアセンブリのトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="713eb-110">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="713eb-111">公開キーまたはトークンのバイト数。</span><span class="sxs-lookup"><span data-stu-id="713eb-111">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="713eb-112">参照されるアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="713eb-112">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="713eb-113">アセンブリのメタデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="713eb-113">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="713eb-114">ハッシュ バイナリ ラージ オブジェクト (BLOB) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="713eb-114">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="713eb-115">ハッシュ BLOB のバイト数。</span><span class="sxs-lookup"><span data-stu-id="713eb-115">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="713eb-116">アセンブリのフラグ。</span><span class="sxs-lookup"><span data-stu-id="713eb-116">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="713eb-117">解説</span><span class="sxs-lookup"><span data-stu-id="713eb-117">Remarks</span></span>  

 <span data-ttu-id="713eb-118">`COR_PRF_EX_CLAUSE_INFO` 構造は、追加のアセンブリ参照を宣言するときに、プロファイラーによって値が設定されます。ここでの追加のアセンブリ参照は、アセンブリ参照クロージャのウォークを実行するときに共通言語ランタイムが考慮するものです。</span><span class="sxs-lookup"><span data-stu-id="713eb-118">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="713eb-119">プロファイラーが [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback メソッドを登録すると、ランタイムは、読み込まれるアセンブリのパスと名前、およびそのメソッドへの [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) インターフェイスオブジェクトへのポインターを渡します。</span><span class="sxs-lookup"><span data-stu-id="713eb-119">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="713eb-120">その後、プロファイラーは、 [](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) `COR_PRF_ASSEMBLY_REFERENCE_INFO` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)コールバックで指定されたアセンブリから参照するターゲットアセンブリごとに、オブジェクトを使用して ICorProfilerAssemblyReferenceProvider:: addassemblyreference メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="713eb-120">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="713eb-121">要件</span><span class="sxs-lookup"><span data-stu-id="713eb-121">Requirements</span></span>  

 <span data-ttu-id="713eb-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="713eb-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="713eb-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="713eb-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="713eb-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="713eb-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="713eb-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="713eb-125">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713eb-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="713eb-126">See also</span></span>

- [<span data-ttu-id="713eb-127">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="713eb-127">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="713eb-128">GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="713eb-128">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="713eb-129">AddAssemblyReference メソッド</span><span class="sxs-lookup"><span data-stu-id="713eb-129">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
