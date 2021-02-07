---
description: 詳細については、「ASSEMBLYMETADATA 構造体」を参照してください。
title: ASSEMBLYMETADATA 構造体
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
ms.openlocfilehash: 6fc9c03bea3b1413cd3a8421746137e37d43bd90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678940"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="91c72-103">ASSEMBLYMETADATA 構造体</span><span class="sxs-lookup"><span data-stu-id="91c72-103">ASSEMBLYMETADATA Structure</span></span>

<span data-ttu-id="91c72-104">バージョン、ロケール、プロセッサ、オペレーティングシステムのサポートレベルなど、参照されるアセンブリに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="91c72-104">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91c72-105">構文</span><span class="sxs-lookup"><span data-stu-id="91c72-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="91c72-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="91c72-106">Members</span></span>  
  
|<span data-ttu-id="91c72-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="91c72-107">Member</span></span>|<span data-ttu-id="91c72-108">説明</span><span class="sxs-lookup"><span data-stu-id="91c72-108">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="91c72-109">参照アセンブリのメジャーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="91c72-109">The major version number of the referenced assembly.</span></span> <span data-ttu-id="91c72-110">この値を0にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="91c72-110">This value cannot be zero.</span></span> <span data-ttu-id="91c72-111">のすべてのビットが設定されている場合は、 `usMajorVersion` メジャーバージョンが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="91c72-111">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="91c72-112">参照アセンブリのマイナーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="91c72-112">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="91c72-113">この値を0にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="91c72-113">This value cannot be zero.</span></span> <span data-ttu-id="91c72-114">のすべてのビットが設定されている場合は、 `usMinorVersion` マイナーバージョンが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="91c72-114">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="91c72-115">参照アセンブリのビルド番号。</span><span class="sxs-lookup"><span data-stu-id="91c72-115">The build number of the referenced assembly.</span></span> <span data-ttu-id="91c72-116">この値を0にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="91c72-116">This value cannot be zero.</span></span> <span data-ttu-id="91c72-117">のすべてのビットが設定されている場合は、 `usBuildNumber` ビルド番号が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="91c72-117">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="91c72-118">参照アセンブリのリビジョン番号。</span><span class="sxs-lookup"><span data-stu-id="91c72-118">The revision number of the referenced assembly.</span></span> <span data-ttu-id="91c72-119">この値を0にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="91c72-119">This value cannot be zero.</span></span> <span data-ttu-id="91c72-120">のすべてのビットが設定されている場合は、 `usRevisionNumber` リビジョン番号が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="91c72-120">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="91c72-121">RFC1766 仕様に準拠しているロケール名のリスト。セミコロンで区切られ、参照アセンブリによってサポートされるロケールを指定します。</span><span class="sxs-lookup"><span data-stu-id="91c72-121">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="91c72-122">Null 値は、ロケールに依存しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="91c72-122">A null value indicates locale independence.</span></span> <span data-ttu-id="91c72-123">**注:**  .NET Framework バージョン1.0 では、複数のロケールを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="91c72-123">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="91c72-124">のワイド文字のサイズ `szLocale` 。</span><span class="sxs-lookup"><span data-stu-id="91c72-124">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="91c72-125">参照アセンブリでサポートされているプロセッサの種類について、Winnt.h で定義されている識別子の配列。</span><span class="sxs-lookup"><span data-stu-id="91c72-125">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="91c72-126">NULL 値は、プロセッサに依存しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="91c72-126">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="91c72-127">`rdwProcessor` 配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="91c72-127">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="91c72-128">参照アセンブリによってサポートされているオペレーティングシステムを指定する [Osinfo](osinfo-structure.md) インスタンスの配列。</span><span class="sxs-lookup"><span data-stu-id="91c72-128">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="91c72-129">NULL 値は、オペレーティングシステムに依存しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="91c72-129">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="91c72-130">`rOS` 配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="91c72-130">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91c72-131">要件</span><span class="sxs-lookup"><span data-stu-id="91c72-131">Requirements</span></span>  

 <span data-ttu-id="91c72-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91c72-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91c72-133">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="91c72-133">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91c72-134">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="91c72-134">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91c72-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91c72-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c72-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="91c72-136">See also</span></span>

- [<span data-ttu-id="91c72-137">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="91c72-137">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="91c72-138">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91c72-138">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="91c72-139">OSINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="91c72-139">OSINFO Structure</span></span>](osinfo-structure.md)
