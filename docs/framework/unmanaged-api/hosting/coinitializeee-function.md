---
description: '詳細情報: CoInitializeEE 関数'
title: CoInitializeEE 関数
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9664324c569ed4de73262491cf8eda8296b3c3a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799825"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="1ce9f-103">CoInitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="1ce9f-103">CoInitializeEE Function</span></span>

<span data-ttu-id="1ce9f-104">共通言語ランタイムの実行エンジンが確実にプロセスに読み込まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-104">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="1ce9f-105">この関数は .NET Framework 4 では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-105">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="1ce9f-106">代わりに [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-106">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ce9f-107">構文</span><span class="sxs-lookup"><span data-stu-id="1ce9f-107">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ce9f-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ce9f-108">Parameters</span></span>  

 `fFlags`  
 <span data-ttu-id="1ce9f-109">から [Coinitiee](../metadata/coinitiee-enumeration.md) 列挙定数の1つ。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-109">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ce9f-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ce9f-110">Return Value</span></span>  

 <span data-ttu-id="1ce9f-111">このメソッドは、Winerror.h で定義されている標準 COM エラーコードと、次の表の値を返します。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-111">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="1ce9f-112">リターン コード</span><span class="sxs-lookup"><span data-stu-id="1ce9f-112">Return code</span></span>|<span data-ttu-id="1ce9f-113">説明</span><span class="sxs-lookup"><span data-stu-id="1ce9f-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1ce9f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ce9f-114">S_OK</span></span>|<span data-ttu-id="1ce9f-115">実行エンジンが正常に読み込まれました。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-115">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="1ce9f-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1ce9f-116">S_FALSE</span></span>|<span data-ttu-id="1ce9f-117">実行エンジンは既に読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-117">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="1ce9f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ce9f-118">E_FAIL</span></span>|<span data-ttu-id="1ce9f-119">実行エンジンを読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-119">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ce9f-120">解説</span><span class="sxs-lookup"><span data-stu-id="1ce9f-120">Remarks</span></span>  

 <span data-ttu-id="1ce9f-121">このメソッドは、まだ読み込まれていない場合、実行エンジンを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-121">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ce9f-122">要件</span><span class="sxs-lookup"><span data-stu-id="1ce9f-122">Requirements</span></span>  

 <span data-ttu-id="1ce9f-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ce9f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ce9f-124">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1ce9f-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ce9f-125">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1ce9f-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ce9f-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ce9f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce9f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ce9f-127">See also</span></span>

- [<span data-ttu-id="1ce9f-128">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="1ce9f-128">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
