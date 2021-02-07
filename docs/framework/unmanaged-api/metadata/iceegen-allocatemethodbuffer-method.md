---
description: '詳細について: ICeeGen:: AllocateMethodBuffer メソッド'
title: ICeeGen::AllocateMethodBuffer メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: ced5ac8b4fdd89fc41c2c70b68c5b49843a519e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707151"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="51158-103">ICeeGen::AllocateMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="51158-103">ICeeGen::AllocateMethodBuffer Method</span></span>

<span data-ttu-id="51158-104">メソッドに対して指定したサイズのバッファーを作成し、メソッドの相対仮想アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="51158-104">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="51158-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="51158-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51158-106">構文</span><span class="sxs-lookup"><span data-stu-id="51158-106">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51158-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="51158-107">Parameters</span></span>  

 `cchBuffer`  
 <span data-ttu-id="51158-108">から作成するバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="51158-108">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="51158-109">入出力返されたバッファー。</span><span class="sxs-lookup"><span data-stu-id="51158-109">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="51158-110">入出力メソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="51158-110">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51158-111">要件</span><span class="sxs-lookup"><span data-stu-id="51158-111">Requirements</span></span>  

 <span data-ttu-id="51158-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51158-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51158-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="51158-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51158-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="51158-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51158-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51158-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51158-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="51158-116">See also</span></span>

- [<span data-ttu-id="51158-117">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51158-117">ICeeGen Interface</span></span>](iceegen-interface.md)
