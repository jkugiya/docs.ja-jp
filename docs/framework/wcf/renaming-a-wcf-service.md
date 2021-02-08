---
description: 詳細については、「WCF サービスの名前変更」を参照してください。
title: WCF サービス名の変更
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 8d75e43f4bda97e8ee6de34b039eb1236d6c4a6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779167"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="69166-103">WCF サービス名の変更</span><span class="sxs-lookup"><span data-stu-id="69166-103">Renaming a WCF Service</span></span>

<span data-ttu-id="69166-104">このトピックでは、Windows Communication Foundation (WCF) サービスの名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="69166-104">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="69166-105">WCF サービス名の変更</span><span class="sxs-lookup"><span data-stu-id="69166-105">Renaming a WCF Service</span></span>  

 <span data-ttu-id="69166-106">Windows Communication Foundation (WCF) テンプレートでサービスの名前を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="69166-106">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="69166-107">サービスを実装するクラスの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="69166-107">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="69166-108">次の例に示すように、このサービスの構成ファイルで、サービスの名前を新しい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="69166-108">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="69166-109">構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="69166-109">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="69166-110">サービスが web でホストされている場合は、 *\* .svc* ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="69166-110">If your service is webhosted, it uses an *\*.svc* file.</span></span> <span data-ttu-id="69166-111">この svc ファイルを開き、次の例に示すように、サービスの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="69166-111">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="69166-112">自己ホスト アプリケーションには svc ファイルがないので、この手順は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="69166-112">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="69166-113">WCF サービス コントラクト名の変更</span><span class="sxs-lookup"><span data-stu-id="69166-113">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="69166-114">サービス コントラクトの名前を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="69166-114">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="69166-115">サービス コントラクトの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="69166-115">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="69166-116">次の例に示すように、このサービスの構成ファイルで、サービス コントラクトの名前を新しい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="69166-116">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="69166-117">構成ファイルは、ホスト モデルに応じて、app.config または web.config ファイルのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="69166-117">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
