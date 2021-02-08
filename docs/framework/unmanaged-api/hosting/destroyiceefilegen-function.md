---
description: '詳細情報: DestroyICeeFileGen 関数'
title: DestroyICeeFileGen 関数
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: 14ae990999247b90f16b10115dea3408b965a04a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785654"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="5ff18-103">DestroyICeeFileGen 関数</span><span class="sxs-lookup"><span data-stu-id="5ff18-103">DestroyICeeFileGen Function</span></span>

<span data-ttu-id="5ff18-104">[ICeeFileGen](iceefilegen-class.md)オブジェクトを破棄します。</span><span class="sxs-lookup"><span data-stu-id="5ff18-104">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="5ff18-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="5ff18-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff18-106">構文</span><span class="sxs-lookup"><span data-stu-id="5ff18-106">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ff18-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ff18-107">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="5ff18-108">から `ICeeFileGen` 破棄するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5ff18-108">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ff18-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5ff18-109">Return Value</span></span>  

 <span data-ttu-id="5ff18-110">このメソッドは、標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="5ff18-110">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ff18-111">解説</span><span class="sxs-lookup"><span data-stu-id="5ff18-111">Remarks</span></span>  

 <span data-ttu-id="5ff18-112">`DestroyICeeFileGen``ICeeFileGen` [CreateICeeFileGen](createiceefilegen-function.md)関数によって作成されたオブジェクトを破棄します。</span><span class="sxs-lookup"><span data-stu-id="5ff18-112">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ff18-113">要件</span><span class="sxs-lookup"><span data-stu-id="5ff18-113">Requirements</span></span>  

 <span data-ttu-id="5ff18-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ff18-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ff18-115">**ヘッダー:** ICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="5ff18-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="5ff18-116">**ライブラリ:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="5ff18-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="5ff18-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ff18-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff18-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ff18-118">See also</span></span>

- [<span data-ttu-id="5ff18-119">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="5ff18-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
