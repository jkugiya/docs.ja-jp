---
description: '詳細については、次を参照してください: CorFileMapping 列挙型'
title: CorFileMapping 列挙体
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 0fc3916e75c576a6b133ba8a49c00eec6c9bac19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784471"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="e1ad0-103">CorFileMapping 列挙体</span><span class="sxs-lookup"><span data-stu-id="e1ad0-103">CorFileMapping Enumeration</span></span>

<span data-ttu-id="e1ad0-104">[IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md)メソッドの呼び出しから返されるファイルマッピングの種類を記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="e1ad0-104">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1ad0-105">構文</span><span class="sxs-lookup"><span data-stu-id="e1ad0-105">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="e1ad0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e1ad0-106">Members</span></span>  
  
|<span data-ttu-id="e1ad0-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e1ad0-107">Member</span></span>|<span data-ttu-id="e1ad0-108">説明</span><span class="sxs-lookup"><span data-stu-id="e1ad0-108">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="e1ad0-109">ファイルはデータファイルとしてマップされます。</span><span class="sxs-lookup"><span data-stu-id="e1ad0-109">The file is mapped as a data file.</span></span> <span data-ttu-id="e1ad0-110">つまり、フラグは `SEC_IMAGE` Microsoft Win32 関数に渡されませんでした `CreateFileMapping` 。</span><span class="sxs-lookup"><span data-stu-id="e1ad0-110">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="e1ad0-111">`LoadLibrary`関数または関数をフラグと共に使用することで、ファイルは実行用にマップされ `CreateFileMapping` `SEC_IMAGE` ます。</span><span class="sxs-lookup"><span data-stu-id="e1ad0-111">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1ad0-112">要件</span><span class="sxs-lookup"><span data-stu-id="e1ad0-112">Requirements</span></span>  

 <span data-ttu-id="e1ad0-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1ad0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1ad0-114">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e1ad0-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e1ad0-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1ad0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ad0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1ad0-116">See also</span></span>

- [<span data-ttu-id="e1ad0-117">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="e1ad0-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="e1ad0-118">GetFileMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="e1ad0-118">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
