---
description: '詳細情報: COR_IL_MAP 構造'
title: COR_IL_MAP 構造体
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: ff3d636429f51119342baea5d71163eb9d764e03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712325"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="a9104-103">COR_IL_MAP 構造体</span><span class="sxs-lookup"><span data-stu-id="a9104-103">COR_IL_MAP Structure</span></span>

<span data-ttu-id="a9104-104">機能の相対オフセットでの変更を指定します。</span><span class="sxs-lookup"><span data-stu-id="a9104-104">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9104-105">構文</span><span class="sxs-lookup"><span data-stu-id="a9104-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="a9104-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a9104-106">Members</span></span>  
  
|<span data-ttu-id="a9104-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="a9104-107">Member</span></span>|<span data-ttu-id="a9104-108">説明</span><span class="sxs-lookup"><span data-stu-id="a9104-108">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="a9104-109">関数の先頭を基準とした、以前の Microsoft 中間言語 (MSIL) オフセット。</span><span class="sxs-lookup"><span data-stu-id="a9104-109">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="a9104-110">関数の先頭を基準とする新しい MSIL オフセット。</span><span class="sxs-lookup"><span data-stu-id="a9104-110">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="a9104-111">`true` マッピングが正確であることがわかっている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="a9104-111">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9104-112">解説</span><span class="sxs-lookup"><span data-stu-id="a9104-112">Remarks</span></span>  

 <span data-ttu-id="a9104-113">マップの形式は次のとおりです。デバッガーでは、が `oldOffset` 元の変更されていない msil コード内の msil オフセットを参照していると仮定します。</span><span class="sxs-lookup"><span data-stu-id="a9104-113">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="a9104-114">パラメーターは、新しいインストルメント化され `newOffset` たコード内で、対応する MSIL オフセットを参照します。</span><span class="sxs-lookup"><span data-stu-id="a9104-114">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="a9104-115">ステップ実行を正常に行うには、次の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9104-115">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="a9104-116">マップは昇順に並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9104-116">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="a9104-117">インストルメント化された MSIL コードを並べ替えることはできません。</span><span class="sxs-lookup"><span data-stu-id="a9104-117">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="a9104-118">元の MSIL コードは削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="a9104-118">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="a9104-119">マップには、プログラムデータベース (PDB) ファイルのすべてのシーケンスポイントをマップするためのエントリが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9104-119">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="a9104-120">マップでは、不足しているエントリは補間されません。</span><span class="sxs-lookup"><span data-stu-id="a9104-120">The map does not interpolate missing entries.</span></span> <span data-ttu-id="a9104-121">次の例は、マップとその結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="a9104-121">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="a9104-122">付け</span><span class="sxs-lookup"><span data-stu-id="a9104-122">Map:</span></span>  
  
- <span data-ttu-id="a9104-123">0個の古いオフセット、0個の新しいオフセット</span><span class="sxs-lookup"><span data-stu-id="a9104-123">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="a9104-124">5個の古いオフセット、10個の新しいオフセット</span><span class="sxs-lookup"><span data-stu-id="a9104-124">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="a9104-125">9個の古いオフセット、20個の新しいオフセット</span><span class="sxs-lookup"><span data-stu-id="a9104-125">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="a9104-126">結果:</span><span class="sxs-lookup"><span data-stu-id="a9104-126">Results:</span></span>  
  
- <span data-ttu-id="a9104-127">0、1、2、3、または4の古いオフセットは、新しいオフセット0にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a9104-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="a9104-128">古いオフセット5、6、7、または8は、新しいオフセット10にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a9104-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="a9104-129">9以上の古いオフセットは、新しいオフセット20にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a9104-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="a9104-130">新しいオフセット0、1、2、3、4、5、6、7、8、または9が古いオフセット0にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a9104-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="a9104-131">新しいオフセット10、11、12、13、14、15、16、17、18、19は、古いオフセット5にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a9104-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="a9104-132">20以上の新しいオフセットは、古いオフセット9にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a9104-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9104-133">要件</span><span class="sxs-lookup"><span data-stu-id="a9104-133">Requirements</span></span>  

 <span data-ttu-id="a9104-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9104-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9104-135">**ヘッダー:** CorDebug .idl、Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="a9104-135">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="a9104-136">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9104-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9104-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9104-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9104-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9104-138">See also</span></span>

- [<span data-ttu-id="a9104-139">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="a9104-139">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="a9104-140">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a9104-140">Debugging</span></span>](index.md)
