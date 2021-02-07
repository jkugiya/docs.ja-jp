---
description: 詳細については、「WCF と国際化ドメイン名」を参照してください。
title: WCF と国際化ドメイン名
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: e7e1ad999d7de749b4f8cf4b3efd823befffba43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755994"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="05687-103">WCF と国際化ドメイン名</span><span class="sxs-lookup"><span data-stu-id="05687-103">WCF and Internationalized Domain Names</span></span>

<span data-ttu-id="05687-104">国際化ドメイン名 (IDN) を持つ WCF サービスを許可するためのサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="05687-104">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="05687-105">国際化ドメイン名とは、非 ASCII 文字を含むドメイン名です。</span><span class="sxs-lookup"><span data-stu-id="05687-105">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="05687-106">このサポートには、IDN 名を持つ WCF サービスをホストする機能と、IDN 名を持つ Web サービスとの通信を行う WCF クライアントをホストする機能の両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="05687-106">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="05687-107">System.Uri と IDN</span><span class="sxs-lookup"><span data-stu-id="05687-107">System.Uri and IDN</span></span>  

 <span data-ttu-id="05687-108"><xref:System.Uri> には、<xref:System.Uri.Host%2A> および <xref:System.Uri.DnsSafeHost%2A> という 2 つのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="05687-108"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="05687-109">これらのプロパティには、IDN 構成設定に応じて Unicode 値または Punycode 値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="05687-109">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="05687-110">IDN をアプリケーションの構成ファイルで有効にするには、次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="05687-110">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="05687-111">要素には、 \<idn> 次のいずれかの値に設定できる enabled 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="05687-111">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1. <span data-ttu-id="05687-112">"None"</span><span class="sxs-lookup"><span data-stu-id="05687-112">"None"</span></span>  
  
2. <span data-ttu-id="05687-113">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="05687-113">"AllExceptIntranet"</span></span>  
  
3. <span data-ttu-id="05687-114">"All"</span><span class="sxs-lookup"><span data-stu-id="05687-114">"All"</span></span>  
  
 <span data-ttu-id="05687-115">IDN 設定が "None" に設定されている場合、Uri. Host または Uri. DnsSafeHost で変換は実行されません。</span><span class="sxs-lookup"><span data-stu-id="05687-115">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="05687-116">IDN 設定が "All" に設定されている場合は uri です。ホストは Unicode と uri のままです。DnsSafeHost は Punycode に変換されます。</span><span class="sxs-lookup"><span data-stu-id="05687-116">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="05687-117">IDN 設定が "AllExceptIntranet" に設定されている場合は uri です。DnsSafeHost は、インターネットアドレスの場合は Punycode に変換され、イントラネットアドレスの場合は Unicode のままです。</span><span class="sxs-lookup"><span data-stu-id="05687-117">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="05687-118">この設定は、正しい DNS 名解決にとって重要です。</span><span class="sxs-lookup"><span data-stu-id="05687-118">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="05687-119">Windows 8 以降のバージョンでは、この設定を構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="05687-119">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="05687-120">Punycode を使用してアドレスをハードコーディングしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="05687-120">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="05687-121">アドレスは、適用した構成設定に基づき、WCF によって自動的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="05687-121">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="05687-122">Unicode 文字を applicationHost.exe.config に追加する場合は、UTF-8 エンコードを使用してファイルを保存してください。</span><span class="sxs-lookup"><span data-stu-id="05687-122">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05687-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="05687-123">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
