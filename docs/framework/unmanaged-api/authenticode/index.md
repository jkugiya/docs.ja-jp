---
description: '詳細情報: Authenticode (アンマネージ API リファレンス)'
title: Authenticode (アンマネージ API リファレンス)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: d7a1684fde900bfc01161193d0747b156c6856a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772836"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="d517a-103">Authenticode (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d517a-103">Authenticode (Unmanaged API Reference)</span></span>

<span data-ttu-id="d517a-104">Authenticode XrML ライセンスの作成および検証モジュールをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d517a-104">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d517a-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d517a-105">In This Section</span></span>  

 [<span data-ttu-id="d517a-106">_AxlGetIssuerPublicKeyHash 関数</span><span class="sxs-lookup"><span data-stu-id="d517a-106">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="d517a-107">指定された証明書の署名に使用する秘密キーに関連付けられている公開キーの SHA-1 ハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="d517a-107">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="d517a-108">_AxlPublicKeyBlobToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="d517a-108">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="d517a-109">CSP PUBLICKEYBLOB 形式から厳密な名前の公開キー トークンを算出します。</span><span class="sxs-lookup"><span data-stu-id="d517a-109">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="d517a-110">_AxlRSAKeyValueToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="d517a-110">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="d517a-111">Modulus および Exponent を、厳密な名前の公開キー トークンに変換します。</span><span class="sxs-lookup"><span data-stu-id="d517a-111">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="d517a-112">CertFreeAuthenticodeSignerInfo 関数</span><span class="sxs-lookup"><span data-stu-id="d517a-112">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="d517a-113">AXL_AUTHENTICODE_SIGNER_INFO 構造に割り当てられているリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="d517a-113">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="d517a-114">CertFreeAuthenticodeTimestamperInfo 関数</span><span class="sxs-lookup"><span data-stu-id="d517a-114">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="d517a-115">AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造に割り当てられているリソースを開放します。</span><span class="sxs-lookup"><span data-stu-id="d517a-115">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="d517a-116">CertTimestampAuthenticodeLicense 関数</span><span class="sxs-lookup"><span data-stu-id="d517a-116">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="d517a-117">CertCreateAuthenticodeLicense で作成された Authenticode XrML ライセンスにタイム スタンプを付けます。</span><span class="sxs-lookup"><span data-stu-id="d517a-117">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="d517a-118">CertVerifyAuthenticodeLicense 関数</span><span class="sxs-lookup"><span data-stu-id="d517a-118">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="d517a-119">Authenticode XrML ライセンスの有効性を検証します。</span><span class="sxs-lookup"><span data-stu-id="d517a-119">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="d517a-120">AXL_AUTHENTICODE_SIGNER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="d517a-120">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="d517a-121">Authenticode の署名者情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="d517a-121">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="d517a-122">AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="d517a-122">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="d517a-123">Authenticode のタイム スタンパー情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="d517a-123">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d517a-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d517a-124">See also</span></span>

- [<span data-ttu-id="d517a-125">アンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="d517a-125">Unmanaged API Reference</span></span>](../index.md)
