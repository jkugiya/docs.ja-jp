---
description: '詳細について: ICeeGen:: TruncateSection メソッド'
title: ICeeGen::TruncateSection メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
ms.openlocfilehash: 074c7d7b4222b5b22f1d9b79169d531cd5544b1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784211"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="485be-103">ICeeGen::TruncateSection メソッド</span><span class="sxs-lookup"><span data-stu-id="485be-103">ICeeGen::TruncateSection Method</span></span>

<span data-ttu-id="485be-104">指定したコードセクションを指定した長さだけ切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="485be-104">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="485be-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="485be-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="485be-106">構文</span><span class="sxs-lookup"><span data-stu-id="485be-106">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="485be-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="485be-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="485be-108">から切り捨てるセクション。</span><span class="sxs-lookup"><span data-stu-id="485be-108">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="485be-109">からセクションを切り捨てる長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="485be-109">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="485be-110">解説</span><span class="sxs-lookup"><span data-stu-id="485be-110">Remarks</span></span>  

 <span data-ttu-id="485be-111">`TruncateSection`他のメソッドによって処理されない特殊なセクション要件がある場合にのみ、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="485be-111">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="485be-112">要件</span><span class="sxs-lookup"><span data-stu-id="485be-112">Requirements</span></span>  

 <span data-ttu-id="485be-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="485be-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="485be-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="485be-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="485be-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="485be-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="485be-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="485be-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="485be-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="485be-117">See also</span></span>

- [<span data-ttu-id="485be-118">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="485be-118">ICeeGen Interface</span></span>](iceegen-interface.md)
