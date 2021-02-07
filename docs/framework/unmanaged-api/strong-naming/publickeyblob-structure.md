---
description: 詳細については、「PublicKeyBlob 構造」を参照してください。
title: PublicKeyBlob 構造体
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
ms.openlocfilehash: 94c1ea3d5a41bbb8941658e87f97cd6d6336187a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736481"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="09064-103">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="09064-103">PublicKeyBlob Structure</span></span>

<span data-ttu-id="09064-104">公開キーと秘密キーのペアの公開キーをバイナリ形式で表します。</span><span class="sxs-lookup"><span data-stu-id="09064-104">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09064-105">構文</span><span class="sxs-lookup"><span data-stu-id="09064-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="09064-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="09064-106">Members</span></span>  
  
|<span data-ttu-id="09064-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="09064-107">Member</span></span>|<span data-ttu-id="09064-108">説明</span><span class="sxs-lookup"><span data-stu-id="09064-108">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="09064-109">`ALG_ID`公開キーの署名アルゴリズム (WinCrypt .h で定義されている型の) の識別子。</span><span class="sxs-lookup"><span data-stu-id="09064-109">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="09064-110">`ALG_ID`公開キーのハッシュアルゴリズム (WinCrypt .h で定義されている型の) の識別子。</span><span class="sxs-lookup"><span data-stu-id="09064-110">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="09064-111">キーの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="09064-111">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="09064-112">CryptoAPI によって返される形式のキー値を格納する可変長バイト配列。</span><span class="sxs-lookup"><span data-stu-id="09064-112">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09064-113">解説</span><span class="sxs-lookup"><span data-stu-id="09064-113">Remarks</span></span>  

 <span data-ttu-id="09064-114">`PublicKeyBlob`構造体は、公開キーと秘密キーのペアの公開キーを表すために、 [StrongNameGetPublicKey](strongnamegetpublickey-function.md)、 [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)、およびその他の厳密な名前関数によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="09064-114">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09064-115">要件</span><span class="sxs-lookup"><span data-stu-id="09064-115">Requirements</span></span>  

 <span data-ttu-id="09064-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09064-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09064-117">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="09064-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="09064-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="09064-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09064-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09064-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09064-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="09064-120">See also</span></span>

- [<span data-ttu-id="09064-121">StrongNameGetPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="09064-121">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="09064-122">StrongNameSignatureGeneration 関数</span><span class="sxs-lookup"><span data-stu-id="09064-122">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
