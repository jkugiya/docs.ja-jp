---
description: '詳細について: ICLRStrongName:: StrongNameFreeBuffer メソッド'
title: ICLRStrongName::StrongNameFreeBuffer メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 8b65b75b92dd259c6919cfac9bc097066f552aba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799650"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="37391-103">ICLRStrongName::StrongNameFreeBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="37391-103">ICLRStrongName::StrongNameFreeBuffer Method</span></span>

<span data-ttu-id="37391-104">[ICLRStrongName:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md)、 [ICLRStrongName:: StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md)、 [ICLRStrongName:: StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)などの厳密な名前のメソッドへの前回の呼び出しで割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="37391-104">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37391-105">構文</span><span class="sxs-lookup"><span data-stu-id="37391-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37391-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37391-106">Parameters</span></span>  

 `pbMemory`  
 <span data-ttu-id="37391-107">から解放するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="37391-107">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37391-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="37391-108">Return Value</span></span>  

 <span data-ttu-id="37391-109">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="37391-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37391-110">要件</span><span class="sxs-lookup"><span data-stu-id="37391-110">Requirements</span></span>  

 <span data-ttu-id="37391-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37391-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37391-112">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="37391-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="37391-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="37391-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37391-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37391-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37391-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="37391-115">See also</span></span>

- [<span data-ttu-id="37391-116">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37391-116">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
