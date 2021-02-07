---
description: 詳細については、「CorRegFlags 列挙型」を参照してください。
title: CorRegFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
ms.openlocfilehash: 534b7b4b170d1f586e967807c4cc8a9c82648e8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753662"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="926f0-103">CorRegFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="926f0-103">CorRegFlags Enumeration</span></span>

<span data-ttu-id="926f0-104">モジュールまたは複合イメージをインストールするときに登録に使用されるフラグ値を提供します。</span><span class="sxs-lookup"><span data-stu-id="926f0-104">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="926f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="926f0-105">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="926f0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="926f0-106">Members</span></span>  
  
|<span data-ttu-id="926f0-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="926f0-107">Member</span></span>|<span data-ttu-id="926f0-108">説明</span><span class="sxs-lookup"><span data-stu-id="926f0-108">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="926f0-109">転送先にファイルをコピーしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="926f0-109">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="926f0-110">モジュールまたは複合が構成であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="926f0-110">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="926f0-111">モジュールまたは複合にクラス参照があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="926f0-111">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="926f0-112">要件</span><span class="sxs-lookup"><span data-stu-id="926f0-112">Requirements</span></span>  

 <span data-ttu-id="926f0-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="926f0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="926f0-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="926f0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="926f0-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="926f0-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="926f0-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="926f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="926f0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="926f0-117">See also</span></span>

- [<span data-ttu-id="926f0-118">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="926f0-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
