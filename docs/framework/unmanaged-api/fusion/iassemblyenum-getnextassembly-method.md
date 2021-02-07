---
description: '詳細については、「IAssemblyEnum:: GetNextAssembly メソッド」を参照してください。'
title: IAssemblyEnum::GetNextAssembly メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
ms.openlocfilehash: 52b264b1d8efad54168a6bf69fd0c715cbfa7e2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760818"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="62ab9-103">IAssemblyEnum::GetNextAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="62ab9-103">IAssemblyEnum::GetNextAssembly Method</span></span>

<span data-ttu-id="62ab9-104">この[Iassemblyenum](iassemblyenum-interface.md)オブジェクトに格納されている次の[IAssemblyName](iassemblyname-interface.md)へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="62ab9-104">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ab9-105">構文</span><span class="sxs-lookup"><span data-stu-id="62ab9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62ab9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62ab9-106">Parameters</span></span>  

 `pvReserved`  
 <span data-ttu-id="62ab9-107">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="62ab9-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="62ab9-108">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="62ab9-108">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="62ab9-109">入出力返された `IAssemblyName` ポインター。</span><span class="sxs-lookup"><span data-stu-id="62ab9-109">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="62ab9-110">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="62ab9-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="62ab9-111">`dwFlags` 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="62ab9-111">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ab9-112">要件</span><span class="sxs-lookup"><span data-stu-id="62ab9-112">Requirements</span></span>  

 <span data-ttu-id="62ab9-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62ab9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ab9-114">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="62ab9-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="62ab9-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ab9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ab9-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="62ab9-116">See also</span></span>

- [<span data-ttu-id="62ab9-117">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62ab9-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="62ab9-118">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62ab9-118">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
