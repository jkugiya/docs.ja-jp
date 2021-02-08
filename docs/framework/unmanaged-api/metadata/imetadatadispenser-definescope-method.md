---
description: '詳細について: IMetaDataDispenser::D efineScope メソッド'
title: IMetaDataDispenser::DefineScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: b7a7870ec06af4c08a4ef3609077eb93f74da776
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789243"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="2cb03-103">IMetaDataDispenser::DefineScope メソッド</span><span class="sxs-lookup"><span data-stu-id="2cb03-103">IMetaDataDispenser::DefineScope Method</span></span>

<span data-ttu-id="2cb03-104">新しいメタデータを作成できる新しい領域をメモリ内に作成します。</span><span class="sxs-lookup"><span data-stu-id="2cb03-104">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb03-105">構文</span><span class="sxs-lookup"><span data-stu-id="2cb03-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cb03-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2cb03-106">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="2cb03-107">から作成されるメタデータ構造のバージョンの CLSID。</span><span class="sxs-lookup"><span data-stu-id="2cb03-107">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="2cb03-108">この値は、.NET Framework バージョン2.0 の CLSID_CorMetaDataRuntime である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cb03-108">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="2cb03-109">からオプションを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="2cb03-109">[in] Flags that specify options.</span></span> <span data-ttu-id="2cb03-110">.NET Framework 2.0 の場合、この値は0である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cb03-110">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="2cb03-111">から返される、必要なメタデータインターフェイスの IID。呼び出し元は、インターフェイスを使用して新しいメタデータを作成します。</span><span class="sxs-lookup"><span data-stu-id="2cb03-111">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="2cb03-112">の値には `riid` 、"emit" インターフェイスのいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cb03-112">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="2cb03-113">有効な値は、IID_IMetaDataEmit、IID_IMetaDataAssemblyEmit、または IID_IMetaDataEmit2 です。</span><span class="sxs-lookup"><span data-stu-id="2cb03-113">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="2cb03-114">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2cb03-114">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb03-115">解説</span><span class="sxs-lookup"><span data-stu-id="2cb03-115">Remarks</span></span>  

 <span data-ttu-id="2cb03-116">`DefineScope` メモリ内メタデータテーブルのセットを作成し、メタデータの一意の GUID (モジュールバージョン識別子または MVID) を生成し、出力されるコンパイル単位のエントリをモジュールテーブルに作成します。</span><span class="sxs-lookup"><span data-stu-id="2cb03-116">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="2cb03-117">必要に応じて、 [IMetaDataEmit:: SetModuleProps](imetadataemit-setmoduleprops-method.md) または [IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md) メソッドを使用して、メタデータスコープ全体に属性をアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="2cb03-117">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cb03-118">要件</span><span class="sxs-lookup"><span data-stu-id="2cb03-118">Requirements</span></span>  

 <span data-ttu-id="2cb03-119">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb03-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cb03-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="2cb03-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2cb03-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="2cb03-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2cb03-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cb03-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb03-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cb03-123">See also</span></span>

- [<span data-ttu-id="2cb03-124">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cb03-124">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="2cb03-125">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cb03-125">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="2cb03-126">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cb03-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="2cb03-127">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cb03-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2cb03-128">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cb03-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
