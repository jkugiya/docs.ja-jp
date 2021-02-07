---
description: 詳細については、「CorValidatorModuleType 列挙型」を参照してください。
title: CorValidatorModuleType 列挙型
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: 13792c461660ddd8cfd530f5b34d642d806cdea4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707242"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="ac095-103">CorValidatorModuleType 列挙型</span><span class="sxs-lookup"><span data-stu-id="ac095-103">CorValidatorModuleType Enumeration</span></span>

<span data-ttu-id="ac095-104">モジュールの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac095-104">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac095-105">構文</span><span class="sxs-lookup"><span data-stu-id="ac095-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="ac095-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ac095-106">Members</span></span>  
  
|<span data-ttu-id="ac095-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="ac095-107">Member</span></span>|<span data-ttu-id="ac095-108">説明</span><span class="sxs-lookup"><span data-stu-id="ac095-108">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="ac095-109">モジュールの型が無効です。</span><span class="sxs-lookup"><span data-stu-id="ac095-109">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="ac095-110">列挙型の最小値 `CorValidatorModuleType` 。</span><span class="sxs-lookup"><span data-stu-id="ac095-110">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="ac095-111">モジュールは、移植可能な実行可能 (PE) ファイルです。</span><span class="sxs-lookup"><span data-stu-id="ac095-111">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="ac095-112">モジュールは .obj ファイルです。</span><span class="sxs-lookup"><span data-stu-id="ac095-112">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="ac095-113">モジュールは、エディットコンティニュのデバッガーセッションです。</span><span class="sxs-lookup"><span data-stu-id="ac095-113">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="ac095-114">モジュールは、インクリメンタルビルドされたモジュールです。</span><span class="sxs-lookup"><span data-stu-id="ac095-114">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="ac095-115">列挙型の最大値 `CorValidatorModuleType` 。</span><span class="sxs-lookup"><span data-stu-id="ac095-115">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac095-116">要件</span><span class="sxs-lookup"><span data-stu-id="ac095-116">Requirements</span></span>  

 <span data-ttu-id="ac095-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac095-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac095-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="ac095-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac095-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ac095-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac095-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac095-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac095-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac095-121">See also</span></span>

- [<span data-ttu-id="ac095-122">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="ac095-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
