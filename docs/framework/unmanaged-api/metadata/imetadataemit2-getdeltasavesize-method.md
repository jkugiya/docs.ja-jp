---
description: '詳細について: IMetaDataEmit2:: GetDeltaSaveSize メソッド'
title: IMetaDataEmit2::GetDeltaSaveSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: d7b5eae7f89a5465876083c5cc8021330d3c59de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745763"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="683d1-103">IMetaDataEmit2::GetDeltaSaveSize メソッド</span><span class="sxs-lookup"><span data-stu-id="683d1-103">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>

<span data-ttu-id="683d1-104">現在のエディットコンティニュセッションの結果として得られるメタデータサイズの変更を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="683d1-104">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="683d1-105">構文</span><span class="sxs-lookup"><span data-stu-id="683d1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="683d1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="683d1-106">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="683d1-107">から [CorSaveSize](corsavesize-enumeration.md) 値の1つ。必要な精度のレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="683d1-107">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="683d1-108">.NET Framework バージョン2.0 では、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="683d1-108">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="683d1-109">入出力メタデータのサイズの変更。</span><span class="sxs-lookup"><span data-stu-id="683d1-109">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="683d1-110">要件</span><span class="sxs-lookup"><span data-stu-id="683d1-110">Requirements</span></span>  

 <span data-ttu-id="683d1-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="683d1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="683d1-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="683d1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="683d1-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="683d1-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="683d1-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="683d1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="683d1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="683d1-115">See also</span></span>

- [<span data-ttu-id="683d1-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="683d1-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="683d1-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="683d1-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
