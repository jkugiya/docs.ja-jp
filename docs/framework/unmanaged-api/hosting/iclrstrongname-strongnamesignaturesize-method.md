---
description: '詳細について: ICLRStrongName:: StrongNameSignatureSize メソッド'
title: ICLRStrongName::StrongNameSignatureSize メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
ms.openlocfilehash: 4c3804eea5b7c6325519b19546f25585af649866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781858"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="92af1-103">ICLRStrongName::StrongNameSignatureSize メソッド</span><span class="sxs-lookup"><span data-stu-id="92af1-103">ICLRStrongName::StrongNameSignatureSize Method</span></span>

<span data-ttu-id="92af1-104">厳密な名前の署名のサイズが返されます。</span><span class="sxs-lookup"><span data-stu-id="92af1-104">Returns the size of the strong name signature.</span></span> <span data-ttu-id="92af1-105">このメソッドは、通常、遅延署名されたアセンブリを作成するときに、ファイル内で予約する領域の量を決定するためにコンパイラによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="92af1-105">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92af1-106">構文</span><span class="sxs-lookup"><span data-stu-id="92af1-106">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="92af1-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92af1-107">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="92af1-108">から厳密な名前の署名を生成するために使用されるキーペアの公開部分を格納する [Publickeyblob](../strong-naming/publickeyblob-structure.md) 型の構造体。</span><span class="sxs-lookup"><span data-stu-id="92af1-108">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="92af1-109">からのサイズ (バイト単位) `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="92af1-109">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="92af1-110">から厳密な名前の署名を格納するために必要なバイト数。</span><span class="sxs-lookup"><span data-stu-id="92af1-110">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92af1-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="92af1-111">Return Value</span></span>  

 <span data-ttu-id="92af1-112">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="92af1-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92af1-113">要件</span><span class="sxs-lookup"><span data-stu-id="92af1-113">Requirements</span></span>  

 <span data-ttu-id="92af1-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92af1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92af1-115">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="92af1-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="92af1-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="92af1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92af1-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92af1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92af1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="92af1-118">See also</span></span>

- [<span data-ttu-id="92af1-119">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92af1-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
