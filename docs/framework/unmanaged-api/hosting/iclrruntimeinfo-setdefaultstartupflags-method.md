---
description: '詳細について: ICLRRuntimeInfo:: SetDefaultStartupFlags メソッド'
title: ICLRRuntimeInfo::SetDefaultStartupFlags メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: eb839b2ff71836adc1b3858092f7caf5787275b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785043"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="a1138-103">ICLRRuntimeInfo::SetDefaultStartupFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="a1138-103">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>

<span data-ttu-id="a1138-104">ランタイムを開始するために使用されるスタートアップフラグとホスト構成ファイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="a1138-104">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="a1138-105">このメソッドは、 `startupFlags` [Corbindtoruntimeex](corbindtoruntimeex-function.md) および [Corbindtoruntimeex](corbindtoruntimehost-function.md) 関数でのパラメーターの使用よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="a1138-105">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1138-106">構文</span><span class="sxs-lookup"><span data-stu-id="a1138-106">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1138-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1138-107">Parameters</span></span>  

 `dwStartupFlags`  
 <span data-ttu-id="a1138-108">から設定するホストスタートアップフラグ。</span><span class="sxs-lookup"><span data-stu-id="a1138-108">[in] The host startup flags to set.</span></span> <span data-ttu-id="a1138-109">[Corbindtoruntimeex](corbindtoruntimeex-function.md)および[Corbindtoruntimeex](corbindtoruntimehost-function.md)関数と同じフラグを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1138-109">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="a1138-110">から設定するホスト構成ファイルのディレクトリパス。</span><span class="sxs-lookup"><span data-stu-id="a1138-110">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1138-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1138-111">Return Value</span></span>  

 <span data-ttu-id="a1138-112">このメソッドは、次の特定の HRESULT と、メソッドエラーを示す HRESULT エラーを返します。</span><span class="sxs-lookup"><span data-stu-id="a1138-112">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a1138-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1138-113">HRESULT</span></span>|<span data-ttu-id="a1138-114">説明</span><span class="sxs-lookup"><span data-stu-id="a1138-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1138-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1138-115">S_OK</span></span>|<span data-ttu-id="a1138-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="a1138-116">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1138-117">解説</span><span class="sxs-lookup"><span data-stu-id="a1138-117">Remarks</span></span>  

 <span data-ttu-id="a1138-118">マルチスレッドホストは、このメソッドの呼び出しを同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1138-118">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="a1138-119">それ以外の場合、スレッド B は、の `SetStartupFlags` 呼び出しを完了し `SetStartupFlags` てからランタイムを開始する前に、メソッドを呼び出すことがあります。</span><span class="sxs-lookup"><span data-stu-id="a1138-119">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1138-120">要件</span><span class="sxs-lookup"><span data-stu-id="a1138-120">Requirements</span></span>  

 <span data-ttu-id="a1138-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1138-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1138-122">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="a1138-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a1138-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a1138-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1138-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1138-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1138-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1138-125">See also</span></span>

- [<span data-ttu-id="a1138-126">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1138-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="a1138-127">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1138-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="a1138-128">ホスティング</span><span class="sxs-lookup"><span data-stu-id="a1138-128">Hosting</span></span>](index.md)
