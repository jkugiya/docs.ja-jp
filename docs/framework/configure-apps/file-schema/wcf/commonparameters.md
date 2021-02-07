---
description: '詳細情報: <commonParameters>'
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: a9d230fb0f205315dc52357119e6b35752abc96d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698376"
---
# \<commonParameters>

<span data-ttu-id="58682-102">複数のサービスでグローバルに使用されるパラメーターのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58682-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="58682-103">このコレクションには通常、永続性サービスによって共有されるデータベース接続文字列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="58682-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="58682-104">構文</span><span class="sxs-lookup"><span data-stu-id="58682-104">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58682-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="58682-105">Attributes and Elements</span></span>  

 <span data-ttu-id="58682-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="58682-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58682-107">属性</span><span class="sxs-lookup"><span data-stu-id="58682-107">Attributes</span></span>  

 <span data-ttu-id="58682-108">なし。</span><span class="sxs-lookup"><span data-stu-id="58682-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58682-109">子要素</span><span class="sxs-lookup"><span data-stu-id="58682-109">Child Elements</span></span>  
  
|<span data-ttu-id="58682-110">要素</span><span class="sxs-lookup"><span data-stu-id="58682-110">Element</span></span>|<span data-ttu-id="58682-111">説明</span><span class="sxs-lookup"><span data-stu-id="58682-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|<span data-ttu-id="58682-112">サービスによって使用される共通パラメーターの名前と値のペアをコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="58682-112">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58682-113">親要素</span><span class="sxs-lookup"><span data-stu-id="58682-113">Parent Elements</span></span>  
  
|<span data-ttu-id="58682-114">要素</span><span class="sxs-lookup"><span data-stu-id="58682-114">Element</span></span>|<span data-ttu-id="58682-115">説明</span><span class="sxs-lookup"><span data-stu-id="58682-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="58682-116"><xref:System.Workflow.Runtime.WorkflowRuntime>ワークフローベースの Windows Communication Foundation (WCF) サービスをホストするためののインスタンスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="58682-116">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58682-117">解説</span><span class="sxs-lookup"><span data-stu-id="58682-117">Remarks</span></span>  

 <span data-ttu-id="58682-118">最初の要素 `<commonParameters>` は、複数のサービスでグローバルに使用されるパラメーターを定義します (たとえば `ConnectionString` を使用する場合の <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>)。</span><span class="sxs-lookup"><span data-stu-id="58682-118">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58682-119">SQL 追跡サービスでは、`ConnectionString` セクションに `<commonParameters>` 値を指定しても、その値が常に使用されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="58682-119">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="58682-120">`StateMachineWorkflowInstance.StateHistory` プロパティの取得のように、操作によっては失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="58682-120">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="58682-121">これを回避するには、次の例に示すように、追跡プロバイダーの構成セクションで `ConnectionString` 属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="58682-121">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="58682-122"><xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> や <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> など、作業バッチを永続的ストアにコミットするサービスでは、`EnableRetries` パラメーターを次の例のように使用することで、トランザクションの再試行を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="58682-122">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="58682-123">パラメーターは、 `EnableRetries` *commonparameters* セクションに示されているようにグローバルレベルで設定するか `EnableRetries` 、( *サービス* セクションに示すように) をサポートする個々のサービスに対して設定できます。</span><span class="sxs-lookup"><span data-stu-id="58682-123">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="58682-124">次のサンプルコードは、一般的なパラメーターをプログラムで変更する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="58682-124">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="58682-125">構成ファイルを使用して Windows Workflow Foundation ホストアプリケーションのオブジェクトの動作を制御する方法の詳細について <xref:System.Workflow.Runtime.WorkflowRuntime> は、「 [ワークフロー構成ファイル](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58682-125">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58682-126">例</span><span class="sxs-lookup"><span data-stu-id="58682-126">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="58682-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="58682-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="58682-128">[ワークフロー構成ファイル](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="58682-128">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<add>](add-of-commonparameters.md)
