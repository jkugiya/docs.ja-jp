---
description: '詳細情報: _CorImageUnloading 関数'
title: _CorImageUnloading 関数
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
ms.openlocfilehash: fe10c97be66aab21793b1ad306aa5d90eaa1ade2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716992"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="6d8a1-103">_CorImageUnloading 関数</span><span class="sxs-lookup"><span data-stu-id="6d8a1-103">_CorImageUnloading Function</span></span>

<span data-ttu-id="6d8a1-104">マネージド モジュール イメージがアンロードされたときに、ローダーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6d8a1-104">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="6d8a1-105">この関数は実装されていません。</span><span class="sxs-lookup"><span data-stu-id="6d8a1-105">This function is not implemented.</span></span> <span data-ttu-id="6d8a1-106">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="6d8a1-106">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d8a1-107">構文</span><span class="sxs-lookup"><span data-stu-id="6d8a1-107">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d8a1-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d8a1-108">Parameters</span></span>  

 `ImageBase`  
 <span data-ttu-id="6d8a1-109">からアンロードするイメージの開始位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6d8a1-109">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d8a1-110">要件</span><span class="sxs-lookup"><span data-stu-id="6d8a1-110">Requirements</span></span>  

 <span data-ttu-id="6d8a1-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d8a1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d8a1-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="6d8a1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d8a1-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6d8a1-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d8a1-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d8a1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d8a1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d8a1-115">See also</span></span>

- [<span data-ttu-id="6d8a1-116">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="6d8a1-116">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
