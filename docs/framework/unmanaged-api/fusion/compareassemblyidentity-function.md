---
description: '詳細情報: CompareAssemblyIdentity 関数'
title: CompareAssemblyIdentity 関数
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
ms.openlocfilehash: aa55d1ea0b1968ec4e50106139e154e29e159ec7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761214"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="89df2-103">CompareAssemblyIdentity 関数</span><span class="sxs-lookup"><span data-stu-id="89df2-103">CompareAssemblyIdentity Function</span></span>

<span data-ttu-id="89df2-104">2つのアセンブリ id を比較して、それらが等しいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="89df2-104">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89df2-105">構文</span><span class="sxs-lookup"><span data-stu-id="89df2-105">Syntax</span></span>  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="89df2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="89df2-106">Parameters</span></span>  

 `pwzAssemblyIdentity1`  
 <span data-ttu-id="89df2-107">から比較対象の最初のアセンブリのテキスト id。</span><span class="sxs-lookup"><span data-stu-id="89df2-107">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="89df2-108">からのユーザー指定の統一を示すブール型のフラグ `pwzAssemblyIdentity1` 。</span><span class="sxs-lookup"><span data-stu-id="89df2-108">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="89df2-109">から比較対象の2番目のアセンブリのテキスト id。</span><span class="sxs-lookup"><span data-stu-id="89df2-109">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="89df2-110">からのユーザー指定の統一を示すブール型のフラグ `pwzAssemblyIdentity2` 。</span><span class="sxs-lookup"><span data-stu-id="89df2-110">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="89df2-111">入出力2つのアセンブリが等しいかどうかを示すブール型のフラグ。</span><span class="sxs-lookup"><span data-stu-id="89df2-111">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="89df2-112">入出力比較に関する詳細情報を含む [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) 列挙です。</span><span class="sxs-lookup"><span data-stu-id="89df2-112">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89df2-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="89df2-113">Return Value</span></span>  

 <span data-ttu-id="89df2-114">`pfEquivalent` 2つのアセンブリが等しいかどうかを示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="89df2-114">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="89df2-115">`pResult` 値の1つを返し `AssemblyComparisonResult` 、の値のより詳細な理由を指定し `pfEquivalent` ます。</span><span class="sxs-lookup"><span data-stu-id="89df2-115">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89df2-116">解説</span><span class="sxs-lookup"><span data-stu-id="89df2-116">Remarks</span></span>  

 <span data-ttu-id="89df2-117">`CompareAssemblyIdentity` とが等価かどうかを確認し `pwzAssemblyIdentity1` `pwzAssemblyIdentity2` ます。</span><span class="sxs-lookup"><span data-stu-id="89df2-117">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="89df2-118">`pfEquivalent` は `true` 、次の条件の1つ以上でに設定されます。</span><span class="sxs-lookup"><span data-stu-id="89df2-118">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="89df2-119">2つのアセンブリ id は同等です。</span><span class="sxs-lookup"><span data-stu-id="89df2-119">The two assembly identities are equivalent.</span></span> <span data-ttu-id="89df2-120">厳密な名前が付けられたアセンブリの場合、等価性には、アセンブリ名、バージョン、公開キートークン、およびカルチャが同一である必要があります。</span><span class="sxs-lookup"><span data-stu-id="89df2-120">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="89df2-121">単純な名前付きアセンブリの場合、等価性にはアセンブリ名とカルチャの一致が必要です。</span><span class="sxs-lookup"><span data-stu-id="89df2-121">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="89df2-122">どちらのアセンブリ id も、.NET Framework で実行されるアセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="89df2-122">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="89df2-123">この条件は `true` 、アセンブリのバージョン番号が一致しない場合でもを返します。</span><span class="sxs-lookup"><span data-stu-id="89df2-123">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="89df2-124">2つのアセンブリはマネージアセンブリではありませんが、 `fUnified1` または `fUnified2` がに設定されてい `true` ます。</span><span class="sxs-lookup"><span data-stu-id="89df2-124">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="89df2-125">フラグは、 `fUnified` 厳密な名前が付けられたアセンブリのバージョン番号までのすべてのバージョン番号が、厳密に名前が付けられたアセンブリと同等であると見なされることを示します。</span><span class="sxs-lookup"><span data-stu-id="89df2-125">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="89df2-126">たとえば、の値 `pwzAssemblyIndentity1` が "MyAssembly, version = 3.0.0.0, culture = ニュートラル, publicKeyToken =..." で、の値がの場合、 `fUnified1` `true` バージョン0.0.0.0 から3.0.0.0 のすべてのバージョンの MyAssembly が同等として扱われることを示します。</span><span class="sxs-lookup"><span data-stu-id="89df2-126">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="89df2-127">このような場合、 `pwzAssemblyIndentity2` がと同じアセンブリを参照している場合は、 `pwzAssemblyIndentity1` バージョン番号が低い点が `pfEquivalent` に設定され `true` ます。</span><span class="sxs-lookup"><span data-stu-id="89df2-127">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="89df2-128">が `pwzAssemblyIdentity2` より上位のバージョン番号を参照している場合、 `pfEquivalent` の値がである場合にのみがに設定され `true` `fUnified2` `true` ます。</span><span class="sxs-lookup"><span data-stu-id="89df2-128">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="89df2-129">パラメーターには、 `pResult` 2 つのアセンブリが同等であるかどうかについての特定の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="89df2-129">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="89df2-130">詳細については、「 [AssemblyComparisonResult 列挙型](assemblycomparisonresult-enumeration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89df2-130">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89df2-131">要件</span><span class="sxs-lookup"><span data-stu-id="89df2-131">Requirements</span></span>  

 <span data-ttu-id="89df2-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89df2-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89df2-133">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="89df2-133">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="89df2-134">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="89df2-134">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89df2-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89df2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89df2-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="89df2-136">See also</span></span>

- [<span data-ttu-id="89df2-137">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="89df2-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="89df2-138">AssemblyComparisonResult 列挙型</span><span class="sxs-lookup"><span data-stu-id="89df2-138">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
