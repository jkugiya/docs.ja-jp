---
description: '詳細について: ICLRAssemblyReferenceList:: IsStringAssemblyReferenceInList メソッド'
title: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
ms.openlocfilehash: 667764337fbda22a526e51575faf049efc4b86ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790036"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="f272e-103">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="f272e-103">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>

<span data-ttu-id="f272e-104">指定された名前がリスト内のアセンブリの名前と一致するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="f272e-104">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f272e-105">構文</span><span class="sxs-lookup"><span data-stu-id="f272e-105">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f272e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f272e-106">Parameters</span></span>  

 `pwzAssemblyName`  
 <span data-ttu-id="f272e-107">から検索対象のアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="f272e-107">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f272e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f272e-108">Return Value</span></span>  
  
|<span data-ttu-id="f272e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f272e-109">HRESULT</span></span>|<span data-ttu-id="f272e-110">説明</span><span class="sxs-lookup"><span data-stu-id="f272e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f272e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f272e-111">S_OK</span></span>|<span data-ttu-id="f272e-112">文字列が一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f272e-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="f272e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f272e-113">S_FALSE</span></span>|<span data-ttu-id="f272e-114">文字列は一覧に表示されません。</span><span class="sxs-lookup"><span data-stu-id="f272e-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="f272e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f272e-115">E_FAIL</span></span>|<span data-ttu-id="f272e-116">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f272e-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f272e-117">メソッドが E_FAIL を返すと、そのプロセス内で共通言語ランタイムは使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f272e-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="f272e-118">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f272e-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f272e-119">要件</span><span class="sxs-lookup"><span data-stu-id="f272e-119">Requirements</span></span>  

 <span data-ttu-id="f272e-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f272e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f272e-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f272e-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f272e-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f272e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f272e-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f272e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f272e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f272e-124">See also</span></span>

- [<span data-ttu-id="f272e-125">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f272e-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="f272e-126">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f272e-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f272e-127">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f272e-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="f272e-128">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f272e-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
