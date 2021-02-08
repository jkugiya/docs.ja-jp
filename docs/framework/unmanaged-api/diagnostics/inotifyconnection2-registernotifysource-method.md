---
description: '詳細について: INotifyConnection2:: RegisterNotifySource メソッド'
title: INotifyConnection2::RegisterNotifySource メソッド
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: 97aacf7f2005a1e9f21acebd6c5f5ed65867b245
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800319"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="f3f65-103">INotifyConnection2::RegisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="f3f65-103">INotifyConnection2::RegisterNotifySource Method</span></span>

<span data-ttu-id="f3f65-104">指定された通知ソースをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f3f65-104">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3f65-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3f65-105">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3f65-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3f65-106">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="f3f65-107">から通知ソースとして使用するオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="f3f65-107">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="f3f65-108">入出力通知シンクとして使用されるオブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f3f65-108">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3f65-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f3f65-109">Return Value</span></span>  

 <span data-ttu-id="f3f65-110">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="f3f65-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3f65-111">要件</span><span class="sxs-lookup"><span data-stu-id="f3f65-111">Requirements</span></span>  

 <span data-ttu-id="f3f65-112">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="f3f65-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f65-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3f65-113">See also</span></span>

- [<span data-ttu-id="f3f65-114">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3f65-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="f3f65-115">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3f65-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="f3f65-116">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3f65-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="f3f65-117">UnregisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="f3f65-117">UnregisterNotifySource Method</span></span>](inotifyconnection2-unregisternotifysource-method.md)
