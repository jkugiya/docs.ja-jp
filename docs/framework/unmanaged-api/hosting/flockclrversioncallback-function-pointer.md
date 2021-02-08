---
description: '詳細情報: FLockClrVersionCallback 関数ポインター'
title: FLockClrVersionCallback 関数ポインター
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: 3506cd30ab2a9e5a06b03f5010c9870280a38378
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785381"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="4e70c-103">FLockClrVersionCallback 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="4e70c-103">FLockClrVersionCallback Function Pointer</span></span>

<span data-ttu-id="4e70c-104">は、初期化が開始されたか完了したことを示すために、共通言語ランタイム (CLR) が呼び出す関数を指します。</span><span class="sxs-lookup"><span data-stu-id="4e70c-104">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="4e70c-105">この関数ポインターは .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="4e70c-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e70c-106">構文</span><span class="sxs-lookup"><span data-stu-id="4e70c-106">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="4e70c-107">解説</span><span class="sxs-lookup"><span data-stu-id="4e70c-107">Remarks</span></span>  

 <span data-ttu-id="4e70c-108">この関数は、ホストによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="4e70c-108">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e70c-109">要件</span><span class="sxs-lookup"><span data-stu-id="4e70c-109">Requirements</span></span>  

 <span data-ttu-id="4e70c-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e70c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e70c-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4e70c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e70c-112">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="4e70c-112">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="4e70c-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e70c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e70c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e70c-114">See also</span></span>

- [<span data-ttu-id="4e70c-115">LockClrVersion 関数</span><span class="sxs-lookup"><span data-stu-id="4e70c-115">LockClrVersion Function</span></span>](lockclrversion-function.md)
- [<span data-ttu-id="4e70c-116">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="4e70c-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
