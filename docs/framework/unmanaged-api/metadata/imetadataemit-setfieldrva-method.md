---
description: '詳細について: IMetaDataEmit:: SetFieldRVA メソッド'
title: IMetaDataEmit::SetFieldRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: 5d78880b892dc948337aa1ec1a471a5d380f1e2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657932"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="e8b7b-103">IMetaDataEmit::SetFieldRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="e8b7b-103">IMetaDataEmit::SetFieldRVA Method</span></span>

<span data-ttu-id="e8b7b-104">指定したトークンによって参照されるフィールドの相対仮想アドレスのグローバル変数値を設定します。</span><span class="sxs-lookup"><span data-stu-id="e8b7b-104">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b7b-105">構文</span><span class="sxs-lookup"><span data-stu-id="e8b7b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8b7b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e8b7b-106">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="e8b7b-107">からターゲットフィールドのトークン。</span><span class="sxs-lookup"><span data-stu-id="e8b7b-107">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="e8b7b-108">からコードまたはデータ領域のアドレス。</span><span class="sxs-lookup"><span data-stu-id="e8b7b-108">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8b7b-109">要件</span><span class="sxs-lookup"><span data-stu-id="e8b7b-109">Requirements</span></span>  

 <span data-ttu-id="e8b7b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8b7b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8b7b-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e8b7b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8b7b-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8b7b-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8b7b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8b7b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b7b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8b7b-114">See also</span></span>

- [<span data-ttu-id="e8b7b-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8b7b-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e8b7b-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8b7b-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
