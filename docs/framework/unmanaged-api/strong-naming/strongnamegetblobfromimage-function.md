---
description: '詳細情報: StrongNameGetBlobFromImage 関数'
title: StrongNameGetBlobFromImage 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
ms.openlocfilehash: c68d6914d47fbb711c49c1e8432cae1bf33e771f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636352"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="bb76e-103">StrongNameGetBlobFromImage 関数</span><span class="sxs-lookup"><span data-stu-id="bb76e-103">StrongNameGetBlobFromImage Function</span></span>

<span data-ttu-id="bb76e-104">指定したメモリ アドレスにあるアセンブリ イメージのバイナリ表現が取得されます。</span><span class="sxs-lookup"><span data-stu-id="bb76e-104">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="bb76e-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="bb76e-105">This function has been deprecated.</span></span> <span data-ttu-id="bb76e-106">代わりに [ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="bb76e-106">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb76e-107">構文</span><span class="sxs-lookup"><span data-stu-id="bb76e-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb76e-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb76e-108">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="bb76e-109">からマップされたアセンブリマニフェストのメモリアドレス。</span><span class="sxs-lookup"><span data-stu-id="bb76e-109">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="bb76e-110">からにあるイメージのサイズ (バイト単位) `pbBase` 。</span><span class="sxs-lookup"><span data-stu-id="bb76e-110">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="bb76e-111">からイメージのバイナリ表現を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="bb76e-111">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="bb76e-112">[入力、出力]要求された最大サイズ (バイト単位) `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="bb76e-112">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="bb76e-113">戻り時に、の実際のサイズ (バイト単位) `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="bb76e-113">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb76e-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="bb76e-114">Return Value</span></span>  

 <span data-ttu-id="bb76e-115">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="bb76e-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb76e-116">解説</span><span class="sxs-lookup"><span data-stu-id="bb76e-116">Remarks</span></span>  

 <span data-ttu-id="bb76e-117">関数が `StrongNameGetBlobFromImage` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="bb76e-117">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb76e-118">要件</span><span class="sxs-lookup"><span data-stu-id="bb76e-118">Requirements</span></span>  

 <span data-ttu-id="bb76e-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb76e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb76e-120">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="bb76e-120">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bb76e-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bb76e-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb76e-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb76e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb76e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb76e-123">See also</span></span>

- [<span data-ttu-id="bb76e-124">StrongNameGetBlobFromImage メソッド</span><span class="sxs-lookup"><span data-stu-id="bb76e-124">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="bb76e-125">StrongNameGetBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="bb76e-125">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="bb76e-126">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb76e-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
