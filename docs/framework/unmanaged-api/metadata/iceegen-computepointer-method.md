---
description: '詳細について: ICeeGen:: ComputePointer メソッド'
title: ICeeGen::ComputePointer メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
ms.openlocfilehash: 9319343cc93eae3e4c7b060239d23ad8aeb7d3e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721178"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="66cb8-103">ICeeGen::ComputePointer メソッド</span><span class="sxs-lookup"><span data-stu-id="66cb8-103">ICeeGen::ComputePointer Method</span></span>

<span data-ttu-id="66cb8-104">指定されたコードセクションのバッファーを決定します。</span><span class="sxs-lookup"><span data-stu-id="66cb8-104">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="66cb8-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="66cb8-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66cb8-106">構文</span><span class="sxs-lookup"><span data-stu-id="66cb8-106">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66cb8-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66cb8-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="66cb8-108">からバッファーを返す対象のコードセクション。</span><span class="sxs-lookup"><span data-stu-id="66cb8-108">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="66cb8-109">からポインターを取得するメソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="66cb8-109">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="66cb8-110">入出力返されたバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="66cb8-110">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66cb8-111">要件</span><span class="sxs-lookup"><span data-stu-id="66cb8-111">Requirements</span></span>  

 <span data-ttu-id="66cb8-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66cb8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66cb8-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="66cb8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66cb8-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="66cb8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66cb8-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66cb8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66cb8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="66cb8-116">See also</span></span>

- [<span data-ttu-id="66cb8-117">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66cb8-117">ICeeGen Interface</span></span>](iceegen-interface.md)
