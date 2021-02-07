---
description: '詳細情報: <serviceSecurityAudit>'
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 262341f44adb7657086edb8d33514c07195ddfa3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682749"
---
# \<serviceSecurityAudit>

<span data-ttu-id="6994c-102">サービス操作中にセキュリティ イベントの監査を有効にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="6994c-102">Specifies settings that enable auditing of security events during service operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceSecurityAudit>**  
  
## <a name="syntax"></a><span data-ttu-id="6994c-103">構文</span><span class="sxs-lookup"><span data-stu-id="6994c-103">Syntax</span></span>  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6994c-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6994c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6994c-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6994c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6994c-106">属性</span><span class="sxs-lookup"><span data-stu-id="6994c-106">Attributes</span></span>  
  
|<span data-ttu-id="6994c-107">属性</span><span class="sxs-lookup"><span data-stu-id="6994c-107">Attribute</span></span>|<span data-ttu-id="6994c-108">説明</span><span class="sxs-lookup"><span data-stu-id="6994c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6994c-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="6994c-109">auditLogLocation</span></span>|<span data-ttu-id="6994c-110">監査ログの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="6994c-110">Specifies the location of the audit log.</span></span> <span data-ttu-id="6994c-111">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6994c-111">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6994c-112">-既定: セキュリティイベントは、windows XP の場合はアプリケーションログに、windows Server 2003 および Windows Vista の場合はイベントログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="6994c-112">-   Default: Security events are written to the application log on Windows XP, and to the Event Log on Windows Server 2003 and Windows Vista.</span></span><br /><span data-ttu-id="6994c-113">-Application: 監査イベントは、アプリケーションイベントログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="6994c-113">-   Application: Audit events are written to the Application Event Log.</span></span><br /><span data-ttu-id="6994c-114">-Security: 監査イベントは、セキュリティイベントログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="6994c-114">-   Security: Audit events are written to the Security Event Log.</span></span><br /><br /> <span data-ttu-id="6994c-115">既定値は Default です。</span><span class="sxs-lookup"><span data-stu-id="6994c-115">The default value is Default.</span></span> <span data-ttu-id="6994c-116">詳細については、「<xref:System.ServiceModel.AuditLogLocation>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6994c-116">For more information, see <xref:System.ServiceModel.AuditLogLocation>.</span></span>|  
|<span data-ttu-id="6994c-117">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="6994c-117">suppressAuditFailure</span></span>|<span data-ttu-id="6994c-118">監査ログへの書き込みエラーを非表示にする動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="6994c-118">A Boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span><br /><br /> <span data-ttu-id="6994c-119">アプリケーションには、監査ログへの書き込みエラーを通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6994c-119">Applications should be notified for failures of writing to the audit log.</span></span> <span data-ttu-id="6994c-120">アプリケーションが監査エラーを処理するように設計されていない場合は、この属性を使用して、監査ログへの書き込みでのエラーが表示されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6994c-120">If your application is not designed to handle audit failures, you should use this attribute to suppress failures in writing to the audit log.</span></span><br /><br /> <span data-ttu-id="6994c-121">この属性が `true` の場合、監査イベントの書き込み試行の結果発生する例外 (ただし、OutOfMemoryException、StackOverFlowException、ThreadAbortException、および ArgumentException を除く) はシステムによって処理され、アプリケーションには伝達されません。</span><span class="sxs-lookup"><span data-stu-id="6994c-121">If this attribute is `true`, exceptions other than OutOfMemoryException, StackOverFlowException, ThreadAbortException, and ArgumentException that result from attempts to write audit events are handled by the system, and are not propagated to the application.</span></span> <span data-ttu-id="6994c-122">この属性が `false` の場合、監査イベントの書き込み試行の結果発生する例外は、すべてアプリケーションまで渡されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-122">If this attribute is `false`, all exceptions that result from attempts to write audit events are passed up to the application.</span></span><br /><br /> <span data-ttu-id="6994c-123">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="6994c-123">The default is `true`.</span></span>|  
|<span data-ttu-id="6994c-124">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="6994c-124">serviceAuthorizationAuditLevel</span></span>|<span data-ttu-id="6994c-125">監査ログに記録される承認イベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6994c-125">Specifies the types of authorization events that are recorded in the audit log.</span></span> <span data-ttu-id="6994c-126">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6994c-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6994c-127">-None: サービス承認イベントの監査は実行されません。</span><span class="sxs-lookup"><span data-stu-id="6994c-127">-   None: No auditing of service authorization events is performed.</span></span><br /><span data-ttu-id="6994c-128">-Success: 成功したサービス承認イベントだけが監査されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-128">-   Success: Only successful service authorization events are audited.</span></span><br /><span data-ttu-id="6994c-129">-Failure: 失敗したサービス承認イベントだけが監査されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-129">-   Failure: Only failure service authorization events are audited.</span></span><br /><span data-ttu-id="6994c-130">-SuccessOrFailure: 成功と失敗の両方のサービス承認イベントが監査されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-130">-   SuccessOrFailure: Both success and failure service authorization events are audited.</span></span><br /><br /> <span data-ttu-id="6994c-131">既定値は None です。</span><span class="sxs-lookup"><span data-stu-id="6994c-131">The default value is None.</span></span> <span data-ttu-id="6994c-132">詳細については、「<xref:System.ServiceModel.AuditLevel>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6994c-132">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
|<span data-ttu-id="6994c-133">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="6994c-133">messageAuthenticationAuditLevel</span></span>|<span data-ttu-id="6994c-134">ログに記録されるメッセージ認証監査イベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6994c-134">Specifies the type of message authentication audit events logged.</span></span> <span data-ttu-id="6994c-135">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6994c-135">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6994c-136">-None: 監査イベントは生成されません。</span><span class="sxs-lookup"><span data-stu-id="6994c-136">-   None: No audit events are generated.</span></span><br /><span data-ttu-id="6994c-137">-Success: 成功したセキュリティ (メッセージ署名の検証、暗号、トークンの検証を含む完全な検証) イベントのみが記録されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-137">-   Success: Only successful security (full validation including message signature validation, cipher, and token validation) events are logged.</span></span><br /><span data-ttu-id="6994c-138">-Failure: エラーイベントのみがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-138">-   Failure: Only failure events are logged.</span></span><br /><span data-ttu-id="6994c-139">-SuccessOrFailure: 成功イベントと失敗イベントの両方がログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-139">-   SuccessOrFailure: Both success and failure events are logged.</span></span><br /><br /> <span data-ttu-id="6994c-140">既定値は None です。</span><span class="sxs-lookup"><span data-stu-id="6994c-140">The default value is None.</span></span> <span data-ttu-id="6994c-141">詳細については、「<xref:System.ServiceModel.AuditLevel>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6994c-141">For more information, see <xref:System.ServiceModel.AuditLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6994c-142">子要素</span><span class="sxs-lookup"><span data-stu-id="6994c-142">Child Elements</span></span>  

 <span data-ttu-id="6994c-143">なし。</span><span class="sxs-lookup"><span data-stu-id="6994c-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6994c-144">親要素</span><span class="sxs-lookup"><span data-stu-id="6994c-144">Parent Elements</span></span>  
  
|<span data-ttu-id="6994c-145">要素</span><span class="sxs-lookup"><span data-stu-id="6994c-145">Element</span></span>|<span data-ttu-id="6994c-146">説明</span><span class="sxs-lookup"><span data-stu-id="6994c-146">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6994c-147">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="6994c-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6994c-148">解説</span><span class="sxs-lookup"><span data-stu-id="6994c-148">Remarks</span></span>  

 <span data-ttu-id="6994c-149">この構成要素は、Windows Communication Foundation (WCF) 認証イベントを監査するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-149">This configuration element is used to audit Windows Communication Foundation (WCF) authentication events.</span></span> <span data-ttu-id="6994c-150">監査を有効にすると、成功した認証、失敗した認証、またはその両方を監査できます。</span><span class="sxs-lookup"><span data-stu-id="6994c-150">When auditing is enabled, either successful or failed authentication attempts (or both) can be audited.</span></span> <span data-ttu-id="6994c-151">イベントは、3 種類のイベント ログ (アプリケーション ログ、セキュリティ ログ、およびオペレーティング システムのバージョンに対する既定のログ) のいずれかに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="6994c-151">The events are written to one of three event logs: application, security, or the default log for the operating system version.</span></span> <span data-ttu-id="6994c-152">イベント ログはすべて、Windows イベント ビューアーを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="6994c-152">The event logs can all be viewed using the Windows Event viewer.</span></span>  
  
 <span data-ttu-id="6994c-153">この構成要素の使用例については、「 [サービス監査の動作](../../../wcf/samples/service-auditing-behavior.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6994c-153">For a detailed example of using this configuration element, see [Service Auditing Behavior](../../../wcf/samples/service-auditing-behavior.md).</span></span>  
  
 <span data-ttu-id="6994c-154">監査イベントは既定で、Windows XP の場合はアプリケーション ログに、Windows Server 2003 と Windows Vista の場合はセキュリティ ログに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-154">By default, on Windows XP the audit events can be seen in the Application Log; while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="6994c-155">監査イベントの場所は、`auditLogLocation` 属性を "Application" または "Security" に設定することによって指定できます。</span><span class="sxs-lookup"><span data-stu-id="6994c-155">The location of audit events can be specified by setting the `auditLogLocation` attribute to 'Application' or 'Security'.</span></span> <span data-ttu-id="6994c-156">詳細については、「 [方法: セキュリティイベントを監査](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6994c-156">For more information, see [How to: Audit Security Events](../../../wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="6994c-157">イベントがセキュリティログに書き込まれた場合は、LocalSecurityPolicy-> Enable オブジェクトアクセスを "Success" と "Failure" に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6994c-157">If the events are written in the Security Log, the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="6994c-158">イベント ログを調べる場合、監査イベントのソースは "ServiceModel Audit 3.0.0.0" です。</span><span class="sxs-lookup"><span data-stu-id="6994c-158">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="6994c-159">メッセージ認証監査レコードには "MessageAuthentication" のカテゴリ、サービス承認監査レコードには "ServiceAuthorization" のカテゴリが設定されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-159">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of 'ServiceAuthorization'.</span></span>  
  
 <span data-ttu-id="6994c-160">メッセージ認証監査イベントは、メッセージの改ざんや期限切れの有無、クライアントによるサービス認証の成否などに適用されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-160">Message authentication audit events cover whether the message was tampered with, whether the message has expired and whether the client can authenticate to the service.</span></span> <span data-ttu-id="6994c-161">このイベントでは、認証の成功または失敗に関する情報とクライアント ID、およびメッセージ送信先のエンドポイントとそのメッセージに関連付けられたアクションに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-161">They provide information about whether the authentication succeeded or failed along with the identity of the client and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="6994c-162">サービス承認監査イベントは、サービス承認マネージャーによって決定される承認に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6994c-162">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="6994c-163">これらの情報は、承認が成功したか失敗したか、クライアントの id、メッセージが送信されたエンドポイント、メッセージに関連付けられたアクション、受信メッセージから生成された承認コンテキストの識別子、およびアクセス決定を行った承認マネージャーの種類に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="6994c-163">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message and the type of the authorization manager that made the access decision.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6994c-164">例</span><span class="sxs-lookup"><span data-stu-id="6994c-164">Example</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <serviceBehaviors>
      <behavior name="NewBehavior">
        <serviceSecurityAudit auditLogLocation="Application"
                              suppressAuditFailure="true"
                              serviceAuthorizationAuditLevel="Success"
                              messageAuthenticationAuditLevel="Success" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="6994c-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="6994c-165">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [<span data-ttu-id="6994c-166">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="6994c-166">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6994c-167">監査</span><span class="sxs-lookup"><span data-stu-id="6994c-167">Auditing</span></span>](../../../wcf/feature-details/auditing-security-events.md)
- [<span data-ttu-id="6994c-168">方法: セキュリティ イベントを監査する</span><span class="sxs-lookup"><span data-stu-id="6994c-168">How to: Audit Security Events</span></span>](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [<span data-ttu-id="6994c-169">サービス監査動作</span><span class="sxs-lookup"><span data-stu-id="6994c-169">Service Auditing Behavior</span></span>](../../../wcf/samples/service-auditing-behavior.md)
