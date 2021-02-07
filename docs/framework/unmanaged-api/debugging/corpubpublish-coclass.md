---
description: '詳細については、次を参照してください: CorpubPublish コクラス'
title: CorpubPublish コクラス
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: fdf4be6ff2d20391e989998cd0045ed27d602561
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661689"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="83db2-103">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="83db2-103">CorpubPublish Coclass</span></span>

<span data-ttu-id="83db2-104">アプリケーション ドメインとプロセスに関する情報を発行するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="83db2-104">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83db2-105">構文</span><span class="sxs-lookup"><span data-stu-id="83db2-105">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="83db2-106">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83db2-106">Interfaces</span></span>  
  
|<span data-ttu-id="83db2-107">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83db2-107">Interface</span></span>|<span data-ttu-id="83db2-108">説明</span><span class="sxs-lookup"><span data-stu-id="83db2-108">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="83db2-109">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83db2-109">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="83db2-110">プロセスおよびプロセス内のアプリケーションドメインに関する情報を公開するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="83db2-110">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="83db2-111">ICorPublishAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83db2-111">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="83db2-112">プロセス内のアプリケーションドメインに関する情報を表し、提供します。</span><span class="sxs-lookup"><span data-stu-id="83db2-112">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="83db2-113">ICorPublishAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83db2-113">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="83db2-114">プロセス内に現在存在するアプリケーションドメインのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="83db2-114">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="83db2-115">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83db2-115">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="83db2-116">コンピューター上で実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="83db2-116">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="83db2-117">ICorPublishProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83db2-117">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="83db2-118">コンピューター上で実行されているプロセスのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="83db2-118">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83db2-119">解説</span><span class="sxs-lookup"><span data-stu-id="83db2-119">Remarks</span></span>  

 <span data-ttu-id="83db2-120">一般的な発行シナリオでは、開発者がアプリケーションドメイン内のコンピューターで実行されているマネージコードをデバッグする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83db2-120">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="83db2-121">ホスト環境で、プロセス内で複数のアプリケーションドメインが実行されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="83db2-121">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="83db2-122">開発者は、コンピューター上で実行されているすべてのプロセスを一覧表示し、特定のプロセスを選択するために、グラフィカルユーザーインターフェイスまたはその他の方法を使用したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="83db2-122">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="83db2-123">この一覧には、マネージコードを実行しているプロセス内のすべてのアプリケーションドメインが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="83db2-123">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="83db2-124">開発者は、特定のアプリケーションドメインを特定し、そのドメインにデバッガーをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="83db2-124">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83db2-125">要件</span><span class="sxs-lookup"><span data-stu-id="83db2-125">Requirements</span></span>  

 <span data-ttu-id="83db2-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83db2-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83db2-127">**ヘッダー:** CorPub .idl</span><span class="sxs-lookup"><span data-stu-id="83db2-127">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="83db2-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83db2-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83db2-129">**.NET Framework のバージョン:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83db2-129">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83db2-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="83db2-130">See also</span></span>

- [<span data-ttu-id="83db2-131">デバッグ</span><span class="sxs-lookup"><span data-stu-id="83db2-131">Debugging</span></span>](index.md)
