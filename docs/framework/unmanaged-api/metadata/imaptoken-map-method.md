---
description: '詳細情報: IMapToken:: Map メソッド'
title: IMapToken::Map メソッド
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: da78f22e944a0e4ec25adcd7cdf97b69131a6612
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706735"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="3e4f1-103">IMapToken::Map メソッド</span><span class="sxs-lookup"><span data-stu-id="3e4f1-103">IMapToken::Map Method</span></span>

<span data-ttu-id="3e4f1-104">メタデータシグネチャを使用して、アセンブリ間のリレーションシップをマップします。</span><span class="sxs-lookup"><span data-stu-id="3e4f1-104">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e4f1-105">構文</span><span class="sxs-lookup"><span data-stu-id="3e4f1-105">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e4f1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e4f1-106">Parameters</span></span>  

 `tkImp`  
 <span data-ttu-id="3e4f1-107">からインポートされたコードオブジェクトを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="3e4f1-107">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="3e4f1-108">から出力されたコードオブジェクトを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="3e4f1-108">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e4f1-109">解説</span><span class="sxs-lookup"><span data-stu-id="3e4f1-109">Remarks</span></span>  

 <span data-ttu-id="3e4f1-110">マージ中にトークンの再マップが行われると、元のトークンはインポートされた (ソース) メタデータスコープ内でスコープが設定され、新しいトークンのスコープは、出力された (ターゲット) メタデータスコープに設定されます。</span><span class="sxs-lookup"><span data-stu-id="3e4f1-110">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e4f1-111">要件</span><span class="sxs-lookup"><span data-stu-id="3e4f1-111">Requirements</span></span>  

 <span data-ttu-id="3e4f1-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e4f1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e4f1-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3e4f1-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e4f1-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="3e4f1-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e4f1-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e4f1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e4f1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e4f1-116">See also</span></span>

- [<span data-ttu-id="3e4f1-117">IMapToken インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e4f1-117">IMapToken Interface</span></span>](imaptoken-interface.md)
