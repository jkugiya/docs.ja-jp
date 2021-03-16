---
description: '詳細情報: <workflowInstanceManagement>'
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 528c0c923be93d9581b8e3bfccc382eab11c5da1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697921"
---
# \<workflowInstanceManagement>

<span data-ttu-id="d0022-102">ワークフロー インスタンスの実行方法を制御する設定を指定するためのサービス動作。これには、永続する未処理の例外動作やアイドル状態の動作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d0022-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="d0022-103">構文</span><span class="sxs-lookup"><span data-stu-id="d0022-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0022-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d0022-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d0022-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0022-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0022-106">属性</span><span class="sxs-lookup"><span data-stu-id="d0022-106">Attributes</span></span>  
  
|<span data-ttu-id="d0022-107">属性</span><span class="sxs-lookup"><span data-stu-id="d0022-107">Attribute</span></span>|<span data-ttu-id="d0022-108">説明</span><span class="sxs-lookup"><span data-stu-id="d0022-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0022-109">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="d0022-109">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="d0022-110">子要素</span><span class="sxs-lookup"><span data-stu-id="d0022-110">Child Elements</span></span>  

 <span data-ttu-id="d0022-111">なし。</span><span class="sxs-lookup"><span data-stu-id="d0022-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0022-112">親要素</span><span class="sxs-lookup"><span data-stu-id="d0022-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d0022-113">要素</span><span class="sxs-lookup"><span data-stu-id="d0022-113">Element</span></span>|<span data-ttu-id="d0022-114">説明</span><span class="sxs-lookup"><span data-stu-id="d0022-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0022-115">\<serviceBehaviors> の \<behavior></span><span class="sxs-lookup"><span data-stu-id="d0022-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d0022-116">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="d0022-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0022-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0022-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
