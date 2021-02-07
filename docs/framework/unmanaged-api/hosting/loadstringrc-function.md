---
description: '詳細情報: LoadStringRC 関数'
title: LoadStringRC 関数
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 188597f9dc21b6a67fb84e91cd66b50ba5a514f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679919"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="1fdd7-103">LoadStringRC 関数</span><span class="sxs-lookup"><span data-stu-id="1fdd7-103">LoadStringRC Function</span></span>

<span data-ttu-id="1fdd7-104">現在のスレッドの既定のカルチャを使用して、HRESULT 値をエラー メッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-104">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="1fdd7-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fdd7-106">構文</span><span class="sxs-lookup"><span data-stu-id="1fdd7-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fdd7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1fdd7-107">Parameters</span></span>  

 `iResourceID`  
 <span data-ttu-id="1fdd7-108">からHRESULT。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-108">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="1fdd7-109">入出力正常に完了したときのエラーメッセージを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-109">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="1fdd7-110">からエラーメッセージバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-110">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="1fdd7-111">から無効.</span><span class="sxs-lookup"><span data-stu-id="1fdd7-111">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fdd7-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="1fdd7-112">Return Value</span></span>  

 <span data-ttu-id="1fdd7-113">このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="1fdd7-114">リターン コード</span><span class="sxs-lookup"><span data-stu-id="1fdd7-114">Return code</span></span>|<span data-ttu-id="1fdd7-115">説明</span><span class="sxs-lookup"><span data-stu-id="1fdd7-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1fdd7-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="1fdd7-116">S_OK</span></span>|<span data-ttu-id="1fdd7-117">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="1fdd7-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1fdd7-118">E_INVALIDARG</span></span>|<span data-ttu-id="1fdd7-119">`szBuffer` が null または `iMax` がゼロ (0) です。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-119">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fdd7-120">解説</span><span class="sxs-lookup"><span data-stu-id="1fdd7-120">Remarks</span></span>  

 <span data-ttu-id="1fdd7-121">メソッドが正常に完了しなかった場合、には `szBuffer` 空の文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-121">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fdd7-122">要件</span><span class="sxs-lookup"><span data-stu-id="1fdd7-122">Requirements</span></span>  

 <span data-ttu-id="1fdd7-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fdd7-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1fdd7-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1fdd7-125">**Library:** MSCorEE.dll し、Mscorwks.dll します。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-125">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="1fdd7-126">Mscorwks.dll ではなく MSCorEE.dll を使用して、正しいバージョンの .NET Framework を対象にするようにします。</span><span class="sxs-lookup"><span data-stu-id="1fdd7-126">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="1fdd7-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fdd7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fdd7-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fdd7-128">See also</span></span>

- [<span data-ttu-id="1fdd7-129">LoadStringRCEx 関数</span><span class="sxs-lookup"><span data-stu-id="1fdd7-129">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)
- [<span data-ttu-id="1fdd7-130">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="1fdd7-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
