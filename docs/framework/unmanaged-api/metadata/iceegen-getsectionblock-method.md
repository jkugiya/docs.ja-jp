---
description: '詳細について: ICeeGen:: GetSectionBlock メソッド'
title: ICeeGen::GetSectionBlock メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: d1a9fdeb35507f9dd6528b581be877049d2a1478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721113"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="98815-103">ICeeGen::GetSectionBlock メソッド</span><span class="sxs-lookup"><span data-stu-id="98815-103">ICeeGen::GetSectionBlock Method</span></span>

<span data-ttu-id="98815-104">コードベースのセクションブロックを取得します。</span><span class="sxs-lookup"><span data-stu-id="98815-104">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="98815-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="98815-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98815-106">構文</span><span class="sxs-lookup"><span data-stu-id="98815-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="98815-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98815-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="98815-108">からコードベースのブロックを取得する対象となるセクション。</span><span class="sxs-lookup"><span data-stu-id="98815-108">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="98815-109">から取得するブロックの長さ。</span><span class="sxs-lookup"><span data-stu-id="98815-109">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="98815-110">からブロックの最初のバイトを揃えるために使用する、セクションの先頭を基準とするバイト。</span><span class="sxs-lookup"><span data-stu-id="98815-110">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="98815-111">これは、セクション内のブロックの位置です。</span><span class="sxs-lookup"><span data-stu-id="98815-111">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="98815-112">入出力取得されたブロックのアドレスを受け取る場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="98815-112">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98815-113">解説</span><span class="sxs-lookup"><span data-stu-id="98815-113">Remarks</span></span>  

 <span data-ttu-id="98815-114">`GetSectionBlock`他のメソッドによって処理されない特殊なセクション要件がある場合にのみ、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="98815-114">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98815-115">要件</span><span class="sxs-lookup"><span data-stu-id="98815-115">Requirements</span></span>  

 <span data-ttu-id="98815-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98815-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98815-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="98815-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98815-118">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="98815-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98815-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98815-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98815-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="98815-120">See also</span></span>

- [<span data-ttu-id="98815-121">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98815-121">ICeeGen Interface</span></span>](iceegen-interface.md)
