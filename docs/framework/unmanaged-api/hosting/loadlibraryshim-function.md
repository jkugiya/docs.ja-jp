---
description: '詳細情報: LoadLibraryShim 関数'
title: LoadLibraryShim 関数
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
ms.openlocfilehash: 829d64b5215fc21b2d8c8b753f5ad99212267b6a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680006"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="68c5c-103">LoadLibraryShim 関数</span><span class="sxs-lookup"><span data-stu-id="68c5c-103">LoadLibraryShim Function</span></span>

<span data-ttu-id="68c5c-104">再頒布可能パッケージ .NET Framework に含まれている、指定したバージョンの DLL を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="68c5c-104">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="68c5c-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="68c5c-105">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="68c5c-106">代わりに [ICLRRuntimeInfo:: LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="68c5c-106">Use the [ICLRRuntimeInfo::LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c5c-107">構文</span><span class="sxs-lookup"><span data-stu-id="68c5c-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68c5c-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68c5c-108">Parameters</span></span>  

 `szDllName`  
 <span data-ttu-id="68c5c-109">から.NET Framework ライブラリから読み込む DLL の名前を表す、0で終わる文字列です。</span><span class="sxs-lookup"><span data-stu-id="68c5c-109">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="68c5c-110">から読み込む DLL のバージョンを表す、0で終わる文字列。</span><span class="sxs-lookup"><span data-stu-id="68c5c-110">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="68c5c-111">`szVersion`が null の場合、読み込み用に選択されたバージョンは、指定された DLL のうち、バージョン4より小さい最新バージョンです。</span><span class="sxs-lookup"><span data-stu-id="68c5c-111">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="68c5c-112">つまり、が null の場合、バージョン4以上のすべてのバージョンは無視され `szVersion` ます。バージョン4より前のバージョンがインストールされていない場合は、DLL の読み込みに失敗します。</span><span class="sxs-lookup"><span data-stu-id="68c5c-112">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="68c5c-113">これは、.NET Framework 4 のインストールが、既存のアプリケーションまたはコンポーネントに影響しないようにするためです。</span><span class="sxs-lookup"><span data-stu-id="68c5c-113">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="68c5c-114">CLR チームブログの「 [インプロセス SxS And Migration クイックスタート](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) 」のエントリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="68c5c-114">See the entry [In-Proc SxS and Migration Quick Start](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="68c5c-115">将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="68c5c-115">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="68c5c-116">入出力モジュールのハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="68c5c-116">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68c5c-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="68c5c-117">Return Value</span></span>  

 <span data-ttu-id="68c5c-118">このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="68c5c-118">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="68c5c-119">リターン コード</span><span class="sxs-lookup"><span data-stu-id="68c5c-119">Return code</span></span>|<span data-ttu-id="68c5c-120">説明</span><span class="sxs-lookup"><span data-stu-id="68c5c-120">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="68c5c-121">S_OK</span><span class="sxs-lookup"><span data-stu-id="68c5c-121">S_OK</span></span>|<span data-ttu-id="68c5c-122">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="68c5c-122">The method completed successfully.</span></span>|  
|<span data-ttu-id="68c5c-123">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="68c5c-123">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="68c5c-124">読み込みには `szDllName` 共通言語ランタイム (clr) を読み込む必要があり、必要なバージョンの clr を読み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="68c5c-124">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68c5c-125">解説</span><span class="sxs-lookup"><span data-stu-id="68c5c-125">Remarks</span></span>  

 <span data-ttu-id="68c5c-126">この関数は、.NET Framework 再頒布可能パッケージに含まれている Dll を読み込むために使用されます。</span><span class="sxs-lookup"><span data-stu-id="68c5c-126">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="68c5c-127">ユーザーが生成した Dll は読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="68c5c-127">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68c5c-128">.NET Framework バージョン2.0 以降では、Fusion.dll を読み込むと CLR が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="68c5c-128">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="68c5c-129">これは、Fusion.dll の関数が、ランタイムによって実装されているラッパーであるためです。</span><span class="sxs-lookup"><span data-stu-id="68c5c-129">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68c5c-130">要件</span><span class="sxs-lookup"><span data-stu-id="68c5c-130">Requirements</span></span>  

 <span data-ttu-id="68c5c-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68c5c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68c5c-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="68c5c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68c5c-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68c5c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c5c-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="68c5c-134">See also</span></span>

- [<span data-ttu-id="68c5c-135">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="68c5c-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
