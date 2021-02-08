---
description: '詳細情報: GetRequestedRuntimeVersion 関数'
title: GetRequestedRuntimeVersion 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 836cc4b875ddc427c6779950f5b68d2df8b6ef75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785277"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="7cf55-103">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="7cf55-103">GetRequestedRuntimeVersion Function</span></span>

<span data-ttu-id="7cf55-104">指定したアプリケーションによって要求された共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="7cf55-104">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="7cf55-105">そのバージョンがインストールされていない場合は、要求されるバージョンより前にインストールされた最も新しいバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="7cf55-105">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="7cf55-106">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="7cf55-106">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf55-107">構文</span><span class="sxs-lookup"><span data-stu-id="7cf55-107">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cf55-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7cf55-108">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="7cf55-109">からアプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="7cf55-109">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="7cf55-110">入出力正常に完了したときのバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="7cf55-110">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7cf55-111">からバージョンバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="7cf55-111">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="7cf55-112">入出力バージョン番号文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7cf55-112">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cf55-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="7cf55-113">Return Value</span></span>  

 <span data-ttu-id="7cf55-114">このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="7cf55-114">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="7cf55-115">リターン コード</span><span class="sxs-lookup"><span data-stu-id="7cf55-115">Return code</span></span>|<span data-ttu-id="7cf55-116">説明</span><span class="sxs-lookup"><span data-stu-id="7cf55-116">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7cf55-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="7cf55-117">S_OK</span></span>|<span data-ttu-id="7cf55-118">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="7cf55-118">The method completed successfully.</span></span>|  
|<span data-ttu-id="7cf55-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7cf55-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7cf55-120">バージョンバッファーが、バージョン文字列を格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="7cf55-120">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="7cf55-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7cf55-121">E_POINTER</span></span>|<span data-ttu-id="7cf55-122">`pdwLength` が null です。</span><span class="sxs-lookup"><span data-stu-id="7cf55-122">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7cf55-123">要件</span><span class="sxs-lookup"><span data-stu-id="7cf55-123">Requirements</span></span>  

 <span data-ttu-id="7cf55-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cf55-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf55-125">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7cf55-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cf55-126">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7cf55-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cf55-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cf55-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf55-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cf55-128">See also</span></span>

- [<span data-ttu-id="7cf55-129">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="7cf55-129">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="7cf55-130">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="7cf55-130">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="7cf55-131">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="7cf55-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
