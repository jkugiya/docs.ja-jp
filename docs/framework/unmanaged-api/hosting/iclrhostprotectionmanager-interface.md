---
description: 詳細については、「ICLRHostProtectionManager インターフェイス」を参照してください。
title: ICLRHostProtectionManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: 60d27a8c1a24720bbfdcde52a5495425279d5ac4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689248"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="3807f-103">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3807f-103">ICLRHostProtectionManager Interface</span></span>

<span data-ttu-id="3807f-104">ホストが、部分的に信頼されたコードで実行される特定のマネージクラス、メソッド、プロパティ、およびフィールドをブロックできるようにします。</span><span class="sxs-lookup"><span data-stu-id="3807f-104">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3807f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3807f-105">Methods</span></span>  
  
|<span data-ttu-id="3807f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3807f-106">Method</span></span>|<span data-ttu-id="3807f-107">説明</span><span class="sxs-lookup"><span data-stu-id="3807f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3807f-108">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="3807f-108">SetEagerSerializeGrantSets</span></span>](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="3807f-109">致命的な共通言語ランタイム (CLR) エラーを引き起こす可能性のあるまれな競合状態が発生しないことを保証します。</span><span class="sxs-lookup"><span data-stu-id="3807f-109">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="3807f-110">SetProtectedCategories メソッド</span><span class="sxs-lookup"><span data-stu-id="3807f-110">SetProtectedCategories Method</span></span>](iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="3807f-111">部分的に信頼されたコードでの実行をブロックする必要がある、マネージ型とメンバーのカテゴリを指定します。</span><span class="sxs-lookup"><span data-stu-id="3807f-111">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3807f-112">要件</span><span class="sxs-lookup"><span data-stu-id="3807f-112">Requirements</span></span>  

 <span data-ttu-id="3807f-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3807f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3807f-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3807f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3807f-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3807f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3807f-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3807f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3807f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3807f-117">See also</span></span>

- [<span data-ttu-id="3807f-118">EApiCategories 列挙型</span><span class="sxs-lookup"><span data-stu-id="3807f-118">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="3807f-119">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3807f-119">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
