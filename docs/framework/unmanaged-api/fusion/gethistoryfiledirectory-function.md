---
description: '詳細情報: GetHistoryFileDirectory 関数'
title: GetHistoryFileDirectory 関数
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
ms.openlocfilehash: 960bc75d69f4be6d1639e109d6327b5e65d3e129
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760967"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="64966-103">GetHistoryFileDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="64966-103">GetHistoryFileDirectory Function</span></span>

<span data-ttu-id="64966-104">アプリケーション履歴ディレクトリのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="64966-104">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64966-105">構文</span><span class="sxs-lookup"><span data-stu-id="64966-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64966-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64966-106">Parameters</span></span>  

 `wzDir`  
 <span data-ttu-id="64966-107">入出力アプリケーション履歴ディレクトリへのパスを保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="64966-107">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="64966-108">[入力、出力]バッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="64966-108">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64966-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="64966-109">Return Value</span></span>  

 <span data-ttu-id="64966-110">このメソッドは、Winerror.h ファイルで定義されているように、次の値に加えて、標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="64966-110">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="64966-111">リターン コード</span><span class="sxs-lookup"><span data-stu-id="64966-111">Return code</span></span>|<span data-ttu-id="64966-112">説明</span><span class="sxs-lookup"><span data-stu-id="64966-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="64966-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="64966-113">S_OK</span></span>|<span data-ttu-id="64966-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="64966-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="64966-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="64966-115">E_INVALIDARG</span></span>|<span data-ttu-id="64966-116">`wzDir` または `pdwSize` が null であるか、またはバージョン文字列が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="64966-116">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64966-117">解説</span><span class="sxs-lookup"><span data-stu-id="64966-117">Remarks</span></span>  

 <span data-ttu-id="64966-118">正常に完了すると、 `pdwSize` 引数はパス文字列の長さに設定されます。</span><span class="sxs-lookup"><span data-stu-id="64966-118">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64966-119">要件</span><span class="sxs-lookup"><span data-stu-id="64966-119">Requirements</span></span>  

 <span data-ttu-id="64966-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64966-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64966-121">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="64966-121">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="64966-122">**Library:** Fusion.dll し、Mscorwks.dll します。</span><span class="sxs-lookup"><span data-stu-id="64966-122">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="64966-123">Mscorwks.dll ではなく Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にするようにします。</span><span class="sxs-lookup"><span data-stu-id="64966-123">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="64966-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64966-124">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64966-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="64966-125">See also</span></span>

- [<span data-ttu-id="64966-126">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="64966-126">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="64966-127">NukeDownloadedCache 関数</span><span class="sxs-lookup"><span data-stu-id="64966-127">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="64966-128">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="64966-128">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
