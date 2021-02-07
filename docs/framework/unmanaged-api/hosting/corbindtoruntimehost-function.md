---
description: 詳細については、「CorBindToRuntimeHost 関数」を参照してください。
title: CorBindToRuntimeHost 関数
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
ms.openlocfilehash: 1921eece4c6fa7f1a8fc851f17ce8f9708bc49d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717161"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="87e16-103">CorBindToRuntimeHost 関数</span><span class="sxs-lookup"><span data-stu-id="87e16-103">CorBindToRuntimeHost Function</span></span>

<span data-ttu-id="87e16-104">ホストが、指定したバージョンの共通言語ランタイム (CLR: Common Language Runtime) をプロセスに読み込むことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="87e16-104">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="87e16-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="87e16-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e16-106">構文</span><span class="sxs-lookup"><span data-stu-id="87e16-106">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,
    [in] LPCWSTR       pwszBuildFlavor,
    [in] LPCWSTR       pwszHostConfigFile,
    [in] VOID*         pReserved,
    [in] DWORD         startupFlags,
    [in] REFCLSID      rclsid,
    [in] REFIID        riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87e16-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87e16-107">Parameters</span></span>  

 `pwszVersion`  
 <span data-ttu-id="87e16-108">[入力] 読み込む CLR のバージョンを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="87e16-108">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="87e16-109">.NET Framework のバージョン番号は、ピリオドで *区切られた* 4 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="87e16-109">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="87e16-110">`pwszVersion` として渡される文字列は、文字 "v" で始まり、バージョン番号の最初の 3 つの部分がその後に続く必要があります (たとえば "v1.0.1529")。</span><span class="sxs-lookup"><span data-stu-id="87e16-110">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="87e16-111">いくつかのバージョンの CLR は、以前のバージョンの CLR との互換性を指定するポリシー ステートメントと共にインストールされています。</span><span class="sxs-lookup"><span data-stu-id="87e16-111">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="87e16-112">既定では、スタートアップ shim により、ポリシー ステートメントに対して `pwszVersion` が評価され、要求されたバージョンと互換性がある最新バージョンのランタイムが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="87e16-112">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="87e16-113">ホストは shim に対し、`pwszVersion` パラメーターで値 STARTUP_LOADER_SAFEMODE を渡すことにより、ポリシー評価を省略し、`startupFlags` で指定されたバージョンとまったく同じバージョンを読み込ませることができます。</span><span class="sxs-lookup"><span data-stu-id="87e16-113">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="87e16-114">`pwszVersion` が `null,` の場合、メソッドはどのバージョンの CLR も読み込みません。</span><span class="sxs-lookup"><span data-stu-id="87e16-114">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="87e16-115">代わりに、ランタイムの読み込みに失敗したことを示す CLR_E_SHIM_RUNTIMELOAD が返されます。</span><span class="sxs-lookup"><span data-stu-id="87e16-115">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="87e16-116">[入力] CLR のサーバー ビルドまたはワークステーション ビルドのどちらを読み込むかを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="87e16-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="87e16-117">有効な値は `svr` と `wks` です。</span><span class="sxs-lookup"><span data-stu-id="87e16-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="87e16-118">ワークステーション ビルドはシングルプロセッサ コンピューターでクライアント アプリケーションを実行するために最適化され、サーバー ビルドはガベージ コレクションでマルチ プロセッサを利用するために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="87e16-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="87e16-119">`pwszBuildFlavor`が null に設定されている場合、ワークステーションのビルドが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="87e16-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="87e16-120">をシングルプロセッサコンピューターで実行する場合、がに設定されていても、ワークステーションのビルドは常に読み込まれ `pwszBuildFlavor` `svr` ます。</span><span class="sxs-lookup"><span data-stu-id="87e16-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="87e16-121">ただし、 `pwszBuildFlavor` がに設定され、 `svr` 同時実行ガベージコレクションが指定されている場合 (パラメーターの説明を参照 `startupFlags` )、サーバービルドが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="87e16-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87e16-122">同時実行ガベージ コレクションは、Intel Itanium アーキテクチャ (以前の IA-64) を実装する 64 ビット システム上で WOW64 x86 エミュレーターを実行しているアプリケーションではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="87e16-122">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="87e16-123">64ビット Windows システムでの WOW64 の使用の詳細については、「 [32 ビットアプリケーションの実行](/windows/desktop/WinProg64/running-32-bit-applications)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87e16-123">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="87e16-124">[入力] 読み込む CLR のバージョンを指定するホスト構成ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="87e16-124">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="87e16-125">ファイル名に絶対パスが含まれていない場合、ファイルは呼び出しを行った実行可能ファイルと同じディレクトリにあるものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="87e16-125">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="87e16-126">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="87e16-126">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="87e16-127">[入力] 同時実行ガベージ コレクション、ドメインに中立なコード、および `pwszVersion` パラメーターの動作を制御するフラグのセット。</span><span class="sxs-lookup"><span data-stu-id="87e16-127">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="87e16-128">どのフラグも設定されていない場合は、既定はシングル ドメインになります。</span><span class="sxs-lookup"><span data-stu-id="87e16-128">The default is single domain if no flag is set.</span></span> <span data-ttu-id="87e16-129">サポートされている値の一覧については、 [STARTUP_FLAGS 列挙体](startup-flags-enumeration.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87e16-129">For a list of supported values, see the [STARTUP_FLAGS enumeration](startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="87e16-130">から `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) または [ICLRRuntimeHost](iclrruntimehost-interface.md) のいずれかのインターフェイスを実装するコクラスの。</span><span class="sxs-lookup"><span data-stu-id="87e16-130">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="87e16-131">サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="87e16-131">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="87e16-132">[入力] 要求するインターフェイスの `IID`。</span><span class="sxs-lookup"><span data-stu-id="87e16-132">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="87e16-133">サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。</span><span class="sxs-lookup"><span data-stu-id="87e16-133">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="87e16-134">[出力] 読み込まれたランタイムのバージョンへのインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="87e16-134">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e16-135">要件</span><span class="sxs-lookup"><span data-stu-id="87e16-135">Requirements</span></span>  

 <span data-ttu-id="87e16-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87e16-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e16-137">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="87e16-137">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="87e16-138">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="87e16-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87e16-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e16-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e16-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="87e16-140">See also</span></span>

- [<span data-ttu-id="87e16-141">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="87e16-141">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="87e16-142">CorBindToRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="87e16-142">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="87e16-143">CorBindToRuntimeByCfg 関数</span><span class="sxs-lookup"><span data-stu-id="87e16-143">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="87e16-144">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="87e16-144">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="87e16-145">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87e16-145">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="87e16-146">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="87e16-146">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
