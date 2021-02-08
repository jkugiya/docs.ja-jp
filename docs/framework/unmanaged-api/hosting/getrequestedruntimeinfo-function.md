---
description: 詳細については、「GetRequestedRuntimeInfo 関数」を参照してください。
title: GetRequestedRuntimeInfo 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
ms.openlocfilehash: 63d0bdcd07be5727cddc0acc352e8358b5ff0090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785290"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="ad454-103">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="ad454-103">GetRequestedRuntimeInfo Function</span></span>

<span data-ttu-id="ad454-104">アプリケーションによって要求された共通言語ランタイム (CLR) に関するバージョンとディレクトリ情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="ad454-104">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="ad454-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="ad454-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad454-106">構文</span><span class="sxs-lookup"><span data-stu-id="ad454-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,
    [in]  LPCWSTR  pwszVersion,
    [in]  LPCWSTR  pConfigurationFile,
    [in]  DWORD    startupFlags,
    [in]  DWORD    runtimeInfoFlags,
    [out] LPWSTR   pDirectory,
    [in]  DWORD    dwDirectory,
    [out] DWORD   *dwDirectoryLength,
    [out] LPWSTR   pVersion,
    [in]  DWORD    cchBuffer,
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad454-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad454-107">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="ad454-108">からアプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="ad454-108">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="ad454-109">からランタイムのバージョン番号を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="ad454-109">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="ad454-110">からに関連付けられている構成ファイルの名前 `pExe` 。</span><span class="sxs-lookup"><span data-stu-id="ad454-110">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="ad454-111">から1つ以上の [STARTUP_FLAGS](startup-flags-enumeration.md) 列挙値。</span><span class="sxs-lookup"><span data-stu-id="ad454-111">[in] One or more of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="ad454-112">から1つ以上の [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) 列挙値。</span><span class="sxs-lookup"><span data-stu-id="ad454-112">[in] One or more of the [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="ad454-113">入出力正常に完了したときのランタイムへのディレクトリパスを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="ad454-113">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="ad454-114">からディレクトリバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="ad454-114">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="ad454-115">入出力ディレクトリパス文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad454-115">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="ad454-116">入出力正常に完了したときのランタイムのバージョン番号を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="ad454-116">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ad454-117">からバージョン文字列バッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="ad454-117">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="ad454-118">入出力バージョン文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad454-118">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad454-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad454-119">Return Value</span></span>  

 <span data-ttu-id="ad454-120">このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="ad454-120">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="ad454-121">リターン コード</span><span class="sxs-lookup"><span data-stu-id="ad454-121">Return code</span></span>|<span data-ttu-id="ad454-122">説明</span><span class="sxs-lookup"><span data-stu-id="ad454-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ad454-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad454-123">S_OK</span></span>|<span data-ttu-id="ad454-124">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="ad454-124">The method completed successfully.</span></span>|  
|<span data-ttu-id="ad454-125">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ad454-125">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ad454-126">ディレクトリのバッファーが、ディレクトリパスを格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="ad454-126">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="ad454-127">または</span><span class="sxs-lookup"><span data-stu-id="ad454-127">- or -</span></span><br /><br /> <span data-ttu-id="ad454-128">バージョンバッファーが、バージョン文字列を格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="ad454-128">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad454-129">解説</span><span class="sxs-lookup"><span data-stu-id="ad454-129">Remarks</span></span>  

 <span data-ttu-id="ad454-130">メソッドは、 `GetRequestedRuntimeInfo` プロセスに読み込まれたバージョンに関するランタイム情報を返します。これは、必ずしもコンピューターにインストールされている最新バージョンではありません。</span><span class="sxs-lookup"><span data-stu-id="ad454-130">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="ad454-131">.NET Framework バージョン2.0 では、次の方法でメソッドを使用して、インストールされている最新のバージョンに関する情報を取得でき `GetRequestedRuntimeInfo` ます。</span><span class="sxs-lookup"><span data-stu-id="ad454-131">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="ad454-132">`pExe`、 `pwszVersion` 、およびの各 `pConfigurationFile` パラメーターを null として指定します。</span><span class="sxs-lookup"><span data-stu-id="ad454-132">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="ad454-133">パラメーターの列挙に RUNTIME_INFO_UPGRADE_VERSION フラグを指定し `RUNTIME_INFO_FLAGS` `runtimeInfoFlags` ます。</span><span class="sxs-lookup"><span data-stu-id="ad454-133">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="ad454-134">メソッドは、 `GetRequestedRuntimeInfo` 次のような状況では、最新の CLR バージョンを返しません。</span><span class="sxs-lookup"><span data-stu-id="ad454-134">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="ad454-135">特定の CLR バージョンの読み込みを指定するアプリケーション構成ファイルが存在します。</span><span class="sxs-lookup"><span data-stu-id="ad454-135">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="ad454-136">パラメーターに null を指定した場合でも、.NET Framework は構成ファイルを使用することに注意 `pConfigurationFile` してください。</span><span class="sxs-lookup"><span data-stu-id="ad454-136">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="ad454-137">[Corbindtoruntimeex](corbindtoruntimeex-function.md)メソッドが、以前の CLR バージョンを指定して呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="ad454-137">The [CorBindToRuntimeEx](corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="ad454-138">以前のバージョンの CLR 用にコンパイルされたアプリケーションが現在実行されています。</span><span class="sxs-lookup"><span data-stu-id="ad454-138">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="ad454-139">パラメーターの場合 `runtimeInfoFlags` 、列挙体のアーキテクチャ定数は一度に1つだけ指定でき `RUNTIME_INFO_FLAGS` ます。</span><span class="sxs-lookup"><span data-stu-id="ad454-139">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="ad454-140">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="ad454-140">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="ad454-141">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="ad454-141">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="ad454-142">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="ad454-142">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad454-143">要件</span><span class="sxs-lookup"><span data-stu-id="ad454-143">Requirements</span></span>  

 <span data-ttu-id="ad454-144">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad454-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad454-145">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ad454-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad454-146">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad454-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad454-147">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad454-147">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad454-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad454-148">See also</span></span>

- [<span data-ttu-id="ad454-149">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="ad454-149">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="ad454-150">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="ad454-150">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="ad454-151">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="ad454-151">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
