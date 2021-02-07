---
description: '詳細情報: METAHOST_POLICY_FLAGS 列挙型'
title: METAHOST_POLICY_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
ms.openlocfilehash: 3a3ebe602c8f048b7f9fc907f5d4741722bd0ed3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679623"
---
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="e0629-103">METAHOST_POLICY_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="e0629-103">METAHOST_POLICY_FLAGS Enumeration</span></span>

<span data-ttu-id="e0629-104">ほとんどのランタイムホストに共通のバインドポリシーを提供します。</span><span class="sxs-lookup"><span data-stu-id="e0629-104">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="e0629-105">この列挙体は、 [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0629-105">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0629-106">構文</span><span class="sxs-lookup"><span data-stu-id="e0629-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e0629-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e0629-107">Members</span></span>  
  
|<span data-ttu-id="e0629-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="e0629-108">Member</span></span>|<span data-ttu-id="e0629-109">説明</span><span class="sxs-lookup"><span data-stu-id="e0629-109">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="e0629-110">現在のプロセスに読み込まれる共通言語ランタイム (CLR: common language runtime) を考慮しない、互換性の高いポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="e0629-110">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="e0629-111">代わりに、インストールされた CLRs と、コンポーネントの設定 (アセンブリファイル自体、宣言された組み込みバージョン、または構成ファイルから派生したもの) のみを考慮します。</span><span class="sxs-lookup"><span data-stu-id="e0629-111">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="e0629-112">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoftの内容に基づいて完全一致が見つからなかった場合に、バージョンのバインド結果にアップグレードポリシーを適用し \\ ます。NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="e0629-112">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="e0629-113">これは [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md)と同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="e0629-113">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="e0629-114">呼び出しに対して指定されたイメージが新しいプロセスで起動されたかのように、バインディングの結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="e0629-114">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="e0629-115">現在、は、一連の `GetRequestedRuntime` 読み込み可能なランタイムを無視し、インストールされている一連のランタイムに対してバインドします。</span><span class="sxs-lookup"><span data-stu-id="e0629-115">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="e0629-116">このフラグにより、ホストは、起動時に EXE がバインドされるランタイムを決定できます。</span><span class="sxs-lookup"><span data-stu-id="e0629-116">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="e0629-117">入力パラメーターと互換性のあるランタイムが見つからない場合、エラーダイアログボックスが表示され `GetRequestedRuntime` ます。</span><span class="sxs-lookup"><span data-stu-id="e0629-117">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="e0629-118">.NET Framework 4.5 以降、このエラーダイアログボックスには、ユーザーが適切な機能を有効にするかどうかを確認する Windows の機能ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0629-118">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="e0629-119">`GetRequestedRuntime` は、プロセスイメージ (およびそれに対応するすべての構成ファイル) をバインドプロセスへの追加入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="e0629-119">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="e0629-120">既定で `GetRequestedRuntime` は、は、バインド先のランタイムを決定するときに、プロセスイメージパス (通常はプロセスの起動に使用された EXE) にフォールバックしません。</span><span class="sxs-lookup"><span data-stu-id="e0629-120">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="e0629-121">`GetRequestedRuntime` 構成ファイルに利用できる情報がない場合に、適切な SKU がインストールされているかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0629-121">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="e0629-122">これにより、構成ファイルを持たないアプリケーションは、.NET Framework の既定のインストールよりも小さい Sku では正常に機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="e0629-122">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="e0629-123">既定で `GetRequestedRuntime` は、構成ファイル要素で sku 属性が指定されていない限り、は適切な sku がインストールされているかどうかを確認しません `<supportedRuntime />` 。</span><span class="sxs-lookup"><span data-stu-id="e0629-123">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="e0629-124">`GetRequestedRuntime` SEM_FAILCRITICALERRORS ( [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) 関数の呼び出しによって設定される) を無視し、エラーダイアログボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="e0629-124">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function), and show the error dialog box.</span></span> <span data-ttu-id="e0629-125">既定では、SEM_FAILCRITICALERRORS はエラーダイアログボックスを表示しません。</span><span class="sxs-lookup"><span data-stu-id="e0629-125">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="e0629-126">このファイルは別のプロセスから継承されている可能性があり、シナリオによってはサイレントエラーが望ましくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0629-126">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0629-127">解説</span><span class="sxs-lookup"><span data-stu-id="e0629-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0629-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="e0629-128">Requirements</span></span>  

 <span data-ttu-id="e0629-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0629-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0629-130">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="e0629-130">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="e0629-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e0629-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0629-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0629-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0629-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0629-133">See also</span></span>

- [<span data-ttu-id="e0629-134">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="e0629-134">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="e0629-135">GetRequestedRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="e0629-135">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
