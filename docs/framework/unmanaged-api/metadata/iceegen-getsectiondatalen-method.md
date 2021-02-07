---
description: '詳細について: ICeeGen:: GetSectionDataLen メソッド'
title: ICeeGen::GetSectionDataLen メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: 9475112a6f25e9a4c57c4ded6cd11dab9bf352b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721054"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="9118b-103">ICeeGen::GetSectionDataLen メソッド</span><span class="sxs-lookup"><span data-stu-id="9118b-103">ICeeGen::GetSectionDataLen Method</span></span>

<span data-ttu-id="9118b-104">指定したセクションの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="9118b-104">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="9118b-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9118b-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9118b-106">構文</span><span class="sxs-lookup"><span data-stu-id="9118b-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9118b-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9118b-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="9118b-108">から長さを取得するデータセクション。</span><span class="sxs-lookup"><span data-stu-id="9118b-108">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="9118b-109">入出力指定したセクションの返された長さ。</span><span class="sxs-lookup"><span data-stu-id="9118b-109">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9118b-110">解説</span><span class="sxs-lookup"><span data-stu-id="9118b-110">Remarks</span></span>  

 <span data-ttu-id="9118b-111">`GetSectionDataLen`他のメソッドによって処理されない特殊なセクション要件がある場合にのみ、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9118b-111">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9118b-112">要件</span><span class="sxs-lookup"><span data-stu-id="9118b-112">Requirements</span></span>  

 <span data-ttu-id="9118b-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9118b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9118b-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9118b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9118b-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="9118b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9118b-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9118b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9118b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9118b-117">See also</span></span>

- [<span data-ttu-id="9118b-118">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9118b-118">ICeeGen Interface</span></span>](iceegen-interface.md)
