---
description: '詳細情報: GetAssemblyIdentityFromFile 関数'
title: GetAssemblyIdentityFromFile 関数
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 8832e03182a5652c938404c99115fa8059439d1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761037"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="49613-103">GetAssemblyIdentityFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="49613-103">GetAssemblyIdentityFromFile Function</span></span>

<span data-ttu-id="49613-104">指定した `IUnknown` `IID` ファイルパスのアセンブリ内で、指定したを持つオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="49613-104">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49613-105">構文</span><span class="sxs-lookup"><span data-stu-id="49613-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="49613-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49613-106">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="49613-107">から要求されたアセンブリへの有効なパス。</span><span class="sxs-lookup"><span data-stu-id="49613-107">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="49613-108">から `IID` 返されるインターフェイスの。</span><span class="sxs-lookup"><span data-stu-id="49613-108">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="49613-109">入出力返されたインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="49613-109">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49613-110">要件</span><span class="sxs-lookup"><span data-stu-id="49613-110">Requirements</span></span>  

 <span data-ttu-id="49613-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49613-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49613-112">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="49613-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="49613-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49613-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49613-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="49613-114">See also</span></span>

- [<span data-ttu-id="49613-115">IUnknown</span><span class="sxs-lookup"><span data-stu-id="49613-115">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="49613-116">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="49613-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
