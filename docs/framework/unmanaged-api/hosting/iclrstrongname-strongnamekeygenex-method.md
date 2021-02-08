---
description: '詳細について: ICLRStrongName:: StrongNameKeyGenEx メソッド'
title: ICLRStrongName::StrongNameKeyGenEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: 3ea2bef5cc6a45066d010fc925f8866e8129faaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799554"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="a56ff-103">ICLRStrongName::StrongNameKeyGenEx メソッド</span><span class="sxs-lookup"><span data-stu-id="a56ff-103">ICLRStrongName::StrongNameKeyGenEx Method</span></span>

<span data-ttu-id="a56ff-104">厳密な名前の使用のために、指定されたキーサイズを持つ新しい公開/秘密キーのペアを生成します。</span><span class="sxs-lookup"><span data-stu-id="a56ff-104">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a56ff-105">構文</span><span class="sxs-lookup"><span data-stu-id="a56ff-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a56ff-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a56ff-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="a56ff-107">から要求されたキーコンテナー名。</span><span class="sxs-lookup"><span data-stu-id="a56ff-107">[in] The requested key container name.</span></span> <span data-ttu-id="a56ff-108">`wszKeyContainer` は、空でない文字列であるか、または一時名を生成するために null である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a56ff-108">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a56ff-109">からキーを登録したままにするかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="a56ff-109">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="a56ff-110">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a56ff-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="a56ff-111">0x00000000- `wszKeyContainer` が null の場合に、一時キーコンテナー名を生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a56ff-111">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="a56ff-112">0x00000001 ( `SN_LEAVE_KEY` )-キーを登録したままにすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a56ff-112">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="a56ff-113">から要求されたキーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="a56ff-113">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a56ff-114">入出力返された公開/秘密キーのペア。</span><span class="sxs-lookup"><span data-stu-id="a56ff-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a56ff-115">入出力のサイズ (バイト単位) `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="a56ff-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a56ff-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="a56ff-116">Return Value</span></span>  

 <span data-ttu-id="a56ff-117">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="a56ff-117">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a56ff-118">解説</span><span class="sxs-lookup"><span data-stu-id="a56ff-118">Remarks</span></span>  

 <span data-ttu-id="a56ff-119">.NET Framework バージョン1.0 および1.1 では、 `dwKeySize` 厳密な名前でアセンブリに署名するには1024ビットが必要です。バージョン2.0 では、2048ビットキーのサポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="a56ff-119">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="a56ff-120">キーを取得した後、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) メソッドを呼び出して、割り当てられたメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a56ff-120">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a56ff-121">要件</span><span class="sxs-lookup"><span data-stu-id="a56ff-121">Requirements</span></span>  

 <span data-ttu-id="a56ff-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a56ff-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a56ff-123">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="a56ff-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a56ff-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a56ff-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a56ff-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a56ff-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a56ff-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a56ff-126">See also</span></span>

- [<span data-ttu-id="a56ff-127">StrongNameKeyGen メソッド</span><span class="sxs-lookup"><span data-stu-id="a56ff-127">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="a56ff-128">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a56ff-128">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
