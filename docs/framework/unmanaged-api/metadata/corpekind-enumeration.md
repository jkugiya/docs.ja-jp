---
description: 詳細については、「CorPEKind 列挙型」を参照してください。
title: CorPEKind 列挙型
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 6d1f29a220ce9d4be4151d8eff6557fa8c693ed2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784276"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="1d7e3-103">CorPEKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="1d7e3-103">CorPEKind Enumeration</span></span>

<span data-ttu-id="1d7e3-104">[IMetaDataImport2:: GetPEKind](imetadataimport2-getpekind-method.md)の呼び出しから返される、ポータブル実行可能 (PE) ファイルを記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="1d7e3-104">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d7e3-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d7e3-105">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="1d7e3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1d7e3-106">Members</span></span>  
  
|<span data-ttu-id="1d7e3-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="1d7e3-107">Member</span></span>|<span data-ttu-id="1d7e3-108">説明</span><span class="sxs-lookup"><span data-stu-id="1d7e3-108">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="1d7e3-109">これが PE ファイルではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1d7e3-109">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="1d7e3-110">この PE ファイルにマネージコードのみが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="1d7e3-110">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="1d7e3-111">この PE ファイルが Win32 呼び出しを行うことを示します。</span><span class="sxs-lookup"><span data-stu-id="1d7e3-111">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="1d7e3-112">この PE ファイルが64ビットプラットフォームで実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="1d7e3-112">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="1d7e3-113">この PE ファイルがネイティブコードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="1d7e3-113">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="1d7e3-114">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="1d7e3-114">pe32BitPreferred</span></span>|<span data-ttu-id="1d7e3-115">この PE ファイルがプラットフォームに依存せず、32ビット環境で読み込まれることを示すことを示します。</span><span class="sxs-lookup"><span data-stu-id="1d7e3-115">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d7e3-116">解説</span><span class="sxs-lookup"><span data-stu-id="1d7e3-116">Remarks</span></span>  

 <span data-ttu-id="1d7e3-117">これらの値は、ビットごとの組み合わせで使用できます。</span><span class="sxs-lookup"><span data-stu-id="1d7e3-117">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d7e3-118">要件</span><span class="sxs-lookup"><span data-stu-id="1d7e3-118">Requirements</span></span>  

 <span data-ttu-id="1d7e3-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d7e3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d7e3-120">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="1d7e3-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1d7e3-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d7e3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d7e3-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d7e3-122">See also</span></span>

- [<span data-ttu-id="1d7e3-123">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="1d7e3-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
