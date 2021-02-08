---
description: '詳細情報: GetCORRequiredVersion 関数'
title: GetCORRequiredVersion 関数
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
ms.openlocfilehash: ea1b928054e3ec6080b00e2a41228035f50c0f84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785355"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="f9976-103">GetCORRequiredVersion 関数</span><span class="sxs-lookup"><span data-stu-id="f9976-103">GetCORRequiredVersion Function</span></span>

<span data-ttu-id="f9976-104">必要な共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="f9976-104">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="f9976-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="f9976-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9976-106">構文</span><span class="sxs-lookup"><span data-stu-id="f9976-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9976-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9976-107">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="f9976-108">入出力バージョン番号を指定する文字列を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="f9976-108">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f9976-109">からバッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="f9976-109">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="f9976-110">入出力バッファーで返されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="f9976-110">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9976-111">要件</span><span class="sxs-lookup"><span data-stu-id="f9976-111">Requirements</span></span>  

 <span data-ttu-id="f9976-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9976-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9976-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f9976-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9976-114">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f9976-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9976-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9976-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9976-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9976-116">See also</span></span>

- [<span data-ttu-id="f9976-117">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="f9976-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
