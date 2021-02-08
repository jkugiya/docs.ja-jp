---
description: '詳細について: IBindingDisplay:: GetCurrentDisplay メソッド'
title: IBindingDisplay::GetCurrentDisplay メソッド
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: 680a91c8025ac3247701c14c23f442da5e304ecb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800423"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="245e0-103">IBindingDisplay::GetCurrentDisplay メソッド</span><span class="sxs-lookup"><span data-stu-id="245e0-103">IBindingDisplay::GetCurrentDisplay Method</span></span>

<span data-ttu-id="245e0-104">現在のバインディング表示情報を返します。</span><span class="sxs-lookup"><span data-stu-id="245e0-104">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="245e0-105">構文</span><span class="sxs-lookup"><span data-stu-id="245e0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="245e0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="245e0-106">Parameters</span></span>  

 `display`  
 <span data-ttu-id="245e0-107">[out, retval]バインディング表示情報を格納している safearray へのポインター。</span><span class="sxs-lookup"><span data-stu-id="245e0-107">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="245e0-108">解説</span><span class="sxs-lookup"><span data-stu-id="245e0-108">Remarks</span></span>  

 <span data-ttu-id="245e0-109">[IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md)メソッドが既に成功しており、プログラムがデバッガーによって停止されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="245e0-109">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="245e0-110">呼び出し元は、SafeArrayDestroy を使用して、返されたメモリの割り当てを解除する必要があり `SAFEARRAY` ます。 [](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)</span><span class="sxs-lookup"><span data-stu-id="245e0-110">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="245e0-111">要件</span><span class="sxs-lookup"><span data-stu-id="245e0-111">Requirements</span></span>  

 <span data-ttu-id="245e0-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="245e0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="245e0-113">**ヘッダー:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="245e0-113">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="245e0-114">**ライブラリ:** BindingDisplay .idl</span><span class="sxs-lookup"><span data-stu-id="245e0-114">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="245e0-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="245e0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="245e0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="245e0-116">See also</span></span>

- [<span data-ttu-id="245e0-117">IBindingDisplay インターフェイス</span><span class="sxs-lookup"><span data-stu-id="245e0-117">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="245e0-118">InitializeForProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="245e0-118">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
