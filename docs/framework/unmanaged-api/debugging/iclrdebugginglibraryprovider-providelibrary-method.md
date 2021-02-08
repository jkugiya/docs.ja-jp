---
description: '詳細について: ICLRDebuggingLibraryProvider::P rovideLibrary メソッド'
title: ICLRDebuggingLibraryProvider::ProvideLibrary メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
ms.openlocfilehash: 624061fb9b23af7a69616d4565586ac0fd129860
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772621"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="9c9a5-103">ICLRDebuggingLibraryProvider::ProvideLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="9c9a5-103">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="9c9a5-104">共通言語ランタイム (CLR) のバージョン固有のデバッグライブラリをオンデマンドで検索して読み込むことができるようにする、ライブラリプロバイダーのコールバックインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-104">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c9a5-105">構文</span><span class="sxs-lookup"><span data-stu-id="9c9a5-105">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="9c9a5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c9a5-106">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="9c9a5-107">から要求されているモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-107">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="9c9a5-108">からPE ファイルの COFF ファイルヘッダーに格納されている日付と時刻のタイムスタンプ。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-108">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="9c9a5-109">から `SizeOfImage` PE ファイルの COFF オプションファイルヘッダーに格納されているフィールド。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-109">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="9c9a5-110">入出力要求されたモジュールへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-110">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="9c9a5-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="9c9a5-111">Return Value</span></span>

<span data-ttu-id="9c9a5-112">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="9c9a5-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c9a5-113">HRESULT</span></span>|<span data-ttu-id="9c9a5-114">説明</span><span class="sxs-lookup"><span data-stu-id="9c9a5-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="9c9a5-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c9a5-115">S_OK</span></span>|<span data-ttu-id="9c9a5-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-116">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="9c9a5-117">例外</span><span class="sxs-lookup"><span data-stu-id="9c9a5-117">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="9c9a5-118">解説</span><span class="sxs-lookup"><span data-stu-id="9c9a5-118">Remarks</span></span>

<span data-ttu-id="9c9a5-119">`ProvideLibrary` mscordbi.dll や mscordacwks.dll などの特定の CLR ファイルをデバッグするために必要なモジュールをデバッガーが提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-119">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="9c9a5-120">モジュールハンドルは、 [ICLRDebugging:: CanUnloadNow](iclrdebugging-canunloadnow-method.md) メソッドの呼び出しによって解放される可能性があることが示されるまで有効なままにしておく必要があります。その時点で、呼び出し元がハンドルを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-120">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="9c9a5-121">デバッガーは、使用可能な任意の方法を使用して、デバッグモジュールを見つけたり調達したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-121">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c9a5-122">この機能により、API 呼び出し元は、実行可能ファイルや悪意のあるコードを含むモジュールを提供できます。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-122">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="9c9a5-123">セキュリティ上の理由から、呼び出し元はを使用して、それ `ProvideLibrary` 自体を実行しないコードを配布することはできません。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-123">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="9c9a5-124">mscordbi.dll や mscordacwks.dll など、既にリリースされているライブラリで深刻なセキュリティの問題が検出された場合、shim には、不適切なバージョンのファイルを認識するように修正プログラムを適用できます。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-124">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="9c9a5-125">その後、shim は、修正されたバージョンのファイルに対する要求を発行し、要求に応答して指定されている場合は無効なバージョンを拒否します。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-125">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="9c9a5-126">これは、ユーザーが shim の新しいバージョンに修正プログラムを適用している場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-126">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="9c9a5-127">修正プログラム脆弱性のバージョンは脆弱なままです。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-127">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="9c9a5-128">要件</span><span class="sxs-lookup"><span data-stu-id="9c9a5-128">Requirements</span></span>

<span data-ttu-id="9c9a5-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c9a5-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9c9a5-130">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c9a5-130">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="9c9a5-131">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c9a5-131">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9c9a5-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c9a5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9c9a5-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c9a5-133">See also</span></span>

- [<span data-ttu-id="9c9a5-134">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c9a5-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9c9a5-135">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9c9a5-135">Debugging</span></span>](index.md)
