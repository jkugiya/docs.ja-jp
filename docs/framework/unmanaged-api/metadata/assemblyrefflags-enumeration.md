---
description: '詳細については、次を参照してください: AssemblyRefFlags 列挙型'
title: AssemblyRefFlags 列挙型
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
ms.openlocfilehash: 1b33faf816194c8b386f34a63d885ba37c4329a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678901"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="012ea-103">AssemblyRefFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="012ea-103">AssemblyRefFlags Enumeration</span></span>

<span data-ttu-id="012ea-104">アセンブリ参照の機能を記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="012ea-104">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="012ea-105">構文</span><span class="sxs-lookup"><span data-stu-id="012ea-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="012ea-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="012ea-106">Members</span></span>  
  
|<span data-ttu-id="012ea-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="012ea-107">Member</span></span>|<span data-ttu-id="012ea-108">説明</span><span class="sxs-lookup"><span data-stu-id="012ea-108">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="012ea-109">アセンブリ参照に、アセンブリの発行者に関する完全なハッシュされていない情報が含まれることを指定します。</span><span class="sxs-lookup"><span data-stu-id="012ea-109">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="012ea-110">要件</span><span class="sxs-lookup"><span data-stu-id="012ea-110">Requirements</span></span>  

 <span data-ttu-id="012ea-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="012ea-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="012ea-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="012ea-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="012ea-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="012ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="012ea-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="012ea-114">See also</span></span>

- [<span data-ttu-id="012ea-115">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="012ea-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="012ea-116">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="012ea-116">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="012ea-117">DefineAssemblyRef メソッド</span><span class="sxs-lookup"><span data-stu-id="012ea-117">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)
