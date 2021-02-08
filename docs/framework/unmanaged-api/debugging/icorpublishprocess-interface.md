---
description: 詳細については、「ICorPublishProcess インターフェイス」を参照してください。
title: ICorPublishProcess インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 8dbc619d33c2c9b625dde852948dff00b5be926e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800878"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="2b2ee-103">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b2ee-103">ICorPublishProcess Interface</span></span>

<span data-ttu-id="2b2ee-104">プロセスについて表示される情報にアクセスするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="2b2ee-104">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b2ee-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2b2ee-105">Methods</span></span>  
  
|<span data-ttu-id="2b2ee-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2b2ee-106">Method</span></span>|<span data-ttu-id="2b2ee-107">説明</span><span class="sxs-lookup"><span data-stu-id="2b2ee-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b2ee-108">EnumAppDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="2b2ee-108">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="2b2ee-109">このによって参照されるプロセス内のアプリケーションドメインを格納している [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) インスタンスを取得し `ICorPublishProcess` ます。</span><span class="sxs-lookup"><span data-stu-id="2b2ee-109">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="2b2ee-110">GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="2b2ee-110">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="2b2ee-111">このによって参照されるプロセスの実行可能ファイルの完全パスを取得し `ICorPublishProcess` ます。</span><span class="sxs-lookup"><span data-stu-id="2b2ee-111">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="2b2ee-112">GetProcessID メソッド</span><span class="sxs-lookup"><span data-stu-id="2b2ee-112">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="2b2ee-113">このによって参照されるプロセスのオペレーティングシステム識別子を取得し `ICorPublishProcess` ます。</span><span class="sxs-lookup"><span data-stu-id="2b2ee-113">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="2b2ee-114">IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="2b2ee-114">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="2b2ee-115">このによって参照されるプロセス `ICorPublishProcess` がマネージコードを実行していることがわかっているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="2b2ee-115">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b2ee-116">要件</span><span class="sxs-lookup"><span data-stu-id="2b2ee-116">Requirements</span></span>  

 <span data-ttu-id="2b2ee-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b2ee-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b2ee-118">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="2b2ee-118">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2b2ee-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b2ee-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b2ee-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b2ee-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b2ee-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b2ee-121">See also</span></span>

- [<span data-ttu-id="2b2ee-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b2ee-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2b2ee-123">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="2b2ee-123">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
