---
description: '詳細については、次を参照してください: AssemblyComparisonResult 列挙型'
title: AssemblyComparisonResult 列挙型
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: 093cff830aa87d28ee86ecaeb6965887279a72d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761288"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="a68a1-103">AssemblyComparisonResult 列挙型</span><span class="sxs-lookup"><span data-stu-id="a68a1-103">AssemblyComparisonResult Enumeration</span></span>

<span data-ttu-id="a68a1-104">[CompareAssemblyIdentity](compareassemblyidentity-function.md)関数によって決定される2つのアセンブリ id の等価性を示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-104">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68a1-105">構文</span><span class="sxs-lookup"><span data-stu-id="a68a1-105">Syntax</span></span>  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="a68a1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a68a1-106">Members</span></span>  
  
|<span data-ttu-id="a68a1-107">メンバー名</span><span class="sxs-lookup"><span data-stu-id="a68a1-107">Member name</span></span>|<span data-ttu-id="a68a1-108">説明</span><span class="sxs-lookup"><span data-stu-id="a68a1-108">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="a68a1-109">比較対象のすべてのアセンブリフィールドが一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-109">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="a68a1-110">アセンブリが同等と見なされることを示します。これは、.NET Framework バージョン2.0 でのアセンブリバージョン番号の共通言語ランタイムバージョン (CLR) の統合に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a68a1-110">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="a68a1-111">.NET Framework 2.0 のアセンブリバージョン番号と CLR の統合に基づいて、アセンブリの部分的な一致を示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-111">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="a68a1-112">アセンブリの部分的な一致を示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-112">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="a68a1-113">バージョン番号の従来の統合に基づいて、アセンブリの部分的な一致を示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-113">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="a68a1-114">単純に名前付きアセンブリの部分一致を示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-114">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="a68a1-115">.NET Framework のレガシバージョンでの CLR のバージョン番号の統合に基づいて、アセンブリが同等と見なされることを示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-115">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="a68a1-116">バージョン番号が無視された、単純に名前が付けられた2つのアセンブリ間の一致を示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-116">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="a68a1-117">2つのアセンブリ間で一致するものがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-117">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="a68a1-118">2つのアセンブリが、部分的にのみ一致するバージョン番号を除き、一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-118">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="a68a1-119">2つのアセンブリが一致しないバージョン番号を除き、一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-119">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="a68a1-120">非等価性の理由が不明であることを示します。</span><span class="sxs-lookup"><span data-stu-id="a68a1-120">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a68a1-121">要件</span><span class="sxs-lookup"><span data-stu-id="a68a1-121">Requirements</span></span>  

 <span data-ttu-id="a68a1-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a68a1-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a68a1-123">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a68a1-123">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a68a1-124">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a68a1-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a68a1-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a68a1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68a1-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a68a1-126">See also</span></span>

- [<span data-ttu-id="a68a1-127">CompareAssemblyIdentity 関数</span><span class="sxs-lookup"><span data-stu-id="a68a1-127">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="a68a1-128">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="a68a1-128">Fusion Enumerations</span></span>](fusion-enumerations.md)
