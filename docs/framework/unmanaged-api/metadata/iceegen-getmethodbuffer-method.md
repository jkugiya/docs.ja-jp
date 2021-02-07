---
description: '詳細について: ICeeGen:: GetMethodBuffer メソッド'
title: ICeeGen::GetMethodBuffer メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: 24811f231b1db6d985753d4f4695f432aa12edc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706930"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="fc82c-103">ICeeGen::GetMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="fc82c-103">ICeeGen::GetMethodBuffer Method</span></span>

<span data-ttu-id="fc82c-104">指定した相対仮想アドレスで、メソッドの適切なサイズのバッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="fc82c-104">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="fc82c-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc82c-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc82c-106">構文</span><span class="sxs-lookup"><span data-stu-id="fc82c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc82c-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc82c-107">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="fc82c-108">からバッファーを返すメソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="fc82c-108">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="fc82c-109">入出力返されたバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fc82c-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc82c-110">要件</span><span class="sxs-lookup"><span data-stu-id="fc82c-110">Requirements</span></span>  

 <span data-ttu-id="fc82c-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc82c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc82c-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="fc82c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc82c-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="fc82c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc82c-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc82c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc82c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc82c-115">See also</span></span>

- [<span data-ttu-id="fc82c-116">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc82c-116">ICeeGen Interface</span></span>](iceegen-interface.md)
