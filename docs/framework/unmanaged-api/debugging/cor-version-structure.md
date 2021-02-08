---
description: '詳細情報: COR_VERSION 構造'
title: COR_VERSION 構造体
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
ms.openlocfilehash: abdbe2a62d89db9dd673a429d81209fc42c34b73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801775"
---
# <a name="cor_version-structure"></a><span data-ttu-id="8baea-103">COR_VERSION 構造体</span><span class="sxs-lookup"><span data-stu-id="8baea-103">COR_VERSION Structure</span></span>

<span data-ttu-id="8baea-104">共通言語ランタイムの標準の 4 つの部分のバージョン番号を保存します。</span><span class="sxs-lookup"><span data-stu-id="8baea-104">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8baea-105">構文</span><span class="sxs-lookup"><span data-stu-id="8baea-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="8baea-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8baea-106">Members</span></span>  
  
|<span data-ttu-id="8baea-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="8baea-107">Member</span></span>|<span data-ttu-id="8baea-108">説明</span><span class="sxs-lookup"><span data-stu-id="8baea-108">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="8baea-109">メジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="8baea-109">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="8baea-110">マイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="8baea-110">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="8baea-111">ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="8baea-111">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="8baea-112">サブビルド番号。</span><span class="sxs-lookup"><span data-stu-id="8baea-112">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8baea-113">解説</span><span class="sxs-lookup"><span data-stu-id="8baea-113">Remarks</span></span>  

 <span data-ttu-id="8baea-114">バージョン番号が1.0.3705.288 の場合、1はメジャーバージョン番号、0はマイナーバージョン番号、3705はビルド番号、288はサブビルド番号です。</span><span class="sxs-lookup"><span data-stu-id="8baea-114">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8baea-115">要件</span><span class="sxs-lookup"><span data-stu-id="8baea-115">Requirements</span></span>  

 <span data-ttu-id="8baea-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8baea-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8baea-117">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="8baea-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="8baea-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8baea-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8baea-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8baea-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8baea-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8baea-120">See also</span></span>

- [<span data-ttu-id="8baea-121">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="8baea-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="8baea-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8baea-122">Debugging</span></span>](index.md)
