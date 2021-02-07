---
description: 詳細については、「ICLRRuntimeInfo インターフェイス」を参照してください。
title: ICLRRuntimeInfo インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: d599c743e5a42801321ea487fdd9e52bfcfaf081
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753862"
---
# <a name="iclrruntimeinfo-interface"></a><span data-ttu-id="dbd9a-103">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dbd9a-103">ICLRRuntimeInfo Interface</span></span>

<span data-ttu-id="dbd9a-104">バージョン、ディレクトリ、読み込み状態など、特定の共通言語ランタイム (CLR) に関する情報を返すメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-104">Provides methods that return information about a specific common language runtime (CLR), including version, directory, and load status.</span></span> <span data-ttu-id="dbd9a-105">このインターフェイスは、ランタイムを初期化せずにランタイム固有の機能も提供します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-105">This interface also provides runtime-specific functionality without initializing the runtime.</span></span> <span data-ttu-id="dbd9a-106">これには、ランタイム相対 [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) メソッド、ランタイムモジュール固有の [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) メソッド、および [getinterface](iclrruntimeinfo-getinterface-method.md) メソッドを使用したランタイム提供のインターフェイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-106">It includes the runtime-relative [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) method, the runtime module-specific [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method, and runtime-provided interfaces through the [GetInterface](iclrruntimeinfo-getinterface-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbd9a-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-107">Methods</span></span>  
  
|<span data-ttu-id="dbd9a-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-108">Method</span></span>|<span data-ttu-id="dbd9a-109">説明</span><span class="sxs-lookup"><span data-stu-id="dbd9a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbd9a-110">BindAsLegacyV2Runtime メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-110">BindAsLegacyV2Runtime Method</span></span>](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|<span data-ttu-id="dbd9a-111">すべてのレガシ CLR バージョン2アクティブ化ポリシーの決定にこのランタイムをバインドします。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-111">Binds this runtime for all legacy CLR version 2 activation policy decisions.</span></span>|  
|[<span data-ttu-id="dbd9a-112">GetDefaultStartupFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-112">GetDefaultStartupFlags Method</span></span>](iclrruntimeinfo-getdefaultstartupflags-method.md)|<span data-ttu-id="dbd9a-113">CLR スタートアップフラグとホスト構成ファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-113">Gets the CLR startup flags and host configuration file.</span></span>|  
|[<span data-ttu-id="dbd9a-114">GetInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-114">GetInterface Method</span></span>](iclrruntimeinfo-getinterface-method.md)|<span data-ttu-id="dbd9a-115">現在のプロセスに CLR を読み込み、 [ICLRRuntimeHost](iclrruntimehost-interface.md)、 [ICLRStrongName](iclrstrongname-interface.md) 、 [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md)などのランタイムインターフェイスポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-115">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) and [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md).</span></span> <span data-ttu-id="dbd9a-116">このメソッドは、すべての関数を置き換え `CorBindTo*` ます。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-116">This method supersedes all the `CorBindTo*` functions.</span></span>|  
|[<span data-ttu-id="dbd9a-117">GetProcAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-117">GetProcAddress Method</span></span>](iclrruntimeinfo-getprocaddress-method.md)|<span data-ttu-id="dbd9a-118">このインターフェイスに関連付けられている CLR からエクスポートされた、指定された関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-118">Gets the address of a specified function that was exported from the CLR associated with this interface.</span></span> <span data-ttu-id="dbd9a-119">このメソッドは、 [GetRealProcAddress](getrealprocaddress-function.md) メソッドよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-119">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) method.</span></span>|  
|[<span data-ttu-id="dbd9a-120">GetRuntimeDirectory メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-120">GetRuntimeDirectory Method</span></span>](iclrruntimeinfo-getruntimedirectory-method.md)|<span data-ttu-id="dbd9a-121">このインターフェイスに関連付けられている CLR のインストールディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-121">Gets the installation directory of the CLR associated with this interface.</span></span> <span data-ttu-id="dbd9a-122">このメソッドは、 [Getcorsystemdirectory](getcorsystemdirectory-function.md) メソッドよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-122">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) method.</span></span>|  
|[<span data-ttu-id="dbd9a-123">GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-123">GetVersionString Method</span></span>](iclrruntimeinfo-getversionstring-method.md)|<span data-ttu-id="dbd9a-124">指定した [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスに関連付けられている共通言語ランタイム (CLR) のバージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-124">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span> <span data-ttu-id="dbd9a-125">このメソッドは、 [Getrequestedruntimeinfo](getrequestedruntimeinfo-function.md) および [Getrequestedruntimeinfo](getrequestedruntimeversion-function.md) メソッドを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-125">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) and [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) methods.</span></span>|  
|[<span data-ttu-id="dbd9a-126">IsLoadable メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-126">IsLoadable Method</span></span>](iclrruntimeinfo-isloadable-method.md)|<span data-ttu-id="dbd9a-127">このインターフェイスに関連付けられているランタイムを現在のプロセスに読み込むことができるかどうかを示します。プロセスに既に読み込まれている可能性のある他のランタイムを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-127">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>|  
|[<span data-ttu-id="dbd9a-128">IsLoaded メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-128">IsLoaded Method</span></span>](iclrruntimeinfo-isloaded-method.md)|<span data-ttu-id="dbd9a-129">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)インターフェイスに関連付けられている CLR がプロセスに読み込まれているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-129">Indicates whether the CLR associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span>|  
|[<span data-ttu-id="dbd9a-130">IsStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-130">IsStarted Method</span></span>](iclrruntimeinfo-isstarted-method.md)|<span data-ttu-id="dbd9a-131">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)インターフェイスに関連付けられている CLR が開始されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-131">Indicates whether the CLR that is associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface has been started.</span></span>|  
|[<span data-ttu-id="dbd9a-132">LoadErrorString メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-132">LoadErrorString Method</span></span>](iclrruntimeinfo-loaderrorstring-method.md)|<span data-ttu-id="dbd9a-133">HRESULT 値を、指定したカルチャの適切なエラーメッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-133">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span> <span data-ttu-id="dbd9a-134">このメソッドは、 [LoadStringRC](loadstringrc-function.md) メソッドと [LoadStringRCEx](loadstringrcex-function.md) メソッドよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-134">This method supersedes the [LoadStringRC](loadstringrc-function.md) and [LoadStringRCEx](loadstringrcex-function.md) methods.</span></span>|  
|[<span data-ttu-id="dbd9a-135">LoadLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-135">LoadLibrary Method</span></span>](iclrruntimeinfo-loadlibrary-method.md)|<span data-ttu-id="dbd9a-136">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)インターフェイスによって表される CLR のフレームワークディレクトリからライブラリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-136">Loads a library from the framework directory of the CLR represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span> <span data-ttu-id="dbd9a-137">このメソッドは、 [LoadLibraryShim](loadlibraryshim-function.md) メソッドよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-137">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) method.</span></span>|  
|[<span data-ttu-id="dbd9a-138">SetDefaultStartupFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="dbd9a-138">SetDefaultStartupFlags Method</span></span>](iclrruntimeinfo-setdefaultstartupflags-method.md)|<span data-ttu-id="dbd9a-139">CLR スタートアップフラグとホスト構成ファイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-139">Sets the CLR startup flags and host configuration file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dbd9a-140">要件</span><span class="sxs-lookup"><span data-stu-id="dbd9a-140">Requirements</span></span>  

 <span data-ttu-id="dbd9a-141">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbd9a-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbd9a-142">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="dbd9a-142">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dbd9a-143">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="dbd9a-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbd9a-144">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbd9a-144">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd9a-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbd9a-145">See also</span></span>

- [<span data-ttu-id="dbd9a-146">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dbd9a-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="dbd9a-147">ホスティング</span><span class="sxs-lookup"><span data-stu-id="dbd9a-147">Hosting</span></span>](index.md)
