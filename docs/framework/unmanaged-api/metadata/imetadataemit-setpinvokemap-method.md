---
description: '詳細について: IMetaDataEmit:: SetPinvokeMap メソッド'
title: IMetaDataEmit::SetPinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: e50f06385b599a99454da0a9b971b00806d3140a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771848"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="cc68b-103">IMetaDataEmit::SetPinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="cc68b-103">IMetaDataEmit::SetPinvokeMap Method</span></span>

<span data-ttu-id="cc68b-104">[IMetaDataEmit::D efinepinvokemap](imetadataemit-definepinvokemap-method.md)の前の呼び出しで定義されているように、メソッドの PInvoke 署名の機能を設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="cc68b-104">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc68b-105">構文</span><span class="sxs-lookup"><span data-stu-id="cc68b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc68b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc68b-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="cc68b-107">から `mdToken` マッピング情報が適用される。</span><span class="sxs-lookup"><span data-stu-id="cc68b-107">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="cc68b-108">からマッピングを行うために PInvoke によって使用されるフラグ。</span><span class="sxs-lookup"><span data-stu-id="cc68b-108">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="cc68b-109">これは、値のビットマスクです `CorPinvokeMap` 。</span><span class="sxs-lookup"><span data-stu-id="cc68b-109">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="cc68b-110">からネイティブ DLL 内のターゲットエクスポートの名前。</span><span class="sxs-lookup"><span data-stu-id="cc68b-110">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="cc68b-111">から `mdModuleRef` ターゲットのアンマネージ DLL のトークン。</span><span class="sxs-lookup"><span data-stu-id="cc68b-111">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc68b-112">要件</span><span class="sxs-lookup"><span data-stu-id="cc68b-112">Requirements</span></span>  

 <span data-ttu-id="cc68b-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc68b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc68b-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="cc68b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc68b-115">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc68b-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc68b-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc68b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc68b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc68b-117">See also</span></span>

- [<span data-ttu-id="cc68b-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc68b-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="cc68b-119">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc68b-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
