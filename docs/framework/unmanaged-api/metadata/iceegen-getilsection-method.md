---
description: '詳細について: ICeeGen:: GetIlSection メソッド'
title: ICeeGen::GetIlSection メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
ms.openlocfilehash: 44195ec55480279494620aed6db566f1c2308a6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707008"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="58339-103">ICeeGen::GetIlSection メソッド</span><span class="sxs-lookup"><span data-stu-id="58339-103">ICeeGen::GetIlSection Method</span></span>

<span data-ttu-id="58339-104">指定したハンドルによって参照される中間言語コードベースのセクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="58339-104">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="58339-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="58339-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58339-106">構文</span><span class="sxs-lookup"><span data-stu-id="58339-106">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58339-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="58339-107">Parameters</span></span>  

 `section`  
 <span data-ttu-id="58339-108">から取得するセクションへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="58339-108">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58339-109">要件</span><span class="sxs-lookup"><span data-stu-id="58339-109">Requirements</span></span>  

 <span data-ttu-id="58339-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58339-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58339-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="58339-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58339-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="58339-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58339-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58339-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58339-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="58339-114">See also</span></span>

- [<span data-ttu-id="58339-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58339-115">ICeeGen Interface</span></span>](iceegen-interface.md)
