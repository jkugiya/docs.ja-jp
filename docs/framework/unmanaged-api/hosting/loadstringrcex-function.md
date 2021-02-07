---
description: '詳細情報: LoadStringRCEx 関数'
title: LoadStringRCEx 関数
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: d3fe4b97014e5093dd8d209a5e27bac4ed7b879f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679915"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="66e66-103">LoadStringRCEx 関数</span><span class="sxs-lookup"><span data-stu-id="66e66-103">LoadStringRCEx Function</span></span>

<span data-ttu-id="66e66-104">HRESULT 値を、指定したカルチャの適切なエラー メッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="66e66-104">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="66e66-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="66e66-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e66-106">構文</span><span class="sxs-lookup"><span data-stu-id="66e66-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66e66-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66e66-107">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="66e66-108">からカルチャ識別子。</span><span class="sxs-lookup"><span data-stu-id="66e66-108">[in] A culture identifier.</span></span> <span data-ttu-id="66e66-109">既定のカルチャを使用するには、に-1 を渡し `lcid` ます。</span><span class="sxs-lookup"><span data-stu-id="66e66-109">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="66e66-110">からHRESULT。</span><span class="sxs-lookup"><span data-stu-id="66e66-110">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="66e66-111">入出力正常に完了したときのエラーメッセージを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="66e66-111">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="66e66-112">からエラーメッセージバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="66e66-112">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="66e66-113">から無効.</span><span class="sxs-lookup"><span data-stu-id="66e66-113">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="66e66-114">入出力エラーメッセージの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="66e66-114">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66e66-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="66e66-115">Return Value</span></span>  

 <span data-ttu-id="66e66-116">このメソッドは、次の値に加えて、Winerror.h で定義されている標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="66e66-116">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="66e66-117">リターン コード</span><span class="sxs-lookup"><span data-stu-id="66e66-117">Return code</span></span>|<span data-ttu-id="66e66-118">説明</span><span class="sxs-lookup"><span data-stu-id="66e66-118">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="66e66-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="66e66-119">S_OK</span></span>|<span data-ttu-id="66e66-120">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="66e66-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="66e66-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="66e66-121">E_INVALIDARG</span></span>|<span data-ttu-id="66e66-122">`szBuffer` が null であるか、または `iMax` がゼロ (0) です。</span><span class="sxs-lookup"><span data-stu-id="66e66-122">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66e66-123">解説</span><span class="sxs-lookup"><span data-stu-id="66e66-123">Remarks</span></span>  

 <span data-ttu-id="66e66-124">メソッドが正常に完了しなかった場合、には `szBuffer` 空の文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="66e66-124">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e66-125">要件</span><span class="sxs-lookup"><span data-stu-id="66e66-125">Requirements</span></span>  

 <span data-ttu-id="66e66-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66e66-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e66-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="66e66-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66e66-128">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66e66-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66e66-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e66-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e66-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="66e66-130">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="66e66-131">LoadStringRC 関数</span><span class="sxs-lookup"><span data-stu-id="66e66-131">LoadStringRC Function</span></span>](loadstringrc-function.md)
- [<span data-ttu-id="66e66-132">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="66e66-132">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
