---
description: '詳細について: ICeeGen:: GetString メソッド'
title: ICeeGen::GetString メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: 227b4badff3265fc22f1c76301ba03e58fea34c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706891"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="a42a9-103">ICeeGen::GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="a42a9-103">ICeeGen::GetString Method</span></span>

<span data-ttu-id="a42a9-104">指定した相対仮想アドレスに格納されている文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="a42a9-104">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="a42a9-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a42a9-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a42a9-106">構文</span><span class="sxs-lookup"><span data-stu-id="a42a9-106">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a42a9-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a42a9-107">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="a42a9-108">から返される文字列の相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="a42a9-108">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="a42a9-109">入出力返された文字列。</span><span class="sxs-lookup"><span data-stu-id="a42a9-109">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a42a9-110">要件</span><span class="sxs-lookup"><span data-stu-id="a42a9-110">Requirements</span></span>  

 <span data-ttu-id="a42a9-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a42a9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a42a9-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a42a9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a42a9-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="a42a9-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a42a9-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a42a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a42a9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a42a9-115">See also</span></span>

- [<span data-ttu-id="a42a9-116">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a42a9-116">ICeeGen Interface</span></span>](iceegen-interface.md)
