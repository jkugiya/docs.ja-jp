---
description: '詳細について: ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList メソッド'
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
ms.openlocfilehash: 91f7b9eaacee559c5e404b5dda0f8b4201f91a66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649560"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="81ea6-103">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList メソッド</span><span class="sxs-lookup"><span data-stu-id="81ea6-103">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>

<span data-ttu-id="81ea6-104">指定された部分アセンブリ id のリストから、 [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="81ea6-104">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81ea6-105">構文</span><span class="sxs-lookup"><span data-stu-id="81ea6-105">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81ea6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81ea6-106">Parameters</span></span>  

 `ppwzAssemblyReferences`  
 <span data-ttu-id="81ea6-107">から"Name, property = value..." の形式で、null で終わる文字列の配列部分アセンブリ id の一覧を指定する。</span><span class="sxs-lookup"><span data-stu-id="81ea6-107">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="81ea6-108">から内の項目の数 `ppwzAssemblyReferences` 。</span><span class="sxs-lookup"><span data-stu-id="81ea6-108">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="81ea6-109">入出力 `ICLRAssemblyReferenceList` で指定されたアセンブリの一覧のアセンブリ id データを格納しているオブジェクトへのインターフェイスポインター `ppwzAssemblyReferences` 。</span><span class="sxs-lookup"><span data-stu-id="81ea6-109">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81ea6-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="81ea6-110">Return Value</span></span>  
  
|<span data-ttu-id="81ea6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81ea6-111">HRESULT</span></span>|<span data-ttu-id="81ea6-112">説明</span><span class="sxs-lookup"><span data-stu-id="81ea6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81ea6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="81ea6-113">S_OK</span></span>|<span data-ttu-id="81ea6-114">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="81ea6-114">The method returned successfully.</span></span>|  
|<span data-ttu-id="81ea6-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81ea6-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81ea6-116">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="81ea6-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81ea6-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81ea6-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81ea6-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="81ea6-118">The call timed out.</span></span>|  
|<span data-ttu-id="81ea6-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81ea6-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81ea6-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="81ea6-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81ea6-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81ea6-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81ea6-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="81ea6-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81ea6-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81ea6-123">E_FAIL</span></span>|<span data-ttu-id="81ea6-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="81ea6-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81ea6-125">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="81ea6-125">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81ea6-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="81ea6-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81ea6-127">要件</span><span class="sxs-lookup"><span data-stu-id="81ea6-127">Requirements</span></span>  

 <span data-ttu-id="81ea6-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81ea6-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81ea6-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="81ea6-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81ea6-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="81ea6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81ea6-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81ea6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ea6-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="81ea6-132">See also</span></span>

- [<span data-ttu-id="81ea6-133">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81ea6-133">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="81ea6-134">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81ea6-134">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
