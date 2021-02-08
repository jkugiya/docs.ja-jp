---
description: '詳細情報: InitDbgTransportManager 関数'
title: InitDbgTransportManager 関数
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
ms.openlocfilehash: 19cdfcbe3a5b120c11fc781476410833997b8c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790439"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="705c7-103">InitDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="705c7-103">InitDbgTransportManager Function</span></span>

<span data-ttu-id="705c7-104">プロセスおよびランタイムの列挙のためにリモート ターゲットに接続するよう、トランスポート マネージャーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="705c7-104">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="705c7-105">構文</span><span class="sxs-lookup"><span data-stu-id="705c7-105">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="705c7-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="705c7-106">Return Value</span></span>  

 <span data-ttu-id="705c7-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="705c7-107">S_OK</span></span>  
 <span data-ttu-id="705c7-108">正常終了しました。</span><span class="sxs-lookup"><span data-stu-id="705c7-108">Success.</span></span>  
  
 <span data-ttu-id="705c7-109">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="705c7-109">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="705c7-110">関数はトランスポート マネージャーにメモリを割り当てられませんでした。</span><span class="sxs-lookup"><span data-stu-id="705c7-110">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="705c7-111">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="705c7-111">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="705c7-112">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="705c7-112">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="705c7-113">要件</span><span class="sxs-lookup"><span data-stu-id="705c7-113">Requirements</span></span>  

 <span data-ttu-id="705c7-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="705c7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="705c7-115">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="705c7-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="705c7-116">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="705c7-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="705c7-117">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="705c7-117">**.NET Framework Versions:** 3.5 SP1</span></span>
