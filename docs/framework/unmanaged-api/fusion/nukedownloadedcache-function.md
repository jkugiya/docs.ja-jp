---
description: '詳細情報: NukeDownloadedCache 関数'
title: NukeDownloadedCache 関数
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
ms.openlocfilehash: 2239473b8e6e43a539b0507c8255d40f87e72043
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800033"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="0d5d5-103">NukeDownloadedCache 関数</span><span class="sxs-lookup"><span data-stu-id="0d5d5-103">NukeDownloadedCache Function</span></span>

<span data-ttu-id="0d5d5-104">共通言語ランタイム (CLR) のダウンロードキャッシュを削除します。</span><span class="sxs-lookup"><span data-stu-id="0d5d5-104">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d5d5-105">構文</span><span class="sxs-lookup"><span data-stu-id="0d5d5-105">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0d5d5-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="0d5d5-106">Return Value</span></span>  

 <span data-ttu-id="0d5d5-107">このメソッドは、Winerror.h で定義されているように、標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="0d5d5-107">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d5d5-108">解説</span><span class="sxs-lookup"><span data-stu-id="0d5d5-108">Remarks</span></span>  

 <span data-ttu-id="0d5d5-109">CLR ダウンロードキャッシュは、URL からダウンロードされる厳密な名前付きアセンブリが再利用できるように格納される領域です。</span><span class="sxs-lookup"><span data-stu-id="0d5d5-109">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d5d5-110">要件</span><span class="sxs-lookup"><span data-stu-id="0d5d5-110">Requirements</span></span>  

 <span data-ttu-id="0d5d5-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d5d5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d5d5-112">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0d5d5-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0d5d5-113">**Library:** Fusion.dll し、Mscorwks.dll します。</span><span class="sxs-lookup"><span data-stu-id="0d5d5-113">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="0d5d5-114">Mscorwks.dll ではなく Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にするようにします。</span><span class="sxs-lookup"><span data-stu-id="0d5d5-114">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="0d5d5-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d5d5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5d5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d5d5-116">See also</span></span>

- [<span data-ttu-id="0d5d5-117">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="0d5d5-117">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="0d5d5-118">GetHistoryFileDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="0d5d5-118">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="0d5d5-119">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="0d5d5-119">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
