---
description: '詳細情報: IInstallReferenceEnum インターフェイス'
title: IInstallReferenceEnum インターフェイス
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
ms.openlocfilehash: 496bd508b95b51cb23949f32f8390c7cb733b37e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800101"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="78a4b-103">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78a4b-103">IInstallReferenceEnum Interface</span></span>

<span data-ttu-id="78a4b-104">グローバルアセンブリキャッシュにインストールされている参照アセンブリの列挙子を表します。</span><span class="sxs-lookup"><span data-stu-id="78a4b-104">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a4b-105">構文</span><span class="sxs-lookup"><span data-stu-id="78a4b-105">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="78a4b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="78a4b-106">Methods</span></span>  
  
|<span data-ttu-id="78a4b-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="78a4b-107">Method</span></span>|<span data-ttu-id="78a4b-108">説明</span><span class="sxs-lookup"><span data-stu-id="78a4b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78a4b-109">GetNextInstallReferenceItem メソッド</span><span class="sxs-lookup"><span data-stu-id="78a4b-109">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="78a4b-110">このに格納されている次のへのポインターを取得し `IInstallReferenceItem` `IInstallReferenceEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="78a4b-110">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78a4b-111">要件</span><span class="sxs-lookup"><span data-stu-id="78a4b-111">Requirements</span></span>  

 <span data-ttu-id="78a4b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78a4b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78a4b-113">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="78a4b-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="78a4b-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78a4b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a4b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="78a4b-115">See also</span></span>

- [<span data-ttu-id="78a4b-116">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78a4b-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="78a4b-117">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78a4b-117">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
