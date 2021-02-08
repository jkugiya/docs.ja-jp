---
description: 詳細については、「ComCallUnmarshal コクラス」を参照してください。
title: ComCallUnmarshal コクラス
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
ms.openlocfilehash: 508c1183e2862a286e9db0390bc0348629a9db8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799838"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="8d877-103">ComCallUnmarshal コクラス</span><span class="sxs-lookup"><span data-stu-id="8d877-103">ComCallUnmarshal Coclass</span></span>

<span data-ttu-id="8d877-104">インターフェイスポインターのマーシャリングを管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d877-104">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d877-105">構文</span><span class="sxs-lookup"><span data-stu-id="8d877-105">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="8d877-106">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d877-106">Interfaces</span></span>  
  
|<span data-ttu-id="8d877-107">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d877-107">Interface</span></span>|<span data-ttu-id="8d877-108">説明</span><span class="sxs-lookup"><span data-stu-id="8d877-108">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="8d877-109">クライアントプロセスでプロキシを作成、初期化、および管理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d877-109">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d877-110">要件</span><span class="sxs-lookup"><span data-stu-id="8d877-110">Requirements</span></span>  

 <span data-ttu-id="8d877-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d877-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d877-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8d877-112">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="8d877-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8d877-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d877-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d877-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d877-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d877-115">See also</span></span>

- [<span data-ttu-id="8d877-116">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="8d877-116">Hosting Coclasses</span></span>](hosting-coclasses.md)
