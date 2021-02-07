---
description: '詳細情報: AssemblyFlags 列挙型'
title: AssemblyFlags 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: 17cc0dec305c21d21693fe8f4f8d82c039f73278
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679005"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="c6294-103">AssemblyFlags 列挙体</span><span class="sxs-lookup"><span data-stu-id="c6294-103">AssemblyFlags Enumeration</span></span>

<span data-ttu-id="c6294-104">アセンブリのランタイム機能を記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="c6294-104">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6294-105">構文</span><span class="sxs-lookup"><span data-stu-id="c6294-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c6294-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c6294-106">Members</span></span>  
  
|<span data-ttu-id="c6294-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="c6294-107">Member</span></span>|<span data-ttu-id="c6294-108">説明</span><span class="sxs-lookup"><span data-stu-id="c6294-108">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="c6294-109">エクスポートされた型定義が、アセンブリを構成するファイル内で暗黙的に指定されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6294-109">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="c6294-110">.NET Framework バージョン1.0 および1.1 では、この値は常に設定されると想定されます。</span><span class="sxs-lookup"><span data-stu-id="c6294-110">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="c6294-111">アセンブリを構成するファイル内でリソース定義が暗黙的であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6294-111">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="c6294-112">.NET Framework 1.0 および1.1 では、この値は常に設定されると想定されます。</span><span class="sxs-lookup"><span data-stu-id="c6294-112">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="c6294-113">アセンブリが同じアプリケーションドメインで実行されている場合、その他のバージョンでは実行できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6294-113">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="c6294-114">同じプロセスで実行されている場合、アセンブリを他のバージョンと一緒に実行できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6294-114">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="c6294-115">アセンブリが同じコンピューター上で実行されている場合、その他のバージョンでは実行できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6294-115">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6294-116">解説</span><span class="sxs-lookup"><span data-stu-id="c6294-116">Remarks</span></span>  

 <span data-ttu-id="c6294-117">0x0010 と0x0070 の間の値は、参照アセンブリのサイドバイサイドの互換性機能を記述するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c6294-117">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="c6294-118">これらの値のいずれも設定されていない場合、アセンブリはサイドバイサイドで互換性があると見なされます。</span><span class="sxs-lookup"><span data-stu-id="c6294-118">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6294-119">要件</span><span class="sxs-lookup"><span data-stu-id="c6294-119">Requirements</span></span>  

 <span data-ttu-id="c6294-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6294-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6294-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c6294-121">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="c6294-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c6294-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6294-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6294-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6294-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6294-124">See also</span></span>

- [<span data-ttu-id="c6294-125">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="c6294-125">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="c6294-126">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c6294-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
