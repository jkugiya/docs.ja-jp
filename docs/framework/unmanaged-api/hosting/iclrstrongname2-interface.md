---
description: 詳細については、「ICLRStrongName2 インターフェイス」を参照してください。
title: ICLRStrongName2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: 7442bd054af735e9f1b75b05feb8724dfa993f73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781793"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="caf69-103">ICLRStrongName2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caf69-103">ICLRStrongName2 Interface</span></span>

<span data-ttu-id="caf69-104">セキュリティで保護されたハッシュアルゴリズム (SHA-256、SHA-384、および SHA-512) の SHA-1 グループを使用して、厳密な名前を作成する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="caf69-104">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="caf69-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="caf69-105">Methods</span></span>  
  
|<span data-ttu-id="caf69-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="caf69-106">Method</span></span>|<span data-ttu-id="caf69-107">説明</span><span class="sxs-lookup"><span data-stu-id="caf69-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="caf69-108">StrongNameGetPublicKeyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="caf69-108">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="caf69-109">公開キーと秘密キーのペアから公開キーを取得し、ハッシュアルゴリズムと署名アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="caf69-109">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="caf69-110">StrongNameSignatureVerificationEx2 メソッド</span><span class="sxs-lookup"><span data-stu-id="caf69-110">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="caf69-111">厳密に名前が付けられたアセンブリの署名を検証し、ECMA キーから実際のキーへのマッピングを提供します。</span><span class="sxs-lookup"><span data-stu-id="caf69-111">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caf69-112">解説</span><span class="sxs-lookup"><span data-stu-id="caf69-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caf69-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="caf69-113">Requirements</span></span>  

 <span data-ttu-id="caf69-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caf69-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caf69-115">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="caf69-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="caf69-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="caf69-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="caf69-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caf69-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
