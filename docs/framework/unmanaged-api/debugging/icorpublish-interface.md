---
description: 詳細については、「ICorPublish インターフェイス」を参照してください。
title: ICorPublish インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 0cec1d3407246989c6b916ca0760e6f556566ce6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721828"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="7fb1e-103">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7fb1e-103">ICorPublish Interface</span></span>

<span data-ttu-id="7fb1e-104">プロセスに関する情報、およびそれらのプロセス内のアプリケーションドメインに関する情報を公開するための一般的なインターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-104">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fb1e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7fb1e-105">Methods</span></span>  
  
|<span data-ttu-id="7fb1e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7fb1e-106">Method</span></span>|<span data-ttu-id="7fb1e-107">説明</span><span class="sxs-lookup"><span data-stu-id="7fb1e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fb1e-108">EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="7fb1e-108">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="7fb1e-109">このコンピューター上で実行されているマネージプロセスを含む [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-109">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="7fb1e-110">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="7fb1e-110">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="7fb1e-111">指定した識別子を持つプロセスを表す [ICorPublishProcess](icorpublishprocess-interface.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-111">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fb1e-112">要件</span><span class="sxs-lookup"><span data-stu-id="7fb1e-112">Requirements</span></span>  

 <span data-ttu-id="7fb1e-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fb1e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fb1e-114">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="7fb1e-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7fb1e-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fb1e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fb1e-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fb1e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb1e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fb1e-117">See also</span></span>

- [<span data-ttu-id="7fb1e-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7fb1e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7fb1e-119">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="7fb1e-119">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
