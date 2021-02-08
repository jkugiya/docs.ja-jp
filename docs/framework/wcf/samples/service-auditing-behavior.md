---
description: 詳細については、「サービス監査の動作」を参照してください。
title: サービス監査動作
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: 101f737d790d7e5ec0fdefc3a60695cb3c432c28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793130"
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="2bad6-103">サービス監査動作</span><span class="sxs-lookup"><span data-stu-id="2bad6-103">Service Auditing Behavior</span></span>

<span data-ttu-id="2bad6-104">このサンプルでは、<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> を使用して、サービス操作中にセキュリティ イベントの監査を有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2bad6-104">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="2bad6-105">このサンプルは、 [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="2bad6-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="2bad6-106">サービスとクライアントは、を使用して構成されてい [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-106">The service and client have been configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="2bad6-107">`mode`の属性 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) がに設定され、 `Message` `clientCredentialType` がに設定されてい `Windows` ます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-107">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="2bad6-108">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bad6-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bad6-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2bad6-110">サービス構成ファイルは、次のように `serviceSecurityAudit` 要素を使用して監査を構成します。</span><span class="sxs-lookup"><span data-stu-id="2bad6-110">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="2bad6-111">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2bad6-112">クライアントをシャットダウンするには、コンソール ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2bad6-112">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="2bad6-113">結果として得られる監査ログは、イベント ビューアーを実行して表示できます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-113">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="2bad6-114">監査イベントは既定で、Windows XP の場合はアプリケーション ログに、Windows Server 2003 と Windows Vista の場合はセキュリティ ログに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-114">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="2bad6-115">Windows Server 2008 と Windows 7 では、監査イベントをアプリケーション ログとサービス ログに表示できます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-115">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="2bad6-116">監査イベントの場所は、 `auditLogLocation` 属性を "Application" または "Security" に設定することによって指定できます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-116">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="2bad6-117">詳細については、「 [方法: セキュリティイベントを監査](../feature-details/how-to-audit-wcf-security-events.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bad6-117">For more information, see [How to: Audit Security Events](../feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="2bad6-118">イベントがセキュリティログに書き込まれる場合は、LocalSecurityPolicy-> Enable オブジェクトアクセスを "Success" と "Failure" に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bad6-118">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="2bad6-119">イベント ログを調べる場合、監査イベントのソースは "ServiceModel Audit 3.0.0.0" です。</span><span class="sxs-lookup"><span data-stu-id="2bad6-119">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="2bad6-120">メッセージ認証監査レコードには "MessageAuthentication" のカテゴリがありますが、サービス承認監査レコードには "ServiceAuthorization" のカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="2bad6-120">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="2bad6-121">メッセージ認証監査イベントは、メッセージの改ざんや期限切れの有無、クライアントによるサービス認証の成否などに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-121">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="2bad6-122">このイベントでは、認証の成功または失敗に関する情報とクライアント ID、およびメッセージ送信先のエンドポイントとそのメッセージに関連付けられたアクションに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-122">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="2bad6-123">サービス承認監査イベントは、サービス承認マネージャーによって決定される承認に適用されます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-123">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="2bad6-124">このイベントでは、承認の成功または失敗に関する情報とクライアント ID、メッセージ送信先のエンドポイント、そのメッセージに関連付けられたアクション、受信メッセージから生成された承認コンテキストの ID、およびアクセス決定を行った承認マネージャーの種類に関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2bad6-124">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2bad6-125">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="2bad6-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2bad6-126">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2bad6-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2bad6-127">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2bad6-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2bad6-128">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2bad6-128">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bad6-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bad6-129">See also</span></span>

- [<span data-ttu-id="2bad6-130">監査</span><span class="sxs-lookup"><span data-stu-id="2bad6-130">Auditing</span></span>](../feature-details/auditing-security-events.md)
- [<span data-ttu-id="2bad6-131">方法: セキュリティ イベントを監査する</span><span class="sxs-lookup"><span data-stu-id="2bad6-131">How to: Audit Security Events</span></span>](../feature-details/how-to-audit-wcf-security-events.md)
