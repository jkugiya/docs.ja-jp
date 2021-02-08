---
description: '詳細情報: CLR_DEBUGGING_VERSION 構造'
title: CLR_DEBUGGING_VERSION 構造体
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
ms.openlocfilehash: 2d274a91948b98dc309cd5670c3dd3bf6cd01e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772784"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="97d86-103">CLR_DEBUGGING_VERSION 構造体</span><span class="sxs-lookup"><span data-stu-id="97d86-103">CLR_DEBUGGING_VERSION Structure</span></span>

<span data-ttu-id="97d86-104">デバッグのために共通言語ランタイム (CLR) の製品バージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="97d86-104">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d86-105">構文</span><span class="sxs-lookup"><span data-stu-id="97d86-105">Syntax</span></span>  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="97d86-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="97d86-106">Members</span></span>  
  
|<span data-ttu-id="97d86-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="97d86-107">Member</span></span>|<span data-ttu-id="97d86-108">説明</span><span class="sxs-lookup"><span data-stu-id="97d86-108">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="97d86-109">構造体のバージョン番号</span><span class="sxs-lookup"><span data-stu-id="97d86-109">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="97d86-110">メジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="97d86-110">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="97d86-111">マイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="97d86-111">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="97d86-112">ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="97d86-112">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="97d86-113">リビジョン番号。</span><span class="sxs-lookup"><span data-stu-id="97d86-113">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97d86-114">解説</span><span class="sxs-lookup"><span data-stu-id="97d86-114">Remarks</span></span>  

 <span data-ttu-id="97d86-115">構造体 `CLR_DEBUGGING_VERSION` は COR_VERSION 構造体と同じですが、構造体には `CLR_DEBUGGING_VERSION` 追加の構造体のバージョンフィールド () が用意されて `wStructVersion` います。</span><span class="sxs-lookup"><span data-stu-id="97d86-115">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="97d86-116">現在、このフィールドは0に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d86-116">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d86-117">要件</span><span class="sxs-lookup"><span data-stu-id="97d86-117">Requirements</span></span>  

 <span data-ttu-id="97d86-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97d86-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d86-119">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="97d86-119">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="97d86-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97d86-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97d86-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d86-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d86-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="97d86-122">See also</span></span>

- [<span data-ttu-id="97d86-123">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="97d86-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="97d86-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="97d86-124">Debugging</span></span>](index.md)
