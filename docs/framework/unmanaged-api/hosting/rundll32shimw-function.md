---
description: '詳細情報: RunDll32ShimW 関数'
title: RunDll32ShimW 関数
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
ms.openlocfilehash: d01021358a6cddf15d1a0e1b223c9acff3c64ff7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679499"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="6250e-103">RunDll32ShimW 関数</span><span class="sxs-lookup"><span data-stu-id="6250e-103">RunDll32ShimW Function</span></span>

<span data-ttu-id="6250e-104">指定されたコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6250e-104">Executes the specified command.</span></span>  
  
 <span data-ttu-id="6250e-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="6250e-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6250e-106">構文</span><span class="sxs-lookup"><span data-stu-id="6250e-106">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6250e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6250e-107">Parameters</span></span>  

 `hwnd`  
 <span data-ttu-id="6250e-108">からコマンドの出力が表示されるウィンドウへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="6250e-108">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="6250e-109">からコマンドが格納されているライブラリへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="6250e-109">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="6250e-110">から実行するコマンドを指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="6250e-110">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="6250e-111">から出力ウィンドウの表示モードを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="6250e-111">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6250e-112">要件</span><span class="sxs-lookup"><span data-stu-id="6250e-112">Requirements</span></span>  

 <span data-ttu-id="6250e-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6250e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6250e-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6250e-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6250e-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6250e-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6250e-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6250e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6250e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6250e-117">See also</span></span>

- [<span data-ttu-id="6250e-118">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="6250e-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
