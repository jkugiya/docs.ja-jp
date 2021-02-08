---
description: 詳細については、「GetVersionFromProcess 関数」を参照してください。
title: GetVersionFromProcess 関数
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: ab665d2984f79baf049009690b36782528094937
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785251"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="4128f-103">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="4128f-103">GetVersionFromProcess Function</span></span>

<span data-ttu-id="4128f-104">指定したプロセスハンドルに関連付けられている共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="4128f-104">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="4128f-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="4128f-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4128f-106">構文</span><span class="sxs-lookup"><span data-stu-id="4128f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4128f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4128f-107">Parameters</span></span>  

 `hProcess`  
 <span data-ttu-id="4128f-108">からプロセスを処理するハンドル。</span><span class="sxs-lookup"><span data-stu-id="4128f-108">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="4128f-109">入出力メソッドが正常に完了したときのバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="4128f-109">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="4128f-110">からバージョンバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="4128f-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="4128f-111">入出力バージョン番号文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4128f-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4128f-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="4128f-112">Return Value</span></span>  

 <span data-ttu-id="4128f-113">このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="4128f-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="4128f-114">リターン コード</span><span class="sxs-lookup"><span data-stu-id="4128f-114">Return code</span></span>|<span data-ttu-id="4128f-115">説明</span><span class="sxs-lookup"><span data-stu-id="4128f-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4128f-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="4128f-116">S_OK</span></span>|<span data-ttu-id="4128f-117">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="4128f-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="4128f-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4128f-118">E_INVALIDARG</span></span>|<span data-ttu-id="4128f-119">`pVersion` が null で `cchBuffer` あり、が null ではないか、またはその逆です。</span><span class="sxs-lookup"><span data-stu-id="4128f-119">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="4128f-120">\- または -</span><span class="sxs-lookup"><span data-stu-id="4128f-120">-or-</span></span><br /><br /> <span data-ttu-id="4128f-121">`hProcess` は、プロセスへの有効なハンドルではありません。</span><span class="sxs-lookup"><span data-stu-id="4128f-121">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="4128f-122">\- または -</span><span class="sxs-lookup"><span data-stu-id="4128f-122">-or-</span></span><br /><br /> <span data-ttu-id="4128f-123">CLR が読み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="4128f-123">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="4128f-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4128f-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4128f-125">`cchBuffer` が null であるか、またはバージョン文字列の長さを下回っています。</span><span class="sxs-lookup"><span data-stu-id="4128f-125">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="4128f-126">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4128f-126">E_NOTIMPL</span></span>|<span data-ttu-id="4128f-127">この方法は、Microsoft Windows 95、Microsoft Windows 98、または Microsoft Windows Millennium Edition オペレーティングシステムでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="4128f-127">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4128f-128">要件</span><span class="sxs-lookup"><span data-stu-id="4128f-128">Requirements</span></span>  

 <span data-ttu-id="4128f-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4128f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4128f-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4128f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4128f-131">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4128f-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4128f-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4128f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4128f-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="4128f-133">See also</span></span>

- [<span data-ttu-id="4128f-134">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="4128f-134">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="4128f-135">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="4128f-135">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="4128f-136">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="4128f-136">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
