---
description: '詳細情報: GetCLRIdentityManager 関数'
title: GetCLRIdentityManager 関数
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 483cf0499fa162da4c89e350198a5609f9f1bab6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785368"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="c8ca4-103">GetCLRIdentityManager 関数</span><span class="sxs-lookup"><span data-stu-id="c8ca4-103">GetCLRIdentityManager Function</span></span>

<span data-ttu-id="c8ca4-104">共通言語ランタイム (CLR) が id を管理できるようにするインターフェイスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-104">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="c8ca4-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8ca4-106">構文</span><span class="sxs-lookup"><span data-stu-id="c8ca4-106">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8ca4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8ca4-107">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="c8ca4-108">から `REFIID` 取得するインターフェイスを指定する (インターフェイス識別子)。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-108">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="c8ca4-109">この値は IID_ICLRAssemblyIdentityManager または IID_ICLRHostBindingPolicyManager のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-109">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="c8ca4-110">入出力 [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) または [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) オブジェクトのいずれかのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-110">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8ca4-111">解説</span><span class="sxs-lookup"><span data-stu-id="c8ca4-111">Remarks</span></span>  

 <span data-ttu-id="c8ca4-112">関数へのポインターを取得するには、 [GetRealProcAddress](getrealprocaddress-function.md) 関数を呼び出し `GetCLRIdentityManager` ます。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-112">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8ca4-113">要件</span><span class="sxs-lookup"><span data-stu-id="c8ca4-113">Requirements</span></span>  

 <span data-ttu-id="c8ca4-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8ca4-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c8ca4-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8ca4-116">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="c8ca4-116">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="c8ca4-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8ca4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ca4-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8ca4-118">See also</span></span>

- [<span data-ttu-id="c8ca4-119">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="c8ca4-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
