---
description: '詳細情報: IAssemblyCache:: InstallAssembly メソッド'
title: IAssemblyCache::InstallAssembly メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
ms.openlocfilehash: 0bb9fe31467506a03f5e81e5a29a6b1fb65f5804
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760943"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="38264-103">IAssemblyCache::InstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="38264-103">IAssemblyCache::InstallAssembly Method</span></span>

<span data-ttu-id="38264-104">指定したアセンブリをグローバルアセンブリキャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="38264-104">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38264-105">構文</span><span class="sxs-lookup"><span data-stu-id="38264-105">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38264-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38264-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="38264-107">からFusion に定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="38264-107">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="38264-108">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="38264-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="38264-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="38264-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="38264-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="38264-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="38264-111">からインストールするアセンブリのマニフェストへのパス。</span><span class="sxs-lookup"><span data-stu-id="38264-111">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="38264-112">からインストールのためのデータを格納する [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) 構造体。</span><span class="sxs-lookup"><span data-stu-id="38264-112">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38264-113">要件</span><span class="sxs-lookup"><span data-stu-id="38264-113">Requirements</span></span>  

 <span data-ttu-id="38264-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38264-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38264-115">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="38264-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="38264-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38264-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38264-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="38264-117">See also</span></span>

- [<span data-ttu-id="38264-118">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38264-118">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
