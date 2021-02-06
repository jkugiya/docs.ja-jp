---
description: '詳細について: ICLRStrongName:: GetHashFromBlob メソッド'
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637067"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="22325-103">ICLRStrongName::GetHashFromBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="22325-103">ICLRStrongName::GetHashFromBlob Method</span></span>

<span data-ttu-id="22325-104">指定したハッシュ アルゴリズムを使用して、指定したメモリ アドレスにあるアセンブリのハッシュが取得されます。</span><span class="sxs-lookup"><span data-stu-id="22325-104">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22325-105">構文</span><span class="sxs-lookup"><span data-stu-id="22325-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="22325-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="22325-106">Parameters</span></span>  

 `pbBlob`  
 <span data-ttu-id="22325-107">からハッシュされるメモリブロックのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="22325-107">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="22325-108">からメモリブロックの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="22325-108">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="22325-109">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="22325-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="22325-110">既定のアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="22325-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="22325-111">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="22325-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="22325-112">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="22325-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="22325-113">入出力返されたのサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="22325-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22325-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="22325-114">Return Value</span></span>  

 <span data-ttu-id="22325-115">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="22325-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22325-116">要件</span><span class="sxs-lookup"><span data-stu-id="22325-116">Requirements</span></span>  

 <span data-ttu-id="22325-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22325-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22325-118">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="22325-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="22325-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="22325-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22325-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22325-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22325-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="22325-121">See also</span></span>

- [<span data-ttu-id="22325-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22325-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
