---
description: '詳細について: ICLRAssemblyReferenceList:: IsAssemblyReferenceInList メソッド'
title: ICLRAssemblyReferenceList::IsAssemblyReferenceInList メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
ms.openlocfilehash: ce90423715d6cbe07c1112cb2136c11fd58c982a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716771"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="63d9c-103">ICLRAssemblyReferenceList::IsAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="63d9c-103">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>

<span data-ttu-id="63d9c-104">指定されたポインターがリスト内のアセンブリを参照しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="63d9c-104">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63d9c-105">構文</span><span class="sxs-lookup"><span data-stu-id="63d9c-105">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63d9c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63d9c-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="63d9c-107">から検索対象のアセンブリへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="63d9c-107">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="63d9c-108">有効な値は `IAssemblyName` 、型または型です `IReferenceIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="63d9c-108">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63d9c-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="63d9c-109">Return Value</span></span>  
  
|<span data-ttu-id="63d9c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63d9c-110">HRESULT</span></span>|<span data-ttu-id="63d9c-111">説明</span><span class="sxs-lookup"><span data-stu-id="63d9c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63d9c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="63d9c-112">S_OK</span></span>|<span data-ttu-id="63d9c-113">文字列が一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="63d9c-113">The string appears in the list.</span></span>|  
|<span data-ttu-id="63d9c-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="63d9c-114">S_FALSE</span></span>|<span data-ttu-id="63d9c-115">文字列は一覧に表示されません。</span><span class="sxs-lookup"><span data-stu-id="63d9c-115">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="63d9c-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="63d9c-116">E_FAIL</span></span>|<span data-ttu-id="63d9c-117">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="63d9c-117">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="63d9c-118">メソッドが E_FAIL を返すと、そのプロセス内で共通言語ランタイムは使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="63d9c-118">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="63d9c-119">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="63d9c-119">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63d9c-120">要件</span><span class="sxs-lookup"><span data-stu-id="63d9c-120">Requirements</span></span>  

 <span data-ttu-id="63d9c-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63d9c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63d9c-122">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="63d9c-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63d9c-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="63d9c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63d9c-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63d9c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d9c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="63d9c-125">See also</span></span>

- [<span data-ttu-id="63d9c-126">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63d9c-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="63d9c-127">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63d9c-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="63d9c-128">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63d9c-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="63d9c-129">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63d9c-129">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
