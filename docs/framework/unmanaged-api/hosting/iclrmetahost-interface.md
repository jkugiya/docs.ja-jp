---
description: 詳細については、「ICLRMetaHost インターフェイス」を参照してください。
title: ICLRMetaHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: 5dc50af85c067bcb525414e47cddd34070b83a27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637509"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="ade2b-103">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ade2b-103">ICLRMetaHost Interface</span></span>

<span data-ttu-id="ade2b-104">バージョン番号に基づいて特定のバージョンの共通言語ランタイム (CLR) を返すメソッド、インストールされているすべての CLRs の一覧表示、指定されたプロセスに読み込まれたすべてのランタイムの一覧表示、アセンブリをコンパイルするために使用される CLR バージョンの検出、クリーンランタイムシャットダウンを使用したプロセスの終了、従来の API バインディングのクエリを</span><span class="sxs-lookup"><span data-stu-id="ade2b-104">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ade2b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ade2b-105">Methods</span></span>  
  
|<span data-ttu-id="ade2b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ade2b-106">Method</span></span>|<span data-ttu-id="ade2b-107">説明</span><span class="sxs-lookup"><span data-stu-id="ade2b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ade2b-108">EnumerateInstalledRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="ade2b-108">EnumerateInstalledRuntimes Method</span></span>](iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="ade2b-109">コンピューターにインストールされている各 CLR バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスポインターを含む列挙を返します。</span><span class="sxs-lookup"><span data-stu-id="ade2b-109">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="ade2b-110">EnumerateLoadedRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="ade2b-110">EnumerateLoadedRuntimes Method</span></span>](iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="ade2b-111">指定されたプロセスに読み込まれる各 CLR の有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスポインターを含む列挙体を返します。</span><span class="sxs-lookup"><span data-stu-id="ade2b-111">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="ade2b-112">このメソッドは、 [Getversionfromprocess](getversionfromprocess-function.md)よりも優先します。</span><span class="sxs-lookup"><span data-stu-id="ade2b-112">This method supersedes [GetVersionFromProcess](getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="ade2b-113">ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="ade2b-113">ExitProcess Method</span></span>](iclrmetahost-exitprocess-method.md)|<span data-ttu-id="ade2b-114">読み込まれたすべてのランタイムを正常にシャットダウンしてから、プロセスを終了しようとします。</span><span class="sxs-lookup"><span data-stu-id="ade2b-114">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="ade2b-115">[CorExitProcess](corexitprocess-function.md)関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="ade2b-115">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="ade2b-116">GetRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="ade2b-116">GetRuntime Method</span></span>](iclrmetahost-getruntime-method.md)|<span data-ttu-id="ade2b-117">特定の CLR バージョンに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ade2b-117">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="ade2b-118">このメソッドは、 [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)フラグと共に使用される[Corbindtoruntimeex](corbindtoruntimeex-function.md)関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="ade2b-118">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="ade2b-119">GetVersionFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="ade2b-119">GetVersionFromFile Method</span></span>](iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="ade2b-120">ファイルパスを指定して、アセンブリの元の .NET Framework コンパイルバージョン (メタデータに格納されている) を取得します。</span><span class="sxs-lookup"><span data-stu-id="ade2b-120">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="ade2b-121">このメソッドは、 [GetFileVersion](getfileversion-function.md)よりも優先します。</span><span class="sxs-lookup"><span data-stu-id="ade2b-121">This method supersedes [GetFileVersion](getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="ade2b-122">QueryLegacyV2RuntimeBinding メソッド</span><span class="sxs-lookup"><span data-stu-id="ade2b-122">QueryLegacyV2RuntimeBinding Method</span></span>](iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="ade2b-123">レガシアクティブ化ポリシーがバインドされているランタイムを表すインターフェイスを返します。たとえば、 `useLegacyV2RuntimeActivationPolicy` [ \<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)構成ファイルのエントリで属性を使用したり、レガシアクティベーション api を直接使用したり、 [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md)メソッドを呼び出したりします。</span><span class="sxs-lookup"><span data-stu-id="ade2b-123">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="ade2b-124">RequestRuntimeLoadedNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="ade2b-124">RequestRuntimeLoadedNotification Method</span></span>](iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="ade2b-125">CLR バージョンが最初に読み込まれたが、まだ開始されていない場合は、指定された関数ポインターへのコールバックを保証します。</span><span class="sxs-lookup"><span data-stu-id="ade2b-125">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="ade2b-126">このメソッドは、 [Lockclrversion](lockclrversion-function.md)を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ade2b-126">This method supersedes [LockClrVersion](lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ade2b-127">解説</span><span class="sxs-lookup"><span data-stu-id="ade2b-127">Remarks</span></span>  

 <span data-ttu-id="ade2b-128">このインターフェイスのインスタンスを取得する唯一の方法は、 [Clrcreateinstance](clrcreateinstance-function.md) 関数を次のように呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ade2b-128">The only way to get an instance of this interface is by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ade2b-129">要件</span><span class="sxs-lookup"><span data-stu-id="ade2b-129">Requirements</span></span>  

 <span data-ttu-id="ade2b-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ade2b-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade2b-131">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="ade2b-131">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ade2b-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ade2b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ade2b-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade2b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade2b-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ade2b-134">See also</span></span>

- [<span data-ttu-id="ade2b-135">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ade2b-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ade2b-136">ホスティング</span><span class="sxs-lookup"><span data-stu-id="ade2b-136">Hosting</span></span>](index.md)
