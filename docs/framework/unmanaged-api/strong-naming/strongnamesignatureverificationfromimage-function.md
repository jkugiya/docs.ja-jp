---
description: '詳細情報: StrongNameSignatureVerificationFromImage 関数'
title: StrongNameSignatureVerificationFromImage 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
ms.openlocfilehash: 9dca8d0b221dfe8959be2de9b8347b95d3802a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794495"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="37186-103">StrongNameSignatureVerificationFromImage 関数</span><span class="sxs-lookup"><span data-stu-id="37186-103">StrongNameSignatureVerificationFromImage Function</span></span>

<span data-ttu-id="37186-104">メモリに既にマップされているアセンブリが、関連付けられている公開キーに対して有効であるかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="37186-104">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="37186-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="37186-105">This function has been deprecated.</span></span> <span data-ttu-id="37186-106">代わりに [ICLRStrongName:: StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="37186-106">Use the [ICLRStrongName::StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37186-107">構文</span><span class="sxs-lookup"><span data-stu-id="37186-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37186-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37186-108">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="37186-109">からマップされたアセンブリマニフェストの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="37186-109">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="37186-110">からマップされたイメージのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="37186-110">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="37186-111">から検証の動作に影響を与えるフラグ。</span><span class="sxs-lookup"><span data-stu-id="37186-111">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="37186-112">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="37186-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="37186-113">`SN_INFLAG_FORCE_VER` (0x00000001)-レジストリ設定を上書きする必要がある場合でも、検証を強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="37186-113">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="37186-114">`SN_INFLAG_INSTALL` (0x00000002)-これがこのイメージに対して実行される最初の検証であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="37186-114">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="37186-115">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-キャッシュが管理者特権を持つユーザーのみにアクセスを許可することを指定します。</span><span class="sxs-lookup"><span data-stu-id="37186-115">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="37186-116">`SN_INFLAG_USER_ACCESS` (0x00000008)-現在のユーザーのみがアセンブリにアクセスできるように指定します。</span><span class="sxs-lookup"><span data-stu-id="37186-116">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="37186-117">`SN_INFLAG_ALL_ACCESS` (0x00000010)-キャッシュがアクセス制限の保証を提供しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="37186-117">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="37186-118">`SN_INFLAG_RUNTIME` (0x80000000)-内部デバッグ用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="37186-118">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="37186-119">入出力追加の出力情報のフラグ。</span><span class="sxs-lookup"><span data-stu-id="37186-119">[out] A flag for additional output information.</span></span> <span data-ttu-id="37186-120">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="37186-120">The following value is supported:</span></span>  
  
- <span data-ttu-id="37186-121">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-この値は `false` 、レジストリ設定によって検証が成功したことを指定するためにに設定されます。</span><span class="sxs-lookup"><span data-stu-id="37186-121">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37186-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="37186-122">Return Value</span></span>  

 <span data-ttu-id="37186-123">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="37186-123">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37186-124">解説</span><span class="sxs-lookup"><span data-stu-id="37186-124">Remarks</span></span>  

 <span data-ttu-id="37186-125">関数が `StrongNameSignatureVerificationFromImage` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="37186-125">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37186-126">要件</span><span class="sxs-lookup"><span data-stu-id="37186-126">Requirements</span></span>  

 <span data-ttu-id="37186-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37186-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37186-128">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="37186-128">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="37186-129">**ライブラリ:** mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="37186-129">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="37186-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37186-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37186-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="37186-131">See also</span></span>

- [<span data-ttu-id="37186-132">StrongNameSignatureVerificationFromImage メソッド</span><span class="sxs-lookup"><span data-stu-id="37186-132">StrongNameSignatureVerificationFromImage Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="37186-133">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37186-133">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
