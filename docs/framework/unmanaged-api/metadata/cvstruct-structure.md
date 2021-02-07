---
description: '詳細情報: CVStruct 構造体'
title: CVStruct 構造体
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
ms.openlocfilehash: 25e8073f75620bca0737b11499d318cd57d6101c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707216"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="4e172-103">CVStruct 構造体</span><span class="sxs-lookup"><span data-stu-id="4e172-103">CVStruct Structure</span></span>

<span data-ttu-id="4e172-104">モジュールまたは複合イメージをインストールするときに使用する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4e172-104">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e172-105">構文</span><span class="sxs-lookup"><span data-stu-id="4e172-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="4e172-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4e172-106">Members</span></span>  
  
|<span data-ttu-id="4e172-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="4e172-107">Member</span></span>|<span data-ttu-id="4e172-108">説明</span><span class="sxs-lookup"><span data-stu-id="4e172-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4e172-109">メジャー</span><span class="sxs-lookup"><span data-stu-id="4e172-109">Major</span></span>|<span data-ttu-id="4e172-110">メジャーバージョンのビルド番号。</span><span class="sxs-lookup"><span data-stu-id="4e172-110">Major version build number.</span></span>|  
|<span data-ttu-id="4e172-111">Minor</span><span class="sxs-lookup"><span data-stu-id="4e172-111">Minor</span></span>|<span data-ttu-id="4e172-112">マイナーバージョンのビルド番号。</span><span class="sxs-lookup"><span data-stu-id="4e172-112">Minor version build number.</span></span>|  
|<span data-ttu-id="4e172-113">Sub</span><span class="sxs-lookup"><span data-stu-id="4e172-113">Sub</span></span>|<span data-ttu-id="4e172-114">サブビルド番号。</span><span class="sxs-lookup"><span data-stu-id="4e172-114">Sub-build number.</span></span>|  
|<span data-ttu-id="4e172-115">Build</span><span class="sxs-lookup"><span data-stu-id="4e172-115">Build</span></span>|<span data-ttu-id="4e172-116">ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="4e172-116">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e172-117">要件</span><span class="sxs-lookup"><span data-stu-id="4e172-117">Requirements</span></span>  

 <span data-ttu-id="4e172-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e172-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e172-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4e172-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e172-120">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="4e172-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e172-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e172-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e172-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e172-122">See also</span></span>

- [<span data-ttu-id="4e172-123">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="4e172-123">Metadata Structures</span></span>](metadata-structures.md)
