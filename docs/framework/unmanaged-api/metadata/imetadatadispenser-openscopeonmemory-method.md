---
description: '詳細について: IMetaDataDispenser:: OpenScopeOnMemory メソッド'
title: IMetaDataDispenser::OpenScopeOnMemory メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 589c68ab60eec55efc43d077807789e75ae1682f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753589"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="2a87d-103">IMetaDataDispenser::OpenScopeOnMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="2a87d-103">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>

<span data-ttu-id="2a87d-104">既存のメタデータを含むメモリ領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="2a87d-104">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="2a87d-105">つまり、このメソッドは、既存のデータがメタデータとして扱われる、指定されたメモリ領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="2a87d-105">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a87d-106">構文</span><span class="sxs-lookup"><span data-stu-id="2a87d-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a87d-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2a87d-107">Parameters</span></span>  

 `pData`  
 <span data-ttu-id="2a87d-108">からメモリ領域の開始アドレスを指定するポインター。</span><span class="sxs-lookup"><span data-stu-id="2a87d-108">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="2a87d-109">からメモリ領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="2a87d-109">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="2a87d-110">から開くためのモード (読み取り、書き込みなど) を指定する [Coropenflags](coropenflags-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="2a87d-110">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="2a87d-111">から返される、必要なメタデータインターフェイスの IID。呼び出し元は、インターフェイスを使用して、メタデータのインポート (読み取り) または出力 (書き込み) を行います。</span><span class="sxs-lookup"><span data-stu-id="2a87d-111">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="2a87d-112">の値には `riid` 、"import" インターフェイスまたは "emit" インターフェイスのいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a87d-112">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="2a87d-113">有効な値は、IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2、または IID_IMetaDataImport2 です。</span><span class="sxs-lookup"><span data-stu-id="2a87d-113">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="2a87d-114">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2a87d-114">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a87d-115">解説</span><span class="sxs-lookup"><span data-stu-id="2a87d-115">Remarks</span></span>  

 <span data-ttu-id="2a87d-116">メタデータのメモリ内コピーは、"import" インターフェイスのいずれかのメソッドを使用してクエリを実行するか、"emit" インターフェイスのいずれかのメソッドを使用してに追加できます。</span><span class="sxs-lookup"><span data-stu-id="2a87d-116">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="2a87d-117">`OpenScopeOnMemory`メソッドは[IMetaDataDispenser:: openscope](imetadatadispenser-openscope-method.md)メソッドに似ていますが、対象のメタデータがディスク上のファイルではなくメモリに既に存在している点が異なります。</span><span class="sxs-lookup"><span data-stu-id="2a87d-117">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="2a87d-118">メモリのターゲット領域に共通言語ランタイム (CLR) メタデータが含まれていない場合、 `OpenScopeOnMemory` メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="2a87d-118">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a87d-119">要件</span><span class="sxs-lookup"><span data-stu-id="2a87d-119">Requirements</span></span>  

 <span data-ttu-id="2a87d-120">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a87d-120">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a87d-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="2a87d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a87d-122">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="2a87d-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2a87d-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a87d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a87d-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a87d-124">See also</span></span>

- [<span data-ttu-id="2a87d-125">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a87d-125">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="2a87d-126">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a87d-126">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="2a87d-127">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a87d-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="2a87d-128">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a87d-128">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="2a87d-129">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a87d-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2a87d-130">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a87d-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="2a87d-131">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a87d-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2a87d-132">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a87d-132">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
