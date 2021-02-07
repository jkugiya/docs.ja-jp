---
description: '詳細について: ICLRMetaHost:: ExitProcess メソッド'
title: ICLRMetaHost::ExitProcess メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: 3bc832538a5ad2b457de758fc35a632b09c02974
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689158"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="1f4fa-103">ICLRMetaHost::ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="1f4fa-103">ICLRMetaHost::ExitProcess Method</span></span>

<span data-ttu-id="1f4fa-104">読み込まれたすべてのランタイムを正常にシャットダウンしてから、プロセスを終了しようとします。</span><span class="sxs-lookup"><span data-stu-id="1f4fa-104">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="1f4fa-105">[CorExitProcess](corexitprocess-function.md)関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="1f4fa-105">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f4fa-106">構文</span><span class="sxs-lookup"><span data-stu-id="1f4fa-106">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f4fa-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1f4fa-107">Parameters</span></span>  

 `iExitCode`  
 <span data-ttu-id="1f4fa-108">からプロセスの終了コード。</span><span class="sxs-lookup"><span data-stu-id="1f4fa-108">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f4fa-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="1f4fa-109">Return Value</span></span>  

 <span data-ttu-id="1f4fa-110">このメソッドはを返しません。そのため、戻り値は未定義です。</span><span class="sxs-lookup"><span data-stu-id="1f4fa-110">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f4fa-111">解説</span><span class="sxs-lookup"><span data-stu-id="1f4fa-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f4fa-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="1f4fa-112">Requirements</span></span>  

 <span data-ttu-id="1f4fa-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f4fa-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f4fa-114">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="1f4fa-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1f4fa-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1f4fa-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f4fa-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f4fa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4fa-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f4fa-117">See also</span></span>

- [<span data-ttu-id="1f4fa-118">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f4fa-118">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="1f4fa-119">ホスティング</span><span class="sxs-lookup"><span data-stu-id="1f4fa-119">Hosting</span></span>](index.md)
