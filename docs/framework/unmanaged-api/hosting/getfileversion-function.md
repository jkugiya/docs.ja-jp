---
description: '詳細情報: GetFileVersion 関数'
title: GetFileVersion 関数
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: 7de19484f2f8123d61eb94e6a5ae09f56a3b5541
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785303"
---
# <a name="getfileversion-function"></a><span data-ttu-id="dc1d0-103">GetFileVersion 関数</span><span class="sxs-lookup"><span data-stu-id="dc1d0-103">GetFileVersion Function</span></span>

<span data-ttu-id="dc1d0-104">指定したバッファーを使用して、指定したファイルの共通言語ランタイム (CLR) のバージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc1d0-104">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="dc1d0-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="dc1d0-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc1d0-106">構文</span><span class="sxs-lookup"><span data-stu-id="dc1d0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc1d0-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc1d0-107">Parameters</span></span>  

 `szFilename`  
 <span data-ttu-id="dc1d0-108">から検査するファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="dc1d0-108">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="dc1d0-109">[入力、出力]返されたバージョン情報に割り当てられたバッファー。</span><span class="sxs-lookup"><span data-stu-id="dc1d0-109">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="dc1d0-110">からのサイズ (ワイド文字単位) `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="dc1d0-110">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="dc1d0-111">入出力返されたのサイズ (バイト単位) `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="dc1d0-111">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc1d0-112">要件</span><span class="sxs-lookup"><span data-stu-id="dc1d0-112">Requirements</span></span>  

 <span data-ttu-id="dc1d0-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc1d0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc1d0-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="dc1d0-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc1d0-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc1d0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1d0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc1d0-116">See also</span></span>

- [<span data-ttu-id="dc1d0-117">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="dc1d0-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
