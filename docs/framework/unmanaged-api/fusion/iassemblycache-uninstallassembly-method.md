---
description: '詳細情報: IAssemblyCache:: UninstallAssembly メソッド'
title: IAssemblyCache::UninstallAssembly メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
ms.openlocfilehash: d50108b9090b4250e8a6cec1d9b5c54bb78dee9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760902"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="62d2c-103">IAssemblyCache::UninstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="62d2c-103">IAssemblyCache::UninstallAssembly Method</span></span>

<span data-ttu-id="62d2c-104">指定したアセンブリをグローバルアセンブリキャッシュからアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="62d2c-104">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d2c-105">構文</span><span class="sxs-lookup"><span data-stu-id="62d2c-105">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62d2c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62d2c-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="62d2c-107">からFusion に定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="62d2c-107">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="62d2c-108">からアンインストールするアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="62d2c-108">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="62d2c-109">からアセンブリのインストールデータを格納する [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) 構造体。</span><span class="sxs-lookup"><span data-stu-id="62d2c-109">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="62d2c-110">[out、省略可能]Fusion で定義されている配置値の1つ。</span><span class="sxs-lookup"><span data-stu-id="62d2c-110">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="62d2c-111">次の値があります。</span><span class="sxs-lookup"><span data-stu-id="62d2c-111">Possible values include the following:</span></span>  
  
- <span data-ttu-id="62d2c-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="62d2c-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="62d2c-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="62d2c-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="62d2c-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="62d2c-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="62d2c-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="62d2c-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="62d2c-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="62d2c-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="62d2c-117">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="62d2c-117">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d2c-118">要件</span><span class="sxs-lookup"><span data-stu-id="62d2c-118">Requirements</span></span>  

 <span data-ttu-id="62d2c-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d2c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62d2c-120">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="62d2c-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="62d2c-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62d2c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d2c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="62d2c-122">See also</span></span>

- [<span data-ttu-id="62d2c-123">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62d2c-123">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
