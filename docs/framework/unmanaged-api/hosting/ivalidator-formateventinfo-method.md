---
description: '詳細情報: IValidator:: FormatEventInfo メソッド'
title: IValidator::FormatEventInfo メソッド
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: 28ecf9ab2b14cd2fdd178a4ad9d8e218f7038a9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680162"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="2590d-103">IValidator::FormatEventInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="2590d-103">IValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="2590d-104">指定した検証エラーに対応するエラーメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="2590d-104">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2590d-105">構文</span><span class="sxs-lookup"><span data-stu-id="2590d-105">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2590d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2590d-106">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="2590d-107">から検証エラーハンドラーに渡された HRESULT 値。</span><span class="sxs-lookup"><span data-stu-id="2590d-107">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="2590d-108">から `VEContext` 検証エラーに関するコンテキスト情報を格納しているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="2590d-108">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="2590d-109">[入力、出力]返されたエラーメッセージを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="2590d-109">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="2590d-110">からエラーメッセージの最大長。</span><span class="sxs-lookup"><span data-stu-id="2590d-110">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="2590d-111">からエラーを説明する追加のパラメーターを格納しているセーフ配列。</span><span class="sxs-lookup"><span data-stu-id="2590d-111">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2590d-112">要件</span><span class="sxs-lookup"><span data-stu-id="2590d-112">Requirements</span></span>  

 <span data-ttu-id="2590d-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2590d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2590d-114">**ヘッダー:** IValidator、IValidator</span><span class="sxs-lookup"><span data-stu-id="2590d-114">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="2590d-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2590d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2590d-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2590d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
