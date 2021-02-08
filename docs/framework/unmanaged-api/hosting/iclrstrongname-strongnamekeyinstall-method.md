---
description: '詳細について: ICLRStrongName:: StrongNameKeyInstall メソッド'
title: ICLRStrongName::StrongNameKeyInstall メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: 8f9e7bfebff555a6430a3970c8ee1c481e341f58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799513"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="f6fdd-103">ICLRStrongName::StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="f6fdd-103">ICLRStrongName::StrongNameKeyInstall Method</span></span>

<span data-ttu-id="f6fdd-104">公開/秘密キーの組がコンテナーにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="f6fdd-104">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6fdd-105">構文</span><span class="sxs-lookup"><span data-stu-id="f6fdd-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6fdd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f6fdd-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="f6fdd-107">からキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="f6fdd-107">[in] The name of the key container.</span></span> <span data-ttu-id="f6fdd-108">`wszKeyContainer` は空でない文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6fdd-108">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f6fdd-109">からバイナリキーペア。</span><span class="sxs-lookup"><span data-stu-id="f6fdd-109">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f6fdd-110">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="f6fdd-110">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6fdd-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="f6fdd-111">Return Value</span></span>  

 <span data-ttu-id="f6fdd-112">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f6fdd-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6fdd-113">解説</span><span class="sxs-lookup"><span data-stu-id="f6fdd-113">Remarks</span></span>  

 <span data-ttu-id="f6fdd-114">[ICLRStrongName:: StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md)メソッドを使用して、キーコンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="f6fdd-114">Use the [ICLRStrongName::StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6fdd-115">要件</span><span class="sxs-lookup"><span data-stu-id="f6fdd-115">Requirements</span></span>  

 <span data-ttu-id="f6fdd-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6fdd-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6fdd-117">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="f6fdd-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f6fdd-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f6fdd-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6fdd-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6fdd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fdd-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6fdd-120">See also</span></span>

- [<span data-ttu-id="f6fdd-121">StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="f6fdd-121">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="f6fdd-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6fdd-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
