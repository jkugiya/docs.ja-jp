---
description: '詳細情報: AssemblyOptions 列挙型'
title: AssemblyOptions 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
ms.openlocfilehash: aba9ecb3176f533e2d53e2e45fef3d1dc4e55077
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638419"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="c2151-103">AssemblyOptions 列挙体</span><span class="sxs-lookup"><span data-stu-id="c2151-103">AssemblyOptions Enumeration</span></span>

<span data-ttu-id="c2151-104">アセンブリオプションを列挙します。</span><span class="sxs-lookup"><span data-stu-id="c2151-104">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2151-105">構文</span><span class="sxs-lookup"><span data-stu-id="c2151-105">Syntax</span></span>  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="c2151-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="c2151-106">Fields</span></span>  
  
|<span data-ttu-id="c2151-107">フィールド</span><span class="sxs-lookup"><span data-stu-id="c2151-107">Field</span></span>|<span data-ttu-id="c2151-108">説明</span><span class="sxs-lookup"><span data-stu-id="c2151-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c2151-109">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="c2151-109">optAssemTitle</span></span>|<span data-ttu-id="c2151-110">String-アセンブリのタイトルを表します。</span><span class="sxs-lookup"><span data-stu-id="c2151-110">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="c2151-111">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="c2151-111">optAssemDescription</span></span>|<span data-ttu-id="c2151-112">String-アセンブリの説明が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c2151-112">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="c2151-113">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="c2151-113">optAssemConfig</span></span>|<span data-ttu-id="c2151-114">String-アセンブリ構成が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c2151-114">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="c2151-115">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="c2151-115">optAssemOS</span></span>|<span data-ttu-id="c2151-116">"DwOSPlatformId" としてエンコードされた文字列。</span><span class="sxs-lookup"><span data-stu-id="c2151-116">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="c2151-117">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="c2151-117">optAssemProcessor</span></span>|<span data-ttu-id="c2151-118">ULONG</span><span class="sxs-lookup"><span data-stu-id="c2151-118">ULONG</span></span>|  
|<span data-ttu-id="c2151-119">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="c2151-119">optAssemLocale</span></span>|<span data-ttu-id="c2151-120">String-アセンブリロケールを格納します。</span><span class="sxs-lookup"><span data-stu-id="c2151-120">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="c2151-121">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="c2151-121">optAssemVersion</span></span>|<span data-ttu-id="c2151-122">"Major. Minor. Build. Revision" としてエンコードされた文字列。</span><span class="sxs-lookup"><span data-stu-id="c2151-122">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="c2151-123">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="c2151-123">optAssemCompany</span></span>|<span data-ttu-id="c2151-124">文字列-会社を含みます。</span><span class="sxs-lookup"><span data-stu-id="c2151-124">String - Contains the company.</span></span>|  
|<span data-ttu-id="c2151-125">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="c2151-125">optAssemProduct</span></span>|<span data-ttu-id="c2151-126">文字列-製品名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c2151-126">String - Contains the product name.</span></span>|  
|<span data-ttu-id="c2151-127">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="c2151-127">optAssemProductVersion</span></span>|<span data-ttu-id="c2151-128">文字列 (InformationalVersion とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="c2151-128">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="c2151-129">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="c2151-129">optAssemCopyright</span></span>|<span data-ttu-id="c2151-130">文字列-著作権情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c2151-130">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="c2151-131">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="c2151-131">optAssemTrademark</span></span>|<span data-ttu-id="c2151-132">String-商標情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c2151-132">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="c2151-133">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="c2151-133">optAssemKeyFile</span></span>|<span data-ttu-id="c2151-134">文字列 (ファイル名)。</span><span class="sxs-lookup"><span data-stu-id="c2151-134">String (file name).</span></span>|  
|<span data-ttu-id="c2151-135">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="c2151-135">optAssemKeyName</span></span>|<span data-ttu-id="c2151-136">文字列 (キー名)。</span><span class="sxs-lookup"><span data-stu-id="c2151-136">String (The key name).</span></span>|  
|<span data-ttu-id="c2151-137">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="c2151-137">optAssemAlgID</span></span>|<span data-ttu-id="c2151-138">ULONG</span><span class="sxs-lookup"><span data-stu-id="c2151-138">ULONG</span></span>|  
|<span data-ttu-id="c2151-139">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="c2151-139">optAssemFlags</span></span>|<span data-ttu-id="c2151-140">ULONG</span><span class="sxs-lookup"><span data-stu-id="c2151-140">ULONG</span></span>|  
|<span data-ttu-id="c2151-141">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="c2151-141">optAssemHalfSign</span></span>|<span data-ttu-id="c2151-142">Bool (DelaySign とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="c2151-142">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="c2151-143">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="c2151-143">optAssemFileVersion</span></span>|<span data-ttu-id="c2151-144">"Major. Minor. Build. Revision" としてエンコードされた文字列。 ProductVersion と同じです。</span><span class="sxs-lookup"><span data-stu-id="c2151-144">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="c2151-145">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="c2151-145">optAssemSatelliteVer</span></span>|<span data-ttu-id="c2151-146">"Major. Minor. Build. Revision" としてエンコードされた文字列。</span><span class="sxs-lookup"><span data-stu-id="c2151-146">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="c2151-147">optlastassemoopt</span><span class="sxs-lookup"><span data-stu-id="c2151-147">optLastAssemOption</span></span>|<span data-ttu-id="c2151-148">要素数のカウンター。</span><span class="sxs-lookup"><span data-stu-id="c2151-148">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2151-149">要件</span><span class="sxs-lookup"><span data-stu-id="c2151-149">Requirements</span></span>  

 <span data-ttu-id="c2151-150">**ヘッダー:** alink</span><span class="sxs-lookup"><span data-stu-id="c2151-150">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="c2151-151">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="c2151-151">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2151-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2151-152">See also</span></span>

- [<span data-ttu-id="c2151-153">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="c2151-153">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
