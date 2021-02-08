---
description: '詳細について: IMetaDataEmit:: GetSaveSize メソッド'
title: IMetaDataEmit::GetSaveSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
ms.openlocfilehash: 871e9f911eaaf1b1a7259466402e492d75aa7fb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783938"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="e85be-103">IMetaDataEmit::GetSaveSize メソッド</span><span class="sxs-lookup"><span data-stu-id="e85be-103">IMetaDataEmit::GetSaveSize Method</span></span>

<span data-ttu-id="e85be-104">現在のスコープ内のアセンブリとそのメタデータの推定バイナリサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="e85be-104">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85be-105">構文</span><span class="sxs-lookup"><span data-stu-id="e85be-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e85be-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e85be-106">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="e85be-107">から正確またはおおよそのサイズを取得するかどうかを指定する [CorSaveSize](corsavesize-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="e85be-107">[in] A value of the [CorSaveSize](corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="e85be-108">有効な値は、cssAccurate、cssQuick、cssDiscardTransientCAs の3つだけです。</span><span class="sxs-lookup"><span data-stu-id="e85be-108">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="e85be-109">cssAccurate は正確な保存サイズを返しますが、計算にかかる時間は長くなります。</span><span class="sxs-lookup"><span data-stu-id="e85be-109">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="e85be-110">cssQuick は、サイズを返します。これは安全性のために埋め込まれていますが、計算にかかる時間は短くなります。</span><span class="sxs-lookup"><span data-stu-id="e85be-110">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="e85be-111">cssDiscardTransientCAs `GetSaveSize` は、破棄可能なカスタム属性を破棄できることを示します。</span><span class="sxs-lookup"><span data-stu-id="e85be-111">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="e85be-112">入出力ファイルを保存するために必要なサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e85be-112">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e85be-113">解説</span><span class="sxs-lookup"><span data-stu-id="e85be-113">Remarks</span></span>  

 <span data-ttu-id="e85be-114">`GetSaveSize` 現在のスコープ内のアセンブリとそのすべてのメタデータを保存するために必要な領域をバイト単位で計算します。</span><span class="sxs-lookup"><span data-stu-id="e85be-114">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="e85be-115">( [IMetaDataEmit:: SaveToStream](imetadataemit-savetostream-method.md) メソッドを呼び出すと、このバイト数が出力されます)。</span><span class="sxs-lookup"><span data-stu-id="e85be-115">(A call to the [IMetaDataEmit::SaveToStream](imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="e85be-116">呼び出し元が [IMapToken](imaptoken-interface.md) インターフェイス ( [IMetaDataEmit:: SetHandler](imetadataemit-sethandler-method.md) または [IMetaDataEmit:: Merge](imetadataemit-merge-method.md)) を実装している場合、 `GetSaveSize` はメタデータに対して2つのパスを実行し、最適化および圧縮します。</span><span class="sxs-lookup"><span data-stu-id="e85be-116">If the caller implements the [IMapToken](imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="e85be-117">それ以外の場合、最適化は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e85be-117">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="e85be-118">最適化が実行された場合、最初のパスは単にメタデータ構造を並べ替えて、インポート時の検索のパフォーマンスを調整します。</span><span class="sxs-lookup"><span data-stu-id="e85be-118">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="e85be-119">この手順では、通常、後で参照するためにツールによって保持されているトークンが無効になるという副作用で、レコードを移動します。</span><span class="sxs-lookup"><span data-stu-id="e85be-119">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="e85be-120">ただし、メタデータは、2番目のパスの後に、これらのトークンの変更を呼び出し元に通知しません。</span><span class="sxs-lookup"><span data-stu-id="e85be-120">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="e85be-121">2番目のパスでは、 `mdTypeRef` `mdMemberRef` 現在のメタデータスコープ内で宣言されている型またはメンバーへの参照である場合に、メタデータの全体的なサイズを減らす (事前バインディング)、トークンなどのさまざまな最適化が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e85be-121">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="e85be-122">このパスでは、別のトークンマッピングのラウンドが発生します。</span><span class="sxs-lookup"><span data-stu-id="e85be-122">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="e85be-123">このパスが経過すると、メタデータエンジンは、 `IMapToken` 変更されたトークン値のインターフェイスを介して呼び出し元に通知します。</span><span class="sxs-lookup"><span data-stu-id="e85be-123">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e85be-124">要件</span><span class="sxs-lookup"><span data-stu-id="e85be-124">Requirements</span></span>  

 <span data-ttu-id="e85be-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e85be-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e85be-126">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e85be-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e85be-127">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e85be-127">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e85be-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e85be-128">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85be-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="e85be-129">See also</span></span>

- [<span data-ttu-id="e85be-130">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e85be-130">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e85be-131">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e85be-131">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
