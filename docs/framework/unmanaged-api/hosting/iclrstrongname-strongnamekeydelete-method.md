---
description: '詳細について: ICLRStrongName:: StrongNameKeyDelete メソッド'
title: ICLRStrongName::StrongNameKeyDelete メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
ms.openlocfilehash: 5b782785921eb24394db53d29a66600a3867b489
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799578"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="a0601-103">ICLRStrongName::StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="a0601-103">ICLRStrongName::StrongNameKeyDelete Method</span></span>

<span data-ttu-id="a0601-104">指定したキー コンテナーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="a0601-104">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0601-105">構文</span><span class="sxs-lookup"><span data-stu-id="a0601-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0601-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0601-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="a0601-107">から削除するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="a0601-107">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0601-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0601-108">Return Value</span></span>  

 <span data-ttu-id="a0601-109">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="a0601-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0601-110">解説</span><span class="sxs-lookup"><span data-stu-id="a0601-110">Remarks</span></span>  

 <span data-ttu-id="a0601-111">[ICLRStrongName:: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md)メソッドを使用して、公開キーと秘密キーのペアをコンテナーにインポートします。</span><span class="sxs-lookup"><span data-stu-id="a0601-111">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0601-112">要件</span><span class="sxs-lookup"><span data-stu-id="a0601-112">Requirements</span></span>  

 <span data-ttu-id="a0601-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0601-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0601-114">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="a0601-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a0601-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a0601-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0601-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0601-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0601-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0601-117">See also</span></span>

- [<span data-ttu-id="a0601-118">StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="a0601-118">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="a0601-119">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0601-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
