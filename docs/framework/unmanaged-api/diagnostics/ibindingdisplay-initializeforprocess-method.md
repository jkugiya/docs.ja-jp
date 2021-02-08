---
description: '詳細について: IBindingDisplay:: InitializeForProcess メソッド'
title: IBindingDisplay::InitializeForProcess メソッド
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: cf7f0f4d057659089bd7da173e5fac98a7c00dad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800410"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="87a95-103">IBindingDisplay::InitializeForProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="87a95-103">IBindingDisplay::InitializeForProcess Method</span></span>

<span data-ttu-id="87a95-104">[IBindingDisplay](ibindingdisplay-interface.md)オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="87a95-104">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87a95-105">構文</span><span class="sxs-lookup"><span data-stu-id="87a95-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87a95-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87a95-106">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="87a95-107">からプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="87a95-107">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87a95-108">解説</span><span class="sxs-lookup"><span data-stu-id="87a95-108">Remarks</span></span>  

 <span data-ttu-id="87a95-109">デバッガーは、 `InitializeForProcess` 作成時にメソッドを呼び出して、バインド表示を初期化します。</span><span class="sxs-lookup"><span data-stu-id="87a95-109">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="87a95-110">`InitializeForProcess` の他のメソッドが呼び出される前に、作成時にを呼び出す必要があり `IBindingDisplay` ます。</span><span class="sxs-lookup"><span data-stu-id="87a95-110">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87a95-111">要件</span><span class="sxs-lookup"><span data-stu-id="87a95-111">Requirements</span></span>  

 <span data-ttu-id="87a95-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87a95-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87a95-113">**ヘッダー:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="87a95-113">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="87a95-114">**ライブラリ:** BindingDisplay .idl</span><span class="sxs-lookup"><span data-stu-id="87a95-114">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="87a95-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87a95-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a95-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="87a95-116">See also</span></span>

- [<span data-ttu-id="87a95-117">IBindingDisplay インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87a95-117">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
