---
description: '詳細情報: IInstallReferenceItem:: GetReference メソッド'
title: IInstallReferenceItem::GetReference メソッド
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
ms.openlocfilehash: 88f5ca21b6f3494031e1cd232f71253e39d9e648
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800115"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="f44e5-103">IInstallReferenceItem::GetReference メソッド</span><span class="sxs-lookup"><span data-stu-id="f44e5-103">IInstallReferenceItem::GetReference Method</span></span>

<span data-ttu-id="f44e5-104">この[Iinstallreferenceitem](iinstallreferenceitem-interface.md)オブジェクトによって表される[FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md)構造体へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f44e5-104">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f44e5-105">構文</span><span class="sxs-lookup"><span data-stu-id="f44e5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f44e5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f44e5-106">Parameters</span></span>  

 `ppRefData`  
 <span data-ttu-id="f44e5-107">入出力返された `FUSION_INSTALL_REFERENCE` ポインター。</span><span class="sxs-lookup"><span data-stu-id="f44e5-107">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f44e5-108">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="f44e5-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f44e5-109">`dwFlags` 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f44e5-109">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f44e5-110">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="f44e5-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f44e5-111">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f44e5-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f44e5-112">要件</span><span class="sxs-lookup"><span data-stu-id="f44e5-112">Requirements</span></span>  

 <span data-ttu-id="f44e5-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f44e5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f44e5-114">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f44e5-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f44e5-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f44e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f44e5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f44e5-116">See also</span></span>

- [<span data-ttu-id="f44e5-117">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f44e5-117">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="f44e5-118">FUSION_INSTALL_REFERENCE 構造体</span><span class="sxs-lookup"><span data-stu-id="f44e5-118">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)
