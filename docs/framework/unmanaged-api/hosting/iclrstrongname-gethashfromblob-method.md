---
description: '詳細情報: ICLRStrongName::GetHashFromBlob メソッド'
title: ICLRStrongName::GetHashFromBlob メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: 20d03184f57e77741e656575038e426ee37968f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637067"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="9d90f-103">ICLRStrongName::GetHashFromBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="9d90f-103">ICLRStrongName::GetHashFromBlob Method</span></span>

<span data-ttu-id="9d90f-104">指定したハッシュ アルゴリズムを使用して、指定したメモリ アドレスにあるアセンブリのハッシュが取得されます。</span><span class="sxs-lookup"><span data-stu-id="9d90f-104">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d90f-105">構文</span><span class="sxs-lookup"><span data-stu-id="9d90f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d90f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d90f-106">Parameters</span></span>  

 `pbBlob`  
 <span data-ttu-id="9d90f-107">[in] ハッシュされるメモリ ブロックのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9d90f-107">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="9d90f-108">[in] メモリ ブロックの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="9d90f-108">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9d90f-109">[in、out] ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="9d90f-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9d90f-110">既定のアルゴリズムでは、ゼロを使用します。</span><span class="sxs-lookup"><span data-stu-id="9d90f-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9d90f-111">[out] 返されたハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="9d90f-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9d90f-112">[in] 要求された `pbHash` の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="9d90f-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9d90f-113">[out] 返された `pbHash` のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="9d90f-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d90f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="9d90f-114">Return Value</span></span>  

 <span data-ttu-id="9d90f-115">メソッドが正常に完了した場合は `S_OK`、それ以外の場合は失敗を示す HRESULT 値 (リストについては、[一般的な HRESULT 値](/windows/win32/seccrypto/common-hresult-values)に関するページを参照)。</span><span class="sxs-lookup"><span data-stu-id="9d90f-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d90f-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="9d90f-116">Requirements</span></span>  

 <span data-ttu-id="9d90f-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d90f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d90f-118">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9d90f-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d90f-119">**ライブラリ:** リソースとして MSCorEE.dll に含まれている</span><span class="sxs-lookup"><span data-stu-id="9d90f-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d90f-120">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d90f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d90f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d90f-121">See also</span></span>

- [<span data-ttu-id="9d90f-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d90f-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
