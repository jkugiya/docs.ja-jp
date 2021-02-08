---
description: '詳細情報: GetRealProcAddress 関数'
title: GetRealProcAddress 関数
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
ms.openlocfilehash: b8b3db77d6aef7fae3045a7aa2310c1fadc70e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785316"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="7a424-103">GetRealProcAddress 関数</span><span class="sxs-lookup"><span data-stu-id="7a424-103">GetRealProcAddress Function</span></span>

<span data-ttu-id="7a424-104">インストールされている最新バージョンの共通言語ランタイム (CLR) からエクスポートされた、指定された関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="7a424-104">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="7a424-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="7a424-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a424-106">構文</span><span class="sxs-lookup"><span data-stu-id="7a424-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a424-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a424-107">Parameters</span></span>  

 `pwszProcName`  
 <span data-ttu-id="7a424-108">から関数の名前。</span><span class="sxs-lookup"><span data-stu-id="7a424-108">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="7a424-109">入出力関数のアドレスへのポインターを受け取る位置。</span><span class="sxs-lookup"><span data-stu-id="7a424-109">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a424-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="7a424-110">Return Value</span></span>  

 <span data-ttu-id="7a424-111">このメソッドは、Winerror.h で定義されているように、CorError. h で定義されている次の値に加えて、標準の Component Object Model (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="7a424-111">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="7a424-112">リターン コード</span><span class="sxs-lookup"><span data-stu-id="7a424-112">Return code</span></span>|<span data-ttu-id="7a424-113">説明</span><span class="sxs-lookup"><span data-stu-id="7a424-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7a424-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a424-114">S_OK</span></span>|<span data-ttu-id="7a424-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="7a424-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="7a424-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7a424-116">E_POINTER</span></span>|<span data-ttu-id="7a424-117">`ppv` が無効です。</span><span class="sxs-lookup"><span data-stu-id="7a424-117">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="7a424-118">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="7a424-118">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="7a424-119">関数はランタイムからエクスポートされません。</span><span class="sxs-lookup"><span data-stu-id="7a424-119">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a424-120">要件</span><span class="sxs-lookup"><span data-stu-id="7a424-120">Requirements</span></span>  

 <span data-ttu-id="7a424-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a424-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a424-122">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7a424-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a424-123">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a424-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a424-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a424-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a424-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a424-125">See also</span></span>

- [<span data-ttu-id="7a424-126">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="7a424-126">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
