---
description: 詳細については <add> 、 <commonParameters>
title: <add> の <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d7a1b78ed79b7eab472460b364b90bd372ecf6bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804011"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="2d304-103">\<add> の \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="2d304-103">\<add> of \<commonParameters></span></span>

<span data-ttu-id="2d304-104">複数のサービスでグローバルに使用されるパラメーターの名前と値のペアを指定します。</span><span class="sxs-lookup"><span data-stu-id="2d304-104">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="2d304-105">このパラメーターには通常、永続性サービスによって共有されるデータベース接続文字列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="2d304-105">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="2d304-106">構文</span><span class="sxs-lookup"><span data-stu-id="2d304-106">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d304-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2d304-107">Attributes and Elements</span></span>  

 <span data-ttu-id="2d304-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d304-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d304-109">属性</span><span class="sxs-lookup"><span data-stu-id="2d304-109">Attributes</span></span>  
  
|<span data-ttu-id="2d304-110">属性</span><span class="sxs-lookup"><span data-stu-id="2d304-110">Attribute</span></span>|<span data-ttu-id="2d304-111">説明</span><span class="sxs-lookup"><span data-stu-id="2d304-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d304-112">name</span><span class="sxs-lookup"><span data-stu-id="2d304-112">name</span></span>|<span data-ttu-id="2d304-113">サービスに対して指定されたパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="2d304-113">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="2d304-114">value</span><span class="sxs-lookup"><span data-stu-id="2d304-114">value</span></span>|<span data-ttu-id="2d304-115">サービスに対して指定されたパラメーターの値。</span><span class="sxs-lookup"><span data-stu-id="2d304-115">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d304-116">子要素</span><span class="sxs-lookup"><span data-stu-id="2d304-116">Child Elements</span></span>  

 <span data-ttu-id="2d304-117">なし。</span><span class="sxs-lookup"><span data-stu-id="2d304-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d304-118">親要素</span><span class="sxs-lookup"><span data-stu-id="2d304-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2d304-119">要素</span><span class="sxs-lookup"><span data-stu-id="2d304-119">Element</span></span>|<span data-ttu-id="2d304-120">説明</span><span class="sxs-lookup"><span data-stu-id="2d304-120">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="2d304-121">サービスによって使用される共通パラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="2d304-121">A collection of common parameters used by services.</span></span> <span data-ttu-id="2d304-122">このコレクションには通常、永続性サービスによって共有されるデータベース接続文字列が格納されます。</span><span class="sxs-lookup"><span data-stu-id="2d304-122">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d304-123">解説</span><span class="sxs-lookup"><span data-stu-id="2d304-123">Remarks</span></span>  

 <span data-ttu-id="2d304-124">最初の要素 `<commonParameters>` は、複数のサービスでグローバルに使用されるパラメーターを定義します (たとえば `ConnectionString` を使用する場合の <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>)。</span><span class="sxs-lookup"><span data-stu-id="2d304-124">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="2d304-125"><xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> や <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> など、作業バッチを永続的ストアにコミットするサービスでは、`EnableRetries` パラメーターを次の例のように使用することで、トランザクションの再試行を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="2d304-125">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="2d304-126">パラメーターは、 `EnableRetries` *commonparameters* セクションに示されているようにグローバルレベルで設定するか `EnableRetries` 、( *サービス* セクションに示すように) をサポートする個々のサービスに対して設定できます。</span><span class="sxs-lookup"><span data-stu-id="2d304-126">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="2d304-127">構成ファイルを使用して Windows Workflow Foundation ホストアプリケーションのオブジェクトの動作を制御する方法の詳細につい <xref:System.Workflow.Runtime.WorkflowRuntime> ては、「 [ワークフロー構成ファイル](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d304-127">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d304-128">例</span><span class="sxs-lookup"><span data-stu-id="2d304-128">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="2d304-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d304-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="2d304-130">[ワークフロー構成ファイル](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2d304-130">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
