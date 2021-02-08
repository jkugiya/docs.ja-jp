---
description: '詳細情報: StrongNameHashSize 関数'
title: StrongNameHashSize 関数
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
ms.openlocfilehash: 3e6700bfce3ba480814f3837011c5f8f7107bbd5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781240"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="0eeac-103">StrongNameHashSize 関数</span><span class="sxs-lookup"><span data-stu-id="0eeac-103">StrongNameHashSize Function</span></span>

<span data-ttu-id="0eeac-104">指定したハッシュ アルゴリズムを使用して、ハッシュに必須のバッファー サイズが取得されます。</span><span class="sxs-lookup"><span data-stu-id="0eeac-104">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="0eeac-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="0eeac-105">This function has been deprecated.</span></span> <span data-ttu-id="0eeac-106">代わりに [ICLRStrongName:: StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="0eeac-106">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eeac-107">構文</span><span class="sxs-lookup"><span data-stu-id="0eeac-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eeac-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0eeac-108">Parameters</span></span>  

 `ulHashAlg`  
 <span data-ttu-id="0eeac-109">からバッファーサイズを計算するために使用されるハッシュアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="0eeac-109">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="0eeac-110">入出力返されたバッファーサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="0eeac-110">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eeac-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="0eeac-111">Return Value</span></span>  

 <span data-ttu-id="0eeac-112">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="0eeac-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0eeac-113">解説</span><span class="sxs-lookup"><span data-stu-id="0eeac-113">Remarks</span></span>  

 <span data-ttu-id="0eeac-114">関数が `StrongNameHashSize` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="0eeac-114">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eeac-115">要件</span><span class="sxs-lookup"><span data-stu-id="0eeac-115">Requirements</span></span>  

 <span data-ttu-id="0eeac-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0eeac-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eeac-117">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="0eeac-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0eeac-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0eeac-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0eeac-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eeac-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eeac-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0eeac-120">See also</span></span>

- [<span data-ttu-id="0eeac-121">StrongNameHashSize メソッド</span><span class="sxs-lookup"><span data-stu-id="0eeac-121">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="0eeac-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0eeac-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
