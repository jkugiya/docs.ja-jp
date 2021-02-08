---
description: '詳細情報: IsFrameworkAssembly 関数'
title: IsFrameworkAssembly 関数
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: 8f264df7b1ae5c494298b11ebd94cc93aed5543a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800020"
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="4b237-103">IsFrameworkAssembly 関数</span><span class="sxs-lookup"><span data-stu-id="4b237-103">IsFrameworkAssembly Function</span></span>

<span data-ttu-id="4b237-104">指定したアセンブリが管理されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4b237-104">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b237-105">構文</span><span class="sxs-lookup"><span data-stu-id="4b237-105">Syntax</span></span>  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b237-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4b237-106">Parameters</span></span>  

 `pwzAssemblyReference`  
 <span data-ttu-id="4b237-107">から確認するアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="4b237-107">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="4b237-108">入出力アセンブリが管理されているかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="4b237-108">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="4b237-109">からアセンブリの一意の id を含む、正規化されていない文字列。</span><span class="sxs-lookup"><span data-stu-id="4b237-109">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="4b237-110">[入力] `pwzFrameworkAssemblyIdentity` のサイズ。</span><span class="sxs-lookup"><span data-stu-id="4b237-110">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b237-111">解説</span><span class="sxs-lookup"><span data-stu-id="4b237-111">Remarks</span></span>  

 <span data-ttu-id="4b237-112">パラメーターは、 `pwzAssemblyReference` アセンブリの名前を含む文字列へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="4b237-112">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="4b237-113">このアセンブリが .NET Framework の一部である場合、 `pbIsFrameworkAssembly` パラメーターにはのブール値が格納され `true` ます。</span><span class="sxs-lookup"><span data-stu-id="4b237-113">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="4b237-114">名前付きアセンブリが .NET Framework に含まれていない場合、またはパラメーターがアセンブリの名前を指定しない場合 `pwzAssemblyReference` 、に `pbIsFrameworkAssembly` はブール値のが格納され `false` ます。</span><span class="sxs-lookup"><span data-stu-id="4b237-114">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b237-115">要件</span><span class="sxs-lookup"><span data-stu-id="4b237-115">Requirements</span></span>  

 <span data-ttu-id="4b237-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b237-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b237-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b237-117">See also</span></span>

- [<span data-ttu-id="4b237-118">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="4b237-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
