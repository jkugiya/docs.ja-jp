---
description: '詳細について: IMetaDataEmit::D efinePinvokeMap メソッド'
title: IMetaDataEmit::DefinePinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: 7b0477ca603241e773a67f335da579daa2ed3d30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784068"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="4fcf0-103">IMetaDataEmit::DefinePinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="4fcf0-103">IMetaDataEmit::DefinePinvokeMap Method</span></span>

<span data-ttu-id="4fcf0-104">指定したトークンによって参照されるメソッドの PInvoke 署名の特徴を設定します。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-104">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fcf0-105">構文</span><span class="sxs-lookup"><span data-stu-id="4fcf0-105">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fcf0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4fcf0-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="4fcf0-107">からターゲットメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-107">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="4fcf0-108">からマッピングを行うために PInvoke によって使用されるフラグ。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-108">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="4fcf0-109">からアンマネージ DLL 内の対象のエクスポートメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-109">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="4fcf0-110">からターゲットのネイティブ DLL のトークン。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-110">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fcf0-111">要件</span><span class="sxs-lookup"><span data-stu-id="4fcf0-111">Requirements</span></span>  

 <span data-ttu-id="4fcf0-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fcf0-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4fcf0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fcf0-114">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fcf0-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fcf0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fcf0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fcf0-116">See also</span></span>

- [<span data-ttu-id="4fcf0-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4fcf0-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4fcf0-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4fcf0-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
