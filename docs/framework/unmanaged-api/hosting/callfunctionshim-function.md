---
description: '詳細情報: CallFunctionShim 関数'
title: CallFunctionShim 関数
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
ms.openlocfilehash: 7ddd16a06005011adcf41190929fd62f4132f14d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799955"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="dbcb7-103">CallFunctionShim 関数</span><span class="sxs-lookup"><span data-stu-id="dbcb7-103">CallFunctionShim Function</span></span>

<span data-ttu-id="dbcb7-104">指定したライブラリ内の関数を、名前とパラメーターを指定して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-104">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="dbcb7-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbcb7-106">構文</span><span class="sxs-lookup"><span data-stu-id="dbcb7-106">Syntax</span></span>  
  
```cpp  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbcb7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dbcb7-107">Parameters</span></span>  

 `szDllName`  
 <span data-ttu-id="dbcb7-108">から関数を格納しているライブラリの名前。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-108">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="dbcb7-109">から関数の名前。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-109">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="dbcb7-110">から関数に渡す1番目の引数。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-110">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="dbcb7-111">から関数に渡す2番目の引数。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-111">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="dbcb7-112">から関数が含まれているライブラリのバージョン。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-112">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="dbcb7-113">から将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-113">[in] Reserved for future use.</span></span> <span data-ttu-id="dbcb7-114">このパラメーターに0を渡します。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-114">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbcb7-115">要件</span><span class="sxs-lookup"><span data-stu-id="dbcb7-115">Requirements</span></span>  

 <span data-ttu-id="dbcb7-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbcb7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbcb7-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="dbcb7-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbcb7-118">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbcb7-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbcb7-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbcb7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbcb7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbcb7-120">See also</span></span>

- [<span data-ttu-id="dbcb7-121">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="dbcb7-121">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
