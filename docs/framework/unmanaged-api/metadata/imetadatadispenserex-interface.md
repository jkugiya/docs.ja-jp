---
description: 詳細については、「IMetaDataDispenserEx インターフェイス」を参照してください。
title: IMetaDataDispenserEx インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: d940ac20eaad4b930ab17fb2d194d3b03bd4cf3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753537"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="21e57-103">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21e57-103">IMetaDataDispenserEx Interface</span></span>

<span data-ttu-id="21e57-104">[IMetaDataDispenser インターフェイス](imetadatadispenser-interface.md)インターフェイスを拡張して、メタデータ api が現在のメタデータスコープに対してどのように動作するかを制御する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="21e57-104">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21e57-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="21e57-105">Methods</span></span>  
  
|<span data-ttu-id="21e57-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="21e57-106">Method</span></span>|<span data-ttu-id="21e57-107">説明</span><span class="sxs-lookup"><span data-stu-id="21e57-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21e57-108">FindAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="21e57-108">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="21e57-109">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="21e57-109">This method is not implemented.</span></span> <span data-ttu-id="21e57-110">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="21e57-110">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="21e57-111">FindAssemblyModule メソッド</span><span class="sxs-lookup"><span data-stu-id="21e57-111">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="21e57-112">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="21e57-112">This method is not implemented.</span></span> <span data-ttu-id="21e57-113">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="21e57-113">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="21e57-114">GetCORSystemDirectory メソッド</span><span class="sxs-lookup"><span data-stu-id="21e57-114">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="21e57-115">現在の共通言語ランタイム (CLR) が格納されているディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="21e57-115">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="21e57-116">このメソッドは、アウトプロセスデバッガーでの使用に対してのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="21e57-116">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="21e57-117">別のコンポーネントから呼び出された場合は、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="21e57-117">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="21e57-118">GetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="21e57-118">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="21e57-119">現在のメタデータスコープの指定したオプションの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="21e57-119">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="21e57-120">オプションは、現在のメタデータスコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="21e57-120">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="21e57-121">OpenScopeOnITypeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="21e57-121">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="21e57-122">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="21e57-122">This method is not implemented.</span></span> <span data-ttu-id="21e57-123">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="21e57-123">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="21e57-124">SetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="21e57-124">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="21e57-125">指定されたオプションを、現在のメタデータスコープの指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="21e57-125">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="21e57-126">オプションは、現在のメタデータスコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="21e57-126">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21e57-127">要件</span><span class="sxs-lookup"><span data-stu-id="21e57-127">Requirements</span></span>  

 <span data-ttu-id="21e57-128">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21e57-128">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e57-129">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="21e57-129">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21e57-130">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="21e57-130">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21e57-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e57-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e57-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="21e57-132">See also</span></span>

- [<span data-ttu-id="21e57-133">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21e57-133">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="21e57-134">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21e57-134">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="21e57-135">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21e57-135">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="21e57-136">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21e57-136">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
