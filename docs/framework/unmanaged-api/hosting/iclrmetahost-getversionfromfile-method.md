---
description: '詳細について: ICLRMetaHost:: GetVersionFromFile メソッド'
title: ICLRMetaHost::GetVersionFromFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
ms.openlocfilehash: 0122c4aba3b8454a84540b22e815c61a2cb25df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689054"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="0ff24-103">ICLRMetaHost::GetVersionFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="0ff24-103">ICLRMetaHost::GetVersionFromFile Method</span></span>

<span data-ttu-id="0ff24-104">ファイルパスを指定して、アセンブリの元の .NET Framework コンパイルバージョン (メタデータに格納されている) を取得します。</span><span class="sxs-lookup"><span data-stu-id="0ff24-104">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="0ff24-105">このメソッドは、 [GetFileVersion](getfileversion-function.md) 関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="0ff24-105">This method supersedes the [GetFileVersion](getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ff24-106">構文</span><span class="sxs-lookup"><span data-stu-id="0ff24-106">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ff24-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0ff24-107">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="0ff24-108">から完全なアセンブリファイルパス。</span><span class="sxs-lookup"><span data-stu-id="0ff24-108">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="0ff24-109">入出力メタデータに格納されている .NET Framework のコンパイルバージョン。 "v *A と* いう形式になります。*B*[.*X*] "</span><span class="sxs-lookup"><span data-stu-id="0ff24-109">[out] The .NET Framework compilation version stored in the metadata, in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="0ff24-110">*A*、 *B*、および *X* は、メジャーバージョン、マイナーバージョン、およびビルド番号に対応する10進数です。</span><span class="sxs-lookup"><span data-stu-id="0ff24-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="0ff24-111">この文字列の長さは MAX_PATH に制限されています。</span><span class="sxs-lookup"><span data-stu-id="0ff24-111">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ff24-112">この出力は、C:\Windows\Microsoft.NET\Framework. の下に表示される .NET Framework バージョンのディレクトリ名と一致します。</span><span class="sxs-lookup"><span data-stu-id="0ff24-112">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="0ff24-113">値の例としては、"v v1.0.3705"、"v 1.1.4322"、"v v2.0.50727"、および "v4.0" があります。*X*"。ここで *x* は、インストールされているビルド番号に依存します。</span><span class="sxs-lookup"><span data-stu-id="0ff24-113">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="0ff24-114">"V" プレフィックスが必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0ff24-114">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="0ff24-115">[入力、出力] `pwzbuffer` バッファーオーバーランを回避するためののサイズ。</span><span class="sxs-lookup"><span data-stu-id="0ff24-115">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ff24-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="0ff24-116">Return Value</span></span>  

 <span data-ttu-id="0ff24-117">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="0ff24-117">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0ff24-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ff24-118">HRESULT</span></span>|<span data-ttu-id="0ff24-119">説明</span><span class="sxs-lookup"><span data-stu-id="0ff24-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ff24-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ff24-120">S_OK</span></span>|<span data-ttu-id="0ff24-121">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="0ff24-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="0ff24-122">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0ff24-122">E_POINTER</span></span>|<span data-ttu-id="0ff24-123">`pwzbuffer` または `pcchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="0ff24-123">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="0ff24-124">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="0ff24-124">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="0ff24-125">バッファーが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="0ff24-125">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ff24-126">要件</span><span class="sxs-lookup"><span data-stu-id="0ff24-126">Requirements</span></span>  

 <span data-ttu-id="0ff24-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ff24-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ff24-128">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="0ff24-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0ff24-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0ff24-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ff24-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ff24-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff24-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ff24-131">See also</span></span>

- [<span data-ttu-id="0ff24-132">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ff24-132">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="0ff24-133">ホスティング</span><span class="sxs-lookup"><span data-stu-id="0ff24-133">Hosting</span></span>](index.md)
