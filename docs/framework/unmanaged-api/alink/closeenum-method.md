---
description: '詳細情報: CloseEnum メソッド'
title: CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
ms.openlocfilehash: 700c54de5af2e5c0be6940d4045019092655d46f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638380"
---
# <a name="closeenum-method"></a><span data-ttu-id="e073b-103">CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="e073b-103">CloseEnum Method</span></span>

<span data-ttu-id="e073b-104">指定された列挙体を閉じ、関連付けられているリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="e073b-104">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e073b-105">構文</span><span class="sxs-lookup"><span data-stu-id="e073b-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e073b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e073b-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="e073b-107">閉じられる列挙体のハンドル。</span><span class="sxs-lookup"><span data-stu-id="e073b-107">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e073b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e073b-108">Return Value</span></span>  

 <span data-ttu-id="e073b-109">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="e073b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e073b-110">要件</span><span class="sxs-lookup"><span data-stu-id="e073b-110">Requirements</span></span>  

 <span data-ttu-id="e073b-111">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="e073b-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e073b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e073b-112">See also</span></span>

- [<span data-ttu-id="e073b-113">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e073b-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e073b-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e073b-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e073b-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="e073b-115">ALink API</span></span>](index.md)
