---
description: '詳細については、「方法: 証明書を取得する (WCF)」を参照してください。'
title: '方法 : 証明書 (WCF) を取得する'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 2ca40c9646bbdeb6c29a94966fd24ec00d9b5306
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793702"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="ea1ad-103">方法 : 証明書 (WCF) を取得する</span><span class="sxs-lookup"><span data-stu-id="ea1ad-103">How to: Obtain a Certificate (WCF)</span></span>

<span data-ttu-id="ea1ad-104">X.509 証明書を使用するの Windows Communication Foundation (WCF) 機能のいずれかを使用するには、最初に証明書を取得するだけです。</span><span class="sxs-lookup"><span data-stu-id="ea1ad-104">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="ea1ad-105">X.509 証明書を取得するには</span><span class="sxs-lookup"><span data-stu-id="ea1ad-105">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="ea1ad-106">次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="ea1ad-106">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="ea1ad-107">VeriSign, Inc. などの証明機関から証明書を購入します。</span><span class="sxs-lookup"><span data-stu-id="ea1ad-107">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="ea1ad-108">独自の証明書サービスを設定し、証明機関に証明書への署名を依頼します。</span><span class="sxs-lookup"><span data-stu-id="ea1ad-108">Set up your own certificate service and have a certification authority sign the certificates.</span></span> <span data-ttu-id="ea1ad-109">Windows Server 2003、Windows 2000 Server、Windows 2000 Server Datacenter、および Windows 2000 Datacenter Server にはすべて、公開キー基盤 (PKI) をサポートする証明書サービスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ea1ad-109">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="ea1ad-110">Windows Server 2008 では、 [Active Directory 証明書サービス](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) の役割を使用して、証明機関を管理します。</span><span class="sxs-lookup"><span data-stu-id="ea1ad-110">In Windows Server 2008, use the [Active Directory Certificate Services](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="ea1ad-111">独自の証明書サービスを設定し、証明書には署名しません。</span><span class="sxs-lookup"><span data-stu-id="ea1ad-111">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ea1ad-112">どの方法を使用する場合でも、X.509 証明書を含む SOAP 要求の受信者は、その X.509 証明書を信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea1ad-112">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="ea1ad-113">つまり、証明書チェーン内の X.509 証明書または発行者は、信頼されたユーザーの証明書ストア内に存在し、また X.509 証明書は信頼されない証明書ストア内には存在しないということを意味します。</span><span class="sxs-lookup"><span data-stu-id="ea1ad-113">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1ad-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea1ad-114">See also</span></span>

- [<span data-ttu-id="ea1ad-115">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="ea1ad-115">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="ea1ad-116">方法: 開発中に使用する一時的な証明書を作成する</span><span class="sxs-lookup"><span data-stu-id="ea1ad-116">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
