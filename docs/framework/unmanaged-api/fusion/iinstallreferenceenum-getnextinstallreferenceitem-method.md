---
description: '詳細については、「IInstallReferenceEnum:: GetNextInstallReferenceItem メソッド」を参照してください。'
title: IInstallReferenceEnum::GetNextInstallReferenceItem メソッド
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
ms.openlocfilehash: d410407fe16a46b45786ff74f694aaa8931be542
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800120"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="0597e-103">IInstallReferenceEnum::GetNextInstallReferenceItem メソッド</span><span class="sxs-lookup"><span data-stu-id="0597e-103">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>

<span data-ttu-id="0597e-104">この[Iinstallreferenceitem](iinstallreferenceenum-interface.md)オブジェクトに格納されている次の[Iinstallreferenceitem](iinstallreferenceitem-interface.md)オブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0597e-104">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0597e-105">構文</span><span class="sxs-lookup"><span data-stu-id="0597e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0597e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0597e-106">Parameters</span></span>  

 `ppRefItem`  
 <span data-ttu-id="0597e-107">入出力返された `IInstallReferenceItem` ポインター。</span><span class="sxs-lookup"><span data-stu-id="0597e-107">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0597e-108">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="0597e-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="0597e-109">`dwFlags` 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0597e-109">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="0597e-110">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="0597e-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="0597e-111">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0597e-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0597e-112">要件</span><span class="sxs-lookup"><span data-stu-id="0597e-112">Requirements</span></span>  

 <span data-ttu-id="0597e-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0597e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0597e-114">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0597e-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0597e-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0597e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0597e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0597e-116">See also</span></span>

- [<span data-ttu-id="0597e-117">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0597e-117">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="0597e-118">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0597e-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
