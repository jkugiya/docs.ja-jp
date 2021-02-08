---
description: 詳細については、「CorFileFlags 列挙型」を参照してください。
title: CorFileFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
ms.openlocfilehash: 8ffad9bad9c656a10c2c556f5e06f9d510ccb45a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784484"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="982c1-103">CorFileFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="982c1-103">CorFileFlags Enumeration</span></span>

<span data-ttu-id="982c1-104">[IMetaDataAssemblyEmit::D efineFile](imetadataassemblyemit-definefile-method.md)への呼び出しで定義されているファイルの種類を記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="982c1-104">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="982c1-105">構文</span><span class="sxs-lookup"><span data-stu-id="982c1-105">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="982c1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="982c1-106">Members</span></span>  
  
|<span data-ttu-id="982c1-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="982c1-107">Member</span></span>|<span data-ttu-id="982c1-108">説明</span><span class="sxs-lookup"><span data-stu-id="982c1-108">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="982c1-109">は、ファイルがリソースファイルではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="982c1-109">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="982c1-110">ファイル (場合によってはリソースファイル) にメタデータが含まれていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="982c1-110">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="982c1-111">要件</span><span class="sxs-lookup"><span data-stu-id="982c1-111">Requirements</span></span>  

 <span data-ttu-id="982c1-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="982c1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="982c1-113">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="982c1-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="982c1-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="982c1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982c1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="982c1-115">See also</span></span>

- [<span data-ttu-id="982c1-116">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="982c1-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
