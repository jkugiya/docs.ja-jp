---
description: '詳細については、次を参照してください: COUNINITIEE 列挙型'
title: COUNINITIEE 列挙型
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: 893ab96851e9c762a888f3c4cac98b486a0b4614
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707232"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="0edad-103">COUNINITIEE 列挙型</span><span class="sxs-lookup"><span data-stu-id="0edad-103">COUNINITIEE Enumeration</span></span>

<span data-ttu-id="0edad-104">共通言語ランタイムを初期化するときに [CoUninitializeEE](../hosting/couninitializeee-function.md) によって使用される定数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0edad-104">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0edad-105">構文</span><span class="sxs-lookup"><span data-stu-id="0edad-105">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="0edad-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0edad-106">Members</span></span>  
  
|<span data-ttu-id="0edad-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="0edad-107">Member</span></span>|<span data-ttu-id="0edad-108">説明</span><span class="sxs-lookup"><span data-stu-id="0edad-108">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="0edad-109">既定の初期化解除中モードを示します。</span><span class="sxs-lookup"><span data-stu-id="0edad-109">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="0edad-110">アセンブリをアンロードするための初期化解除中モードを示します。</span><span class="sxs-lookup"><span data-stu-id="0edad-110">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0edad-111">要件</span><span class="sxs-lookup"><span data-stu-id="0edad-111">Requirements</span></span>  

 <span data-ttu-id="0edad-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0edad-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0edad-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0edad-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0edad-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0edad-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0edad-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0edad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0edad-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0edad-116">See also</span></span>

- [<span data-ttu-id="0edad-117">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="0edad-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
