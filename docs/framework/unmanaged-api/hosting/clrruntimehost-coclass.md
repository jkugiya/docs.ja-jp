---
description: '次の詳細情報: CLRRuntimeHost コクラス'
title: CLRRuntimeHost コクラス
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: a371b9b7263f8bb58b5c513de6647320f000beed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799890"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="ee19d-103">CLRRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="ee19d-103">CLRRuntimeHost Coclass</span></span>

<span data-ttu-id="ee19d-104">ランタイムによるコード実行を管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee19d-104">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee19d-105">構文</span><span class="sxs-lookup"><span data-stu-id="ee19d-105">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="ee19d-106">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee19d-106">Interfaces</span></span>  
  
|<span data-ttu-id="ee19d-107">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee19d-107">Interface</span></span>|<span data-ttu-id="ee19d-108">説明</span><span class="sxs-lookup"><span data-stu-id="ee19d-108">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="ee19d-109">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee19d-109">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="ee19d-110">ランタイムによるアプリケーションの実行を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee19d-110">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="ee19d-111">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee19d-111">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="ee19d-112">ポータブル実行可能イメージを検証し、検証エラーの詳細なレポートを作成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee19d-112">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee19d-113">要件</span><span class="sxs-lookup"><span data-stu-id="ee19d-113">Requirements</span></span>  

 <span data-ttu-id="ee19d-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee19d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee19d-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ee19d-115">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="ee19d-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ee19d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee19d-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee19d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee19d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee19d-118">See also</span></span>

- [<span data-ttu-id="ee19d-119">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="ee19d-119">Hosting Coclasses</span></span>](hosting-coclasses.md)
