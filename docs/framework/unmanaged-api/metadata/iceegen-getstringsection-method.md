---
description: '詳細について: ICeeGen:: GetStringSection メソッド'
title: ICeeGen::GetStringSection メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
ms.openlocfilehash: ef4b4bb502e1099b9b3bcdbd494d03df0858aa6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721057"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="c48c0-103">ICeeGen::GetStringSection メソッド</span><span class="sxs-lookup"><span data-stu-id="c48c0-103">ICeeGen::GetStringSection Method</span></span>

<span data-ttu-id="c48c0-104">指定したハンドルによって参照されるコードセクションの文字列表現を取得します。</span><span class="sxs-lookup"><span data-stu-id="c48c0-104">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="c48c0-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c48c0-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c48c0-106">構文</span><span class="sxs-lookup"><span data-stu-id="c48c0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c48c0-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c48c0-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="c48c0-108">[入力、出力]コードセクションへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="c48c0-108">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c48c0-109">要件</span><span class="sxs-lookup"><span data-stu-id="c48c0-109">Requirements</span></span>  

 <span data-ttu-id="c48c0-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c48c0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c48c0-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c48c0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c48c0-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c48c0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c48c0-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c48c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c48c0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c48c0-114">See also</span></span>

- [<span data-ttu-id="c48c0-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c48c0-115">ICeeGen Interface</span></span>](iceegen-interface.md)
