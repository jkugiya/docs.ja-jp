---
description: '詳細について: ICeeGen:: GenerateCeeMemoryImage メソッド'
title: ICeeGen::GenerateCeeMemoryImage メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GenerateCeeMemoryImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GenerateCeeMemoryImage
helpviewer_keywords:
- ICeeGen::GenerateCeeMemoryImage method [.NET Framework metadata]
- GenerateCeeMemoryImage method [.NET Framework metadata]
ms.assetid: b3847495-0ae6-4a72-b496-65ce2424afc6
topic_type:
- apiref
ms.openlocfilehash: 08361454171b1c3ad3879399f9499921738c106a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707086"
---
# <a name="iceegengenerateceememoryimage-method"></a><span data-ttu-id="fb131-103">ICeeGen::GenerateCeeMemoryImage メソッド</span><span class="sxs-lookup"><span data-stu-id="fb131-103">ICeeGen::GenerateCeeMemoryImage Method</span></span>

<span data-ttu-id="fb131-104">コードベースのイメージをメモリ内に生成します。</span><span class="sxs-lookup"><span data-stu-id="fb131-104">Generates an image in memory for the code base.</span></span>  
  
 <span data-ttu-id="fb131-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="fb131-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb131-106">構文</span><span class="sxs-lookup"><span data-stu-id="fb131-106">Syntax</span></span>  
  
```cpp  
HRESULT GenerateCeeMemoryImage (  
    [out] void    **ppImage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb131-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb131-107">Parameters</span></span>  

 `ppImage`  
 <span data-ttu-id="fb131-108">入出力生成されたイメージへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fb131-108">[out] A pointer to the generated image.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb131-109">要件</span><span class="sxs-lookup"><span data-stu-id="fb131-109">Requirements</span></span>  

 <span data-ttu-id="fb131-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb131-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb131-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="fb131-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb131-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="fb131-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb131-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb131-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb131-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb131-114">See also</span></span>

- [<span data-ttu-id="fb131-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb131-115">ICeeGen Interface</span></span>](iceegen-interface.md)
