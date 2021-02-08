---
description: '詳細については、次を参照してください: ECustomDumpFlavor 列挙型'
title: ECustomDumpFlavor 列挙型
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 3ef118368fc827472bdaacb0b03d8c2011275056
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785529"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="66afe-103">ECustomDumpFlavor 列挙型</span><span class="sxs-lookup"><span data-stu-id="66afe-103">ECustomDumpFlavor Enumeration</span></span>

<span data-ttu-id="66afe-104">エラーを報告するときに、ヒープダンプのカスタムサブセットに含めるアイテムを示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="66afe-104">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66afe-105">構文</span><span class="sxs-lookup"><span data-stu-id="66afe-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="66afe-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="66afe-106">Members</span></span>  
  
|<span data-ttu-id="66afe-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="66afe-107">Member</span></span>|<span data-ttu-id="66afe-108">説明</span><span class="sxs-lookup"><span data-stu-id="66afe-108">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="66afe-109">カスタムヒープダンプをミニダンプとして起動し、同じメソッドに渡される [Customdumpitem](customdumpitem-structure.md) インスタンスによって指定された追加データを含めるように指定します。</span><span class="sxs-lookup"><span data-stu-id="66afe-109">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="66afe-110">カスタムヒープダンプで、動的に割り当てられていないすべての実行時状態データを収集するように指定します。</span><span class="sxs-lookup"><span data-stu-id="66afe-110">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66afe-111">解説</span><span class="sxs-lookup"><span data-stu-id="66afe-111">Remarks</span></span>  

 <span data-ttu-id="66afe-112">型のパラメーター `ECustomDumpFlavor` は、 [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="66afe-112">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66afe-113">要件</span><span class="sxs-lookup"><span data-stu-id="66afe-113">Requirements</span></span>  

 <span data-ttu-id="66afe-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66afe-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66afe-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="66afe-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66afe-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66afe-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66afe-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66afe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66afe-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="66afe-118">See also</span></span>

- [<span data-ttu-id="66afe-119">ECustomDumpItemKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="66afe-119">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="66afe-120">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66afe-120">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="66afe-121">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="66afe-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
