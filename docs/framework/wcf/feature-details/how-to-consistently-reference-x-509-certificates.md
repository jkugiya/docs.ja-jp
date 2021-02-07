---
description: '詳細については、「方法: x.509 証明書を一貫して参照する」を参照してください。'
title: '方法: 一貫性を保って X.509 証明書を参照する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: cdf5535373490e8cb78e28a8fc0cf881df40e041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734803"
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="a0e4d-103">方法: 一貫性を保って X.509 証明書を参照する</span><span class="sxs-lookup"><span data-stu-id="a0e4d-103">How to: Consistently Reference X.509 Certificates</span></span>

<span data-ttu-id="a0e4d-104">証明書を識別する方法には、証明書のハッシュを使用する方法、発行者とシリアル番号を使用する方法、またはサブジェクト キー識別子 (SKI) を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-104">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="a0e4d-105">SKI を使用すると、証明書のサブジェクト公開キーを一意に識別できます。SKI は、XML デジタル署名を処理する場合によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-105">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="a0e4d-106">SKI 値は、通常、 *x.509 証明書拡張* として x.509 証明書の一部です。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-106">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="a0e4d-107">Windows Communication Foundation (WCF) には、証明書に SKI 拡張機能がない場合に発行者とシリアル番号を使用する、既定の *参照スタイル* が設定されています。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-107">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="a0e4d-108">証明書に SKI 拡張が含まれる場合、既定の参照スタイルは SKI を使用してその証明書を識別します。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-108">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="a0e4d-109">アプリケーションの開発中に、SKI 拡張を使用しない証明書を使用して、SKI 拡張機能を使用する証明書に切り替えた場合、WCF によって生成されるメッセージで使用される参照スタイルも変更されます。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-109">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="a0e4d-110">SKI 拡張が存在するかどうかに関係なく、一貫性のある参照スタイルが必要な場合は、次のコードに示されているような参照スタイルを構成できます。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-110">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0e4d-111">例</span><span class="sxs-lookup"><span data-stu-id="a0e4d-111">Example</span></span>  

 <span data-ttu-id="a0e4d-112">次の例では、1 つの一貫した参照スタイル (ユーザー名とシリアル番号) を使用するカスタム セキュリティ バインド要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-112">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0e4d-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a0e4d-113">Compiling the Code</span></span>  

 <span data-ttu-id="a0e4d-114">コードのコンパイルには次の名前空間が必要です。</span><span class="sxs-lookup"><span data-stu-id="a0e4d-114">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="a0e4d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0e4d-115">See also</span></span>

- [<span data-ttu-id="a0e4d-116">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="a0e4d-116">Working with Certificates</span></span>](working-with-certificates.md)
