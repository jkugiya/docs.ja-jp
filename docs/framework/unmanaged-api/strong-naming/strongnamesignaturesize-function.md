---
description: '詳細情報: StrongNameSignatureSize 関数'
title: StrongNameSignatureSize 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: b3f22a6a4d5455af4dd17cb75edfd18befed7de3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670516"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="0581b-103">StrongNameSignatureSize 関数</span><span class="sxs-lookup"><span data-stu-id="0581b-103">StrongNameSignatureSize Function</span></span>

<span data-ttu-id="0581b-104">厳密な名前の署名のサイズが返されます。</span><span class="sxs-lookup"><span data-stu-id="0581b-104">Returns the size of the strong name signature.</span></span> <span data-ttu-id="0581b-105">`StrongNameSignatureSize` は、通常、コンパイラによって使用され、遅延署名されたアセンブリを作成するときにファイルで予約する領域の量を決定します。</span><span class="sxs-lookup"><span data-stu-id="0581b-105">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="0581b-106">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="0581b-106">This function has been deprecated.</span></span> <span data-ttu-id="0581b-107">代わりに [ICLRStrongName:: StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="0581b-107">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0581b-108">構文</span><span class="sxs-lookup"><span data-stu-id="0581b-108">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="0581b-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0581b-109">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="0581b-110">から厳密な名前の署名を生成するために使用されるキーペアの公開部分を格納する [Publickeyblob](publickeyblob-structure.md) 型の構造体。</span><span class="sxs-lookup"><span data-stu-id="0581b-110">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="0581b-111">からのサイズ (バイト単位) `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="0581b-111">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="0581b-112">から厳密な名前の署名を格納するために必要なバイト数。</span><span class="sxs-lookup"><span data-stu-id="0581b-112">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0581b-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="0581b-113">Return Value</span></span>  

 <span data-ttu-id="0581b-114">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="0581b-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0581b-115">解説</span><span class="sxs-lookup"><span data-stu-id="0581b-115">Remarks</span></span>  

 <span data-ttu-id="0581b-116">関数が `StrongNameSignatureSize` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="0581b-116">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0581b-117">要件</span><span class="sxs-lookup"><span data-stu-id="0581b-117">Requirements</span></span>  

 <span data-ttu-id="0581b-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0581b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0581b-119">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="0581b-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0581b-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0581b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0581b-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0581b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0581b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="0581b-122">See also</span></span>

- [<span data-ttu-id="0581b-123">StrongNameSignatureSize メソッド</span><span class="sxs-lookup"><span data-stu-id="0581b-123">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="0581b-124">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0581b-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
