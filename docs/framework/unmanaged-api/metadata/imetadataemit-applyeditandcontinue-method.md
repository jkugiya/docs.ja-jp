---
description: '詳細について: IMetaDataEmit:: ApplyEditAndContinue メソッド'
title: IMetaDataEmit::ApplyEditAndContinue メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: 46454c4141aa220b43820307c86765a1827251df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753498"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="7df80-103">IMetaDataEmit::ApplyEditAndContinue メソッド</span><span class="sxs-lookup"><span data-stu-id="7df80-103">IMetaDataEmit::ApplyEditAndContinue Method</span></span>

<span data-ttu-id="7df80-104">指定したメタデータに加えられた変更を使用して、現在のアセンブリスコープを更新します。</span><span class="sxs-lookup"><span data-stu-id="7df80-104">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df80-105">構文</span><span class="sxs-lookup"><span data-stu-id="7df80-105">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7df80-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7df80-106">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="7df80-107">\[\]ポータブル実行可能 (PE) ファイルからのデルタメタデータを表す[IUnknown](/cpp/atl/iunknown)オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7df80-107">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="7df80-108">差分メタデータは、モジュールの実際のメタデータのコピーに加えられた変更を含むメタデータのブロックです。</span><span class="sxs-lookup"><span data-stu-id="7df80-108">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7df80-109">要件</span><span class="sxs-lookup"><span data-stu-id="7df80-109">Requirements</span></span>  

 <span data-ttu-id="7df80-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7df80-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7df80-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7df80-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7df80-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="7df80-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7df80-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7df80-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df80-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7df80-114">See also</span></span>

- [<span data-ttu-id="7df80-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7df80-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7df80-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7df80-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
