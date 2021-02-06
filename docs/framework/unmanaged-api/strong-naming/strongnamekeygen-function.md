---
description: '詳細情報: StrongNameKeyGen 関数'
title: StrongNameKeyGen 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
ms.openlocfilehash: c5f4cfcfa9030ae856acf5fd59ab34a2b8338670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636262"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="dc06b-103">StrongNameKeyGen 関数</span><span class="sxs-lookup"><span data-stu-id="dc06b-103">StrongNameKeyGen Function</span></span>

<span data-ttu-id="dc06b-104">厳密な名前を使用するために新しい公開/秘密キーの組が作成されます。</span><span class="sxs-lookup"><span data-stu-id="dc06b-104">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="dc06b-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="dc06b-105">This function has been deprecated.</span></span> <span data-ttu-id="dc06b-106">代わりに [ICLRStrongName:: StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="dc06b-106">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc06b-107">構文</span><span class="sxs-lookup"><span data-stu-id="dc06b-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc06b-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc06b-108">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="dc06b-109">から要求されたキーコンテナー名。</span><span class="sxs-lookup"><span data-stu-id="dc06b-109">[in] The requested key container name.</span></span> <span data-ttu-id="dc06b-110">`wszKeyContainer` は空でない文字列である必要があります。または、一時名を生成する場合は null にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc06b-110">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="dc06b-111">からキーを登録したままにするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc06b-111">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="dc06b-112">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dc06b-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="dc06b-113">0x00000000- `wszKeyContainer` が null の場合に、一時キーコンテナー名を生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="dc06b-113">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="dc06b-114">0x00000001 ( `SN_LEAVE_KEY` )-キーを登録したままにすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="dc06b-114">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="dc06b-115">入出力返された公開/秘密キーのペア。</span><span class="sxs-lookup"><span data-stu-id="dc06b-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="dc06b-116">入出力のサイズ (バイト単位) `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="dc06b-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc06b-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="dc06b-117">Return Value</span></span>  

 <span data-ttu-id="dc06b-118">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="dc06b-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc06b-119">解説</span><span class="sxs-lookup"><span data-stu-id="dc06b-119">Remarks</span></span>  

 <span data-ttu-id="dc06b-120">関数は、 `StrongNameKeyGen` 1024 ビットのキーを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc06b-120">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="dc06b-121">キーが取得されたら、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を呼び出して、割り当てられたメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc06b-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="dc06b-122">関数が `StrongNameKeyGen` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="dc06b-122">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc06b-123">要件</span><span class="sxs-lookup"><span data-stu-id="dc06b-123">Requirements</span></span>  

 <span data-ttu-id="dc06b-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc06b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc06b-125">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="dc06b-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="dc06b-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="dc06b-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc06b-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc06b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc06b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc06b-128">See also</span></span>

- [<span data-ttu-id="dc06b-129">StrongNameKeyGen メソッド</span><span class="sxs-lookup"><span data-stu-id="dc06b-129">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="dc06b-130">StrongNameKeyGenEx メソッド</span><span class="sxs-lookup"><span data-stu-id="dc06b-130">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="dc06b-131">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc06b-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
