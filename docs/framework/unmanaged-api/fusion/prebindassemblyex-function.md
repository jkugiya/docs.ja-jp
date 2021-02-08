---
description: '詳細情報: PreBindAssemblyEx 関数'
title: PreBindAssemblyEx 関数
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
ms.openlocfilehash: e94bd7c335555e8109df60a00cadc76f7e13434b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800007"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="671d5-103">PreBindAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="671d5-103">PreBindAssemblyEx Function</span></span>

<span data-ttu-id="671d5-104">アセンブリのポリシー後の表示名を取得します。</span><span class="sxs-lookup"><span data-stu-id="671d5-104">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="671d5-105">この関数は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="671d5-105">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="671d5-106">構文</span><span class="sxs-lookup"><span data-stu-id="671d5-106">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="671d5-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="671d5-107">Parameters</span></span>  

 `pAppCtx`  
 <span data-ttu-id="671d5-108">からアプリケーションコンテキストを識別します。</span><span class="sxs-lookup"><span data-stu-id="671d5-108">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="671d5-109">からアセンブリ名を識別します。</span><span class="sxs-lookup"><span data-stu-id="671d5-109">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="671d5-110">から親アセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="671d5-110">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="671d5-111">このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="671d5-111">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="671d5-112">からランタイムのバージョンを識別します。</span><span class="sxs-lookup"><span data-stu-id="671d5-112">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="671d5-113">入出力ポリシー後の表示名を格納します。</span><span class="sxs-lookup"><span data-stu-id="671d5-113">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="671d5-114">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="671d5-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="671d5-115">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="671d5-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="671d5-116">解説</span><span class="sxs-lookup"><span data-stu-id="671d5-116">Remarks</span></span>  

 <span data-ttu-id="671d5-117">`ppNamePostPolicy`出力パラメーターは、関数が HRESULT FUSION_E_REF_DEF_MISMATCH を返す場合にのみ設定されます。</span><span class="sxs-lookup"><span data-stu-id="671d5-117">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="671d5-118">それ以外の場合は null です。</span><span class="sxs-lookup"><span data-stu-id="671d5-118">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="671d5-119">要件</span><span class="sxs-lookup"><span data-stu-id="671d5-119">Requirements</span></span>  

 <span data-ttu-id="671d5-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="671d5-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="671d5-121">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="671d5-121">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="671d5-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="671d5-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="671d5-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="671d5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671d5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="671d5-124">See also</span></span>

- [<span data-ttu-id="671d5-125">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="671d5-125">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
