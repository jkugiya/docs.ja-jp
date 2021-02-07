---
description: '詳細について: ICeeGen:: EmitString メソッド'
title: ICeeGen::EmitString メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
ms.openlocfilehash: fca388d044603f932bf90a176cada6e830284702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707112"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="74924-103">ICeeGen::EmitString メソッド</span><span class="sxs-lookup"><span data-stu-id="74924-103">ICeeGen::EmitString Method</span></span>

<span data-ttu-id="74924-104">指定した文字列をコードベースに出力します。</span><span class="sxs-lookup"><span data-stu-id="74924-104">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="74924-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="74924-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74924-106">構文</span><span class="sxs-lookup"><span data-stu-id="74924-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74924-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74924-107">Parameters</span></span>  

 `lpString`  
 <span data-ttu-id="74924-108">から出力する文字列。</span><span class="sxs-lookup"><span data-stu-id="74924-108">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="74924-109">入出力出力された文字列の相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="74924-109">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74924-110">要件</span><span class="sxs-lookup"><span data-stu-id="74924-110">Requirements</span></span>  

 <span data-ttu-id="74924-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74924-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74924-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="74924-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74924-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="74924-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74924-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74924-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74924-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="74924-115">See also</span></span>

- [<span data-ttu-id="74924-116">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74924-116">ICeeGen Interface</span></span>](iceegen-interface.md)
