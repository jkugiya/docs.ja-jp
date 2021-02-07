---
description: 詳細については、「Windows Identity Foundation の構成スキーマ」を参照してください。
title: Windows Identity Foundation 構成スキーマ
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 926b2dbe25359ebc789c95f75a59090c7e5a52e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725338"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="74b6b-103">Windows Identity Foundation 構成スキーマ</span><span class="sxs-lookup"><span data-stu-id="74b6b-103">Windows Identity Foundation Configuration Schema</span></span>

<span data-ttu-id="74b6b-104">このセクションのトピックでは、Windows Identity Foundation (WIF) の構成スキーマに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="74b6b-104">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="74b6b-105">また、フレームワークによって公開されているクラスを介して WIF を使用するようにアプリケーションを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="74b6b-105">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="74b6b-106">これらのクラスは、スキーマ内の関連要素を処理するセクションに記載されています。</span><span class="sxs-lookup"><span data-stu-id="74b6b-106">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="74b6b-107">次に示すのは、WIF 構成スキーマによって公開された基本的な XML タグ構造です。</span><span class="sxs-lookup"><span data-stu-id="74b6b-107">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="74b6b-108">属性は省略されています。</span><span class="sxs-lookup"><span data-stu-id="74b6b-108">Attributes are omitted.</span></span> <span data-ttu-id="74b6b-109">強調表示したコメントは、スキーマの主要なコンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="74b6b-109">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<configuration>  
    <system.identityModel>  
        <!-- Service Configuration -->  
        <identityConfiguration>  
            <caches>  
                <sessionSecurityTokenCache />  
                <tokenReplayCache />  
            </caches>  

            <certificateValidation>  
                <certificateValidator />
            </certificateValidation>  

            <claimsAuthenticationManager />  

            <claimsAuthorizationManager>  
                <optionalConfigurationElement>  
            </claimsAuthorizationManager>  

            <claimTypeRequired>  
                <claimType />
            </claimTypeRequired>  

            <tokenReplayDetection />  

            <!-- Security Token Handler Collection Configuration -->  
            <securityTokenHandlers>  
                <add>  
                    <!-- Can take an optional configuration element which can be one of  
                         the following or a custom element -->  
                    <samlSecurityTokenHandlerRequirement>  
                        <nameClaimType>  
                        <roleClaimType>
                    </samlSecurityTokenHandlerRequirement>  

                    <sessionSecurityTokenHandlerRequirement />  
                    <x509SecurityTokenHandlerRequirement />  
                    <userNameSecurityTokenHandlerRequirement />  
                </add>  
                <clear />  
                <remove />  
                <securityTokenHandlerConfiguration>  
                    <audienceUris>  
                        <add>  
                        <clear>  
                        <remove>  
                    </audienceUris>  

                    <caches>  
                        <sessionSecurityTokenCache />  
                        <tokenReplayCache />  
                    </caches>  

                    <certificateValidation>  
                        <certificateValidator>
                    </certificateValidation>  

                    <issuerNameRegistry>  
                        <!-- Can take an optional configuration element which can be   
                             the <trustedIssuers> element to configure a configuration-based  
                             issuer name registry or can be a custom element -->  
                        <trustedIssuers>  
                            <add>  
                            <clear>  
                            <remove>  
                        </trustedIssuers>  
                    </issuerNameRegistry>  

                    <issuerTokenResolver />  
                    <serviceTokenResolver />  
                    <tokenReplayDetection />  
                </securityTokenHandlerConfiguration>  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  

    <system.identityModel.services>  
        <!-- Federation Authentication Configuration -->  
        <federatedAuthentication>  
            <cookieHandler>  
                <chunkedCookieHandler />  
                <customCookieHandler />  
            </cookieHandler>  

            <serviceCertificate>  
                <certificateReference>  
            </serviceCertificate>  

            <wsFederation />  
        </federatedAuthentication>  
    </system.identityModel.services>  
</configuration>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="74b6b-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="74b6b-110">In This Section</span></span>  

<span data-ttu-id="74b6b-111">[\<system.identityModel>](system-identitymodel.md) アプリケーションの WIF オプションを有効にするための構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="74b6b-111">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
<span data-ttu-id="74b6b-112">[\<system.identityModel.services>](system-identitymodel-services.md) WIF を使用して、パッシブフェデレーションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="74b6b-112">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="74b6b-113">セッション認証モジュール (SAM) とフェデレーション認証モジュール (WSFAM) を構成します。</span><span class="sxs-lookup"><span data-stu-id="74b6b-113">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
