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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638419"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="a1384-103">AssemblyOptions 列挙体</span><span class="sxs-lookup"><span data-stu-id="a1384-103">AssemblyOptions Enumeration</span></span>

<span data-ttu-id="a1384-104">アセンブリ オプションを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a1384-104">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1384-105">構文</span><span class="sxs-lookup"><span data-stu-id="a1384-105">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="a1384-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="a1384-106">Fields</span></span>  
  
|<span data-ttu-id="a1384-107">フィールド</span><span class="sxs-lookup"><span data-stu-id="a1384-107">Field</span></span>|<span data-ttu-id="a1384-108">説明</span><span class="sxs-lookup"><span data-stu-id="a1384-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a1384-109">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="a1384-109">optAssemTitle</span></span>|<span data-ttu-id="a1384-110">String - アセンブリのタイトルを表します。</span><span class="sxs-lookup"><span data-stu-id="a1384-110">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="a1384-111">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="a1384-111">optAssemDescription</span></span>|<span data-ttu-id="a1384-112">String - アセンブリの説明を格納します。</span><span class="sxs-lookup"><span data-stu-id="a1384-112">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="a1384-113">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="a1384-113">optAssemConfig</span></span>|<span data-ttu-id="a1384-114">String - アセンブリ構成を格納します。</span><span class="sxs-lookup"><span data-stu-id="a1384-114">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="a1384-115">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="a1384-115">optAssemOS</span></span>|<span data-ttu-id="a1384-116">String - 次のようにエンコードされます: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"。</span><span class="sxs-lookup"><span data-stu-id="a1384-116">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="a1384-117">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="a1384-117">optAssemProcessor</span></span>|<span data-ttu-id="a1384-118">ULONG</span><span class="sxs-lookup"><span data-stu-id="a1384-118">ULONG</span></span>|  
|<span data-ttu-id="a1384-119">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="a1384-119">optAssemLocale</span></span>|<span data-ttu-id="a1384-120">String - アセンブリ ロケールを格納します。</span><span class="sxs-lookup"><span data-stu-id="a1384-120">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="a1384-121">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="a1384-121">optAssemVersion</span></span>|<span data-ttu-id="a1384-122">String - 次のようにエンコードされます: "Major.Minor.Build.Revision"。</span><span class="sxs-lookup"><span data-stu-id="a1384-122">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="a1384-123">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="a1384-123">optAssemCompany</span></span>|<span data-ttu-id="a1384-124">String - 会社名を格納します。</span><span class="sxs-lookup"><span data-stu-id="a1384-124">String - Contains the company.</span></span>|  
|<span data-ttu-id="a1384-125">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="a1384-125">optAssemProduct</span></span>|<span data-ttu-id="a1384-126">String - 製品名を格納します。</span><span class="sxs-lookup"><span data-stu-id="a1384-126">String - Contains the product name.</span></span>|  
|<span data-ttu-id="a1384-127">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="a1384-127">optAssemProductVersion</span></span>|<span data-ttu-id="a1384-128">String (InformationalVersion とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="a1384-128">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="a1384-129">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="a1384-129">optAssemCopyright</span></span>|<span data-ttu-id="a1384-130">String - 著作権情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="a1384-130">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="a1384-131">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="a1384-131">optAssemTrademark</span></span>|<span data-ttu-id="a1384-132">String - 商標情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="a1384-132">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="a1384-133">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="a1384-133">optAssemKeyFile</span></span>|<span data-ttu-id="a1384-134">String (ファイル名)。</span><span class="sxs-lookup"><span data-stu-id="a1384-134">String (file name).</span></span>|  
|<span data-ttu-id="a1384-135">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="a1384-135">optAssemKeyName</span></span>|<span data-ttu-id="a1384-136">String (キー名)。</span><span class="sxs-lookup"><span data-stu-id="a1384-136">String (The key name).</span></span>|  
|<span data-ttu-id="a1384-137">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="a1384-137">optAssemAlgID</span></span>|<span data-ttu-id="a1384-138">ULONG</span><span class="sxs-lookup"><span data-stu-id="a1384-138">ULONG</span></span>|  
|<span data-ttu-id="a1384-139">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="a1384-139">optAssemFlags</span></span>|<span data-ttu-id="a1384-140">ULONG</span><span class="sxs-lookup"><span data-stu-id="a1384-140">ULONG</span></span>|  
|<span data-ttu-id="a1384-141">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="a1384-141">optAssemHalfSign</span></span>|<span data-ttu-id="a1384-142">Bool (DelaySign とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="a1384-142">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="a1384-143">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="a1384-143">optAssemFileVersion</span></span>|<span data-ttu-id="a1384-144">String - 次のようにエンコードされます: "Major.Minor.Build.Revision"。ProductVersion と同じです。</span><span class="sxs-lookup"><span data-stu-id="a1384-144">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="a1384-145">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="a1384-145">optAssemSatelliteVer</span></span>|<span data-ttu-id="a1384-146">String - "Major.Minor.Build.Revision" としてエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="a1384-146">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="a1384-147">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="a1384-147">optLastAssemOption</span></span>|<span data-ttu-id="a1384-148">要素数のカウンター。</span><span class="sxs-lookup"><span data-stu-id="a1384-148">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1384-149">必要条件</span><span class="sxs-lookup"><span data-stu-id="a1384-149">Requirements</span></span>  

 <span data-ttu-id="a1384-150">**ヘッダー:** alink.h</span><span class="sxs-lookup"><span data-stu-id="a1384-150">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="a1384-151">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="a1384-151">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1384-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1384-152">See also</span></span>

- [<span data-ttu-id="a1384-153">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="a1384-153">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
