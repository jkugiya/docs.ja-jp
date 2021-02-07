---
description: '詳細情報: _CorValidateImage 関数'
title: _CorValidateImage 関数
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: f3d91c2d7e05786f7bfb0ab94b64e2cfb84a21d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746244"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="8b182-103">_CorValidateImage 関数</span><span class="sxs-lookup"><span data-stu-id="8b182-103">_CorValidateImage Function</span></span>

<span data-ttu-id="8b182-104">マネージド モジュール イメージを検証し、それらが読み込まれると、オペレーティング システム ローダーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8b182-104">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b182-105">構文</span><span class="sxs-lookup"><span data-stu-id="8b182-105">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b182-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b182-106">Parameters</span></span>  

 `ImageBase`  
 <span data-ttu-id="8b182-107">からマネージコードとして検証するイメージの開始位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8b182-107">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="8b182-108">イメージは既にメモリに読み込まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b182-108">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="8b182-109">からイメージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="8b182-109">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b182-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="8b182-110">Return Value</span></span>  

 <span data-ttu-id="8b182-111">この関数は、標準値、、 `E_INVALIDARG` `E_OUTOFMEMORY` 、およびを返し `E_UNEXPECTED` `E_FAIL` ます。次の値も返されます。</span><span class="sxs-lookup"><span data-stu-id="8b182-111">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="8b182-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="8b182-112">Return value</span></span>|<span data-ttu-id="8b182-113">説明</span><span class="sxs-lookup"><span data-stu-id="8b182-113">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="8b182-114">イメージが無効です。</span><span class="sxs-lookup"><span data-stu-id="8b182-114">The image is invalid.</span></span> <span data-ttu-id="8b182-115">この値には HRESULT 0xC000007BL があります。</span><span class="sxs-lookup"><span data-stu-id="8b182-115">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="8b182-116">イメージは有効です。</span><span class="sxs-lookup"><span data-stu-id="8b182-116">The image is valid.</span></span> <span data-ttu-id="8b182-117">この値には、HRESULT 0x00000000L が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8b182-117">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b182-118">解説</span><span class="sxs-lookup"><span data-stu-id="8b182-118">Remarks</span></span>  

 <span data-ttu-id="8b182-119">Windows XP 以降のバージョンでは、オペレーティングシステムローダーは、Common Object File Format (COFF) ヘッダーの COM 記述子ディレクトリビットを調べて、マネージモジュールをチェックします。</span><span class="sxs-lookup"><span data-stu-id="8b182-119">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="8b182-120">セットビットはマネージモジュールを示します。</span><span class="sxs-lookup"><span data-stu-id="8b182-120">A set bit indicates a managed module.</span></span> <span data-ttu-id="8b182-121">ローダーがマネージモジュールを検出すると、MsCorEE.dll を読み込み、 `_CorValidateImage` を呼び出します。これにより、次のアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="8b182-121">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="8b182-122">イメージが有効なマネージモジュールであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8b182-122">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="8b182-123">イメージのエントリポイントを共通言語ランタイム (CLR) のエントリポイントに変更します。</span><span class="sxs-lookup"><span data-stu-id="8b182-123">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="8b182-124">Windows の64ビットバージョンでは、PE32 から PE32 + 形式に変換することによって、メモリ内のイメージを変更します。</span><span class="sxs-lookup"><span data-stu-id="8b182-124">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="8b182-125">マネージモジュールイメージが読み込まれると、ローダーに戻ります。</span><span class="sxs-lookup"><span data-stu-id="8b182-125">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="8b182-126">実行可能イメージの場合、オペレーティングシステムローダーは、実行可能ファイルで指定されたエントリポイントに関係なく、 [_CorExeMain](corexemain-function.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8b182-126">For executable images, the operating system loader then calls the [_CorExeMain](corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="8b182-127">DLL アセンブリイメージの場合、ローダーは [_CorDllMain](cordllmain-function.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8b182-127">For DLL assembly images, the loader calls the [_CorDllMain](cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="8b182-128">`_CorExeMain` またはは `_CorDllMain` 、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="8b182-128">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="8b182-129">CLR を初期化します。</span><span class="sxs-lookup"><span data-stu-id="8b182-129">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="8b182-130">アセンブリの CLR ヘッダーからマネージエントリポイントを検索します。</span><span class="sxs-lookup"><span data-stu-id="8b182-130">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="8b182-131">実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="8b182-131">Begins execution.</span></span>  
  
 <span data-ttu-id="8b182-132">ローダーは、マネージモジュールイメージがアンロードされるときに [_CorImageUnloading](corimageunloading-function.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8b182-132">The loader calls the [_CorImageUnloading](corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="8b182-133">ただし、この関数は何のアクションも実行しません。これはだけを返します。</span><span class="sxs-lookup"><span data-stu-id="8b182-133">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b182-134">要件</span><span class="sxs-lookup"><span data-stu-id="8b182-134">Requirements</span></span>  

 <span data-ttu-id="8b182-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b182-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b182-136">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8b182-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b182-137">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8b182-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b182-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b182-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b182-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b182-139">See also</span></span>

- [<span data-ttu-id="8b182-140">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="8b182-140">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
