---
description: '詳細について: ICLRStrongName:: StrongNameSignatureVerificationFromImage メソッド'
title: ICLRStrongName::StrongNameSignatureVerificationFromImage メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: 5c1c3568dd0ad506c478525503f168d8b8c2dfbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781832"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="28af2-103">ICLRStrongName::StrongNameSignatureVerificationFromImage メソッド</span><span class="sxs-lookup"><span data-stu-id="28af2-103">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>

<span data-ttu-id="28af2-104">メモリに既にマップされているアセンブリが、関連付けられている公開キーに対して有効であるかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="28af2-104">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28af2-105">構文</span><span class="sxs-lookup"><span data-stu-id="28af2-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28af2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28af2-106">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="28af2-107">からマップされたアセンブリマニフェストの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="28af2-107">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="28af2-108">からマップされたイメージのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="28af2-108">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="28af2-109">から検証の動作に影響を与えるフラグ。</span><span class="sxs-lookup"><span data-stu-id="28af2-109">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="28af2-110">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="28af2-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="28af2-111">`SN_INFLAG_FORCE_VER` (0x00000001)-レジストリ設定を上書きする必要がある場合でも、検証を強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="28af2-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="28af2-112">`SN_INFLAG_INSTALL` (0x00000002)-これがこのイメージに対して実行される最初の検証であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="28af2-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="28af2-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-キャッシュが管理者特権を持つユーザーのみにアクセスを許可することを指定します。</span><span class="sxs-lookup"><span data-stu-id="28af2-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="28af2-114">`SN_INFLAG_USER_ACCESS` (0x00000008)-現在のユーザーのみがアセンブリにアクセスできるように指定します。</span><span class="sxs-lookup"><span data-stu-id="28af2-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="28af2-115">`SN_INFLAG_ALL_ACCESS` (0x00000010)-キャッシュがアクセス制限の保証を提供しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="28af2-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="28af2-116">`SN_INFLAG_RUNTIME` (0x80000000)-内部デバッグ用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="28af2-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="28af2-117">入出力追加の出力情報のフラグ。</span><span class="sxs-lookup"><span data-stu-id="28af2-117">[out] A flag for additional output information.</span></span> <span data-ttu-id="28af2-118">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="28af2-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="28af2-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-この値は `false` 、レジストリ設定によって検証が成功したことを指定するためにに設定されます。</span><span class="sxs-lookup"><span data-stu-id="28af2-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28af2-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="28af2-120">Return Value</span></span>  

 <span data-ttu-id="28af2-121">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="28af2-121">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28af2-122">要件</span><span class="sxs-lookup"><span data-stu-id="28af2-122">Requirements</span></span>  

 <span data-ttu-id="28af2-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28af2-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28af2-124">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="28af2-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="28af2-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="28af2-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28af2-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28af2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28af2-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="28af2-127">See also</span></span>

- [<span data-ttu-id="28af2-128">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28af2-128">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
