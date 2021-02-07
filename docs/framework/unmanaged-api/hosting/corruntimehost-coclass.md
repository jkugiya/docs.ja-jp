---
description: '詳細については、次を参照してください: CorRuntimeHost コクラス'
title: CorRuntimeHost コクラス
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: cd2d01075e5c8264337e1e989b3d9fdc6bf68962
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760642"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="c6667-103">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="c6667-103">CorRuntimeHost Coclass</span></span>

<span data-ttu-id="c6667-104">共通言語ランタイムによって実行されるアプリケーションを管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6667-104">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6667-105">構文</span><span class="sxs-lookup"><span data-stu-id="c6667-105">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="c6667-106">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c6667-106">Interfaces</span></span>  
  
|<span data-ttu-id="c6667-107">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c6667-107">Interface</span></span>|<span data-ttu-id="c6667-108">説明</span><span class="sxs-lookup"><span data-stu-id="c6667-108">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c6667-109">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c6667-109">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="c6667-110">共通言語ランタイム (CLR: common language runtime) を構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6667-110">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="c6667-111">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c6667-111">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="c6667-112">ホストが共通言語ランタイムを明示的に開始または停止したり、アプリケーションドメインを作成および構成したり、既定のドメインにアクセスしたり、プロセスで実行されているすべてのドメインを列挙したりできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6667-112">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="c6667-113">IDebuggerInfo Iインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c6667-113">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="c6667-114">デバッグサービスの状態に関する情報を取得するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6667-114">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="c6667-115">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c6667-115">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="c6667-116">ガベージコレクションシステムに関する情報を取得し、ガベージコレクションのいくつかの側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6667-116">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="c6667-117">IValidator</span><span class="sxs-lookup"><span data-stu-id="c6667-117">"IValidator"</span></span>|<span data-ttu-id="c6667-118">ポータブル実行可能イメージを検証し、検証エラーの詳細なレポートを作成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6667-118">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6667-119">要件</span><span class="sxs-lookup"><span data-stu-id="c6667-119">Requirements</span></span>  

 <span data-ttu-id="c6667-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6667-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6667-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c6667-121">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c6667-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c6667-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6667-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6667-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6667-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6667-124">See also</span></span>

- [<span data-ttu-id="c6667-125">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="c6667-125">Hosting Coclasses</span></span>](hosting-coclasses.md)
