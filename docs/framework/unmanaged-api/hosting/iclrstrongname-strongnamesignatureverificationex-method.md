---
description: '詳細について: ICLRStrongName:: StrongNameSignatureVerificationEx メソッド'
title: ICLRStrongName::StrongNameSignatureVerificationEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
ms.openlocfilehash: 0e1692d7151e09a621b93823424b3ac10b6607d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789763"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="60a83-103">ICLRStrongName::StrongNameSignatureVerificationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="60a83-103">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>

<span data-ttu-id="60a83-104">指定したパスにあるアセンブリマニフェストに厳密な名前の署名が含まれているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="60a83-104">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60a83-105">構文</span><span class="sxs-lookup"><span data-stu-id="60a83-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60a83-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60a83-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="60a83-107">から検証するアセンブリの移植可能な実行可能ファイル (.exe または .dll) のパス。</span><span class="sxs-lookup"><span data-stu-id="60a83-107">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="60a83-108">[入力] `true` レジストリ設定を上書きする必要がある場合でも、検証を実行するにはそれ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="60a83-108">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="60a83-109">[出力] `true` 厳密な名前の署名が検証された場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="60a83-109">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="60a83-110">`pfWasVerified``false`レジストリ設定によって検証が成功した場合は、もに設定されます。</span><span class="sxs-lookup"><span data-stu-id="60a83-110">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60a83-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="60a83-111">Return Value</span></span>  

 <span data-ttu-id="60a83-112">`S_OK` 検証が成功した場合は、それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="60a83-112">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60a83-113">解説</span><span class="sxs-lookup"><span data-stu-id="60a83-113">Remarks</span></span>  

 <span data-ttu-id="60a83-114">[ICLRStrongName:: StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md)メソッドには、 [ICLRStrongName:: StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md)メソッドと同様の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="60a83-114">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="60a83-115">ただし、 [ICLRStrongName:: StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) の2番目の入力パラメーターと出力パラメーターは、 `BOOLEAN` の代わりに型に `DWORD` なります。</span><span class="sxs-lookup"><span data-stu-id="60a83-115">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60a83-116">要件</span><span class="sxs-lookup"><span data-stu-id="60a83-116">Requirements</span></span>  

 <span data-ttu-id="60a83-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60a83-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60a83-118">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="60a83-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="60a83-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="60a83-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60a83-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60a83-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a83-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="60a83-121">See also</span></span>

- [<span data-ttu-id="60a83-122">StrongNameSignatureVerification メソッド</span><span class="sxs-lookup"><span data-stu-id="60a83-122">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="60a83-123">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60a83-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
