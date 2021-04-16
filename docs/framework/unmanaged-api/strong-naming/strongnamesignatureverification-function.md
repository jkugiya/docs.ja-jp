---
description: '詳細情報: StrongNameSignatureVerification 関数'
title: StrongNameSignatureVerification 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
ms.openlocfilehash: 74130cda96f38218d2fd296ff8804f86a9a18cd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636259"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="c37f0-103">StrongNameSignatureVerification 関数</span><span class="sxs-lookup"><span data-stu-id="c37f0-103">StrongNameSignatureVerification Function</span></span>

<span data-ttu-id="c37f0-104">指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。これは指定したフラグに従って確認されます。</span><span class="sxs-lookup"><span data-stu-id="c37f0-104">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="c37f0-105">この関数は非推奨とされています。</span><span class="sxs-lookup"><span data-stu-id="c37f0-105">This function has been deprecated.</span></span> <span data-ttu-id="c37f0-106">代わりに、[ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="c37f0-106">Use the [ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c37f0-107">構文</span><span class="sxs-lookup"><span data-stu-id="c37f0-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c37f0-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c37f0-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="c37f0-109">[in] 検証するアセンブリの移植可能な実行可能ファイル (.dll または .exe) のパス。</span><span class="sxs-lookup"><span data-stu-id="c37f0-109">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="c37f0-110">[in] 検証動作を変更するフラグ。</span><span class="sxs-lookup"><span data-stu-id="c37f0-110">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="c37f0-111">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c37f0-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="c37f0-112">`SN_INFLAG_FORCE_VER` (0x00000001) - レジストリ設定を上書きする必要がある場合でも、検証を実行します。</span><span class="sxs-lookup"><span data-stu-id="c37f0-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="c37f0-113">`SN_INFLAG_INSTALL` (0x00000002) - マニフェストを初めて検証するときに指定します。</span><span class="sxs-lookup"><span data-stu-id="c37f0-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="c37f0-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - キャッシュで、管理者特権を持つユーザーのみにアクセスを許可することを指定します。</span><span class="sxs-lookup"><span data-stu-id="c37f0-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="c37f0-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - 現在のユーザーのみがアセンブリにアクセスできるように指定します。</span><span class="sxs-lookup"><span data-stu-id="c37f0-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="c37f0-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - キャッシュでアクセス制限の保証を提供しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c37f0-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="c37f0-117">`SN_INFLAG_RUNTIME` (0x80000000) - 内部デバッグ用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="c37f0-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="c37f0-118">[out] 厳密な名前のシグネチャが検証されたかどうかを示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="c37f0-118">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="c37f0-119">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c37f0-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="c37f0-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - この値は、レジストリ設定によって検証が成功したことを指定するために、`false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c37f0-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c37f0-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="c37f0-121">Return Value</span></span>  

 <span data-ttu-id="c37f0-122">検証が正常に実行された場合は `true`。それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="c37f0-122">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c37f0-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="c37f0-123">Requirements</span></span>  

 <span data-ttu-id="c37f0-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c37f0-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c37f0-125">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c37f0-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c37f0-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="c37f0-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c37f0-127">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c37f0-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37f0-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="c37f0-128">See also</span></span>

- [<span data-ttu-id="c37f0-129">StrongNameSignatureVerification メソッド</span><span class="sxs-lookup"><span data-stu-id="c37f0-129">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="c37f0-130">StrongNameSignatureVerificationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="c37f0-130">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="c37f0-131">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c37f0-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
