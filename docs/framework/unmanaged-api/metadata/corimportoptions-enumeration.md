---
description: '詳細については、次を参照してください: CorImportOptions 列挙型'
title: CorImportOptions 列挙型
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
ms.openlocfilehash: b942ed3f5b1b3c400b4f901e3dd3c4364e1d588c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784445"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="f073c-103">CorImportOptions 列挙型</span><span class="sxs-lookup"><span data-stu-id="f073c-103">CorImportOptions Enumeration</span></span>

<span data-ttu-id="f073c-104">現在のスコープ外のアセンブリのインポート中の動作を制御するフラグ値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="f073c-104">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f073c-105">構文</span><span class="sxs-lookup"><span data-stu-id="f073c-105">Syntax</span></span>  
  
```cpp  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="f073c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f073c-106">Members</span></span>  
  
|<span data-ttu-id="f073c-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f073c-107">Member</span></span>|<span data-ttu-id="f073c-108">説明</span><span class="sxs-lookup"><span data-stu-id="f073c-108">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="f073c-109">削除されたレコードをスキップする既定の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="f073c-109">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="f073c-110">すべてのメタデータを列挙する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f073c-110">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="f073c-111">削除された Typedef も含め、すべての Typedef を列挙する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f073c-111">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="f073c-112">削除されたものを含むすべての MethodDefs を列挙する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f073c-112">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="f073c-113">削除されたものも含め、すべての FieldDefs を列挙する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f073c-113">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="f073c-114">削除されたものも含め、すべての PropertyDefs を列挙する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f073c-114">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="f073c-115">削除されたものも含め、すべての EventDefs を列挙する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f073c-115">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="f073c-116">削除された属性も含め、すべてのカスタム属性を列挙する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f073c-116">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="f073c-117">削除された型も含めて、エクスポートされたすべての型を列挙する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f073c-117">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f073c-118">要件</span><span class="sxs-lookup"><span data-stu-id="f073c-118">Requirements</span></span>  

 <span data-ttu-id="f073c-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f073c-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f073c-120">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="f073c-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f073c-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f073c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f073c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="f073c-122">See also</span></span>

- [<span data-ttu-id="f073c-123">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="f073c-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
