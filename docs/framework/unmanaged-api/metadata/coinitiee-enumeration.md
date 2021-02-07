---
description: '詳細情報: COINITIEE 列挙型'
title: COINITIEE 列挙型
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: c17980582903a29cdfe33c64200c31f29ddeb17c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678608"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="db2b9-103">COINITIEE 列挙型</span><span class="sxs-lookup"><span data-stu-id="db2b9-103">COINITIEE Enumeration</span></span>

<span data-ttu-id="db2b9-104">共通言語ランタイムを初期化するときに [Coinitializeee](../hosting/coinitializeee-function.md) によって使用される定数を指定します。</span><span class="sxs-lookup"><span data-stu-id="db2b9-104">Specifies constants used by [CoInitializeEE](../hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db2b9-105">構文</span><span class="sxs-lookup"><span data-stu-id="db2b9-105">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="db2b9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="db2b9-106">Members</span></span>  
  
|<span data-ttu-id="db2b9-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="db2b9-107">Member</span></span>|<span data-ttu-id="db2b9-108">説明</span><span class="sxs-lookup"><span data-stu-id="db2b9-108">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="db2b9-109">既定の初期化モード。</span><span class="sxs-lookup"><span data-stu-id="db2b9-109">Default initialization mode.</span></span> <span data-ttu-id="db2b9-110">これにより、ランタイムが初期化され、既定値が作成され <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="db2b9-110">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="db2b9-111">マネージ DLL を実行するように初期化します。</span><span class="sxs-lookup"><span data-stu-id="db2b9-111">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="db2b9-112">マネージ EXE を実行するように初期化します。</span><span class="sxs-lookup"><span data-stu-id="db2b9-112">Initializes to run a managed EXE.</span></span> <span data-ttu-id="db2b9-113">これにより、ランタイムが初期化されますが、既定値は作成されません <xref:System.AppDomain> 。これは、EXE のメインルーチンを入力した後に作成されます。</span><span class="sxs-lookup"><span data-stu-id="db2b9-113">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db2b9-114">要件</span><span class="sxs-lookup"><span data-stu-id="db2b9-114">Requirements</span></span>  

 <span data-ttu-id="db2b9-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db2b9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db2b9-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="db2b9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db2b9-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="db2b9-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db2b9-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db2b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db2b9-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="db2b9-119">See also</span></span>

- [<span data-ttu-id="db2b9-120">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="db2b9-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
