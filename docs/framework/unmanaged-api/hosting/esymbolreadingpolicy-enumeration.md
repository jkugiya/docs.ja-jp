---
description: '詳細については、次を参照してください: ESymbolReadingPolicy 列挙型'
title: ESymbolReadingPolicy 列挙型
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: e84c31343b589cb6019d88fafc9b94207c5f5892
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785420"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="68780-103">ESymbolReadingPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="68780-103">ESymbolReadingPolicy Enumeration</span></span>

<span data-ttu-id="68780-104">プログラムデータベース (PDB) ファイルを読み取るためのポリシーを設定する値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="68780-104">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68780-105">構文</span><span class="sxs-lookup"><span data-stu-id="68780-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="68780-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="68780-106">Members</span></span>  
  
|<span data-ttu-id="68780-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="68780-107">Member</span></span>|<span data-ttu-id="68780-108">説明</span><span class="sxs-lookup"><span data-stu-id="68780-108">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="68780-109">デバッガーが常に PDB ファイルを読み取る必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="68780-109">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="68780-110">デバッガーが、完全に信頼されたアセンブリに関連付けられている PDB ファイルのみを読み取るように指定します。</span><span class="sxs-lookup"><span data-stu-id="68780-110">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="68780-111">デバッガーが PDB ファイルを読み取らないように指定します。</span><span class="sxs-lookup"><span data-stu-id="68780-111">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68780-112">解説</span><span class="sxs-lookup"><span data-stu-id="68780-112">Remarks</span></span>  

 <span data-ttu-id="68780-113">`ESymbolReadingPolicy`列挙体は、 [ICLRDebugManager:: SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md)メソッドと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="68780-113">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68780-114">要件</span><span class="sxs-lookup"><span data-stu-id="68780-114">Requirements</span></span>  

 <span data-ttu-id="68780-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68780-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68780-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="68780-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68780-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68780-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68780-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68780-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68780-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="68780-119">See also</span></span>

- [<span data-ttu-id="68780-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="68780-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
