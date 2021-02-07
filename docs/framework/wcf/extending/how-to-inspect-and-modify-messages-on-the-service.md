---
description: '詳細については、「方法: サービスのメッセージを検査および変更する」を参照してください。'
title: '方法: サービスのメッセージを検査および変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 5fd3a5e49bdd35a3095e5855b399533337e133a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668878"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="0dc81-103">方法: サービスのメッセージを検査および変更する</span><span class="sxs-lookup"><span data-stu-id="0dc81-103">How to: Inspect and Modify Messages on the Service</span></span>

<span data-ttu-id="0dc81-104">を実装 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> してサービスランタイムに挿入することによって、Windows Communication Foundation (WCF) クライアント全体で受信メッセージまたは送信メッセージを検査または変更できます。</span><span class="sxs-lookup"><span data-stu-id="0dc81-104">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="0dc81-105">詳細については、「 [ディスパッチャーの拡張](extending-dispatchers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0dc81-105">For more information, see [Extending Dispatchers](extending-dispatchers.md).</span></span> <span data-ttu-id="0dc81-106">サービスの同等の機能は、<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="0dc81-106">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="0dc81-107">メッセージを検査または変更するには</span><span class="sxs-lookup"><span data-stu-id="0dc81-107">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="0dc81-108"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="0dc81-108">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="0dc81-109">サービス メッセージ インスペクターを容易に挿入したいスコープに応じて、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、または <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="0dc81-109">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3. <span data-ttu-id="0dc81-110"><xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> で <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> メソッドを呼び出す前に、動作を挿入します。</span><span class="sxs-lookup"><span data-stu-id="0dc81-110">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0dc81-111">詳細については、「動作を使用した [ランタイムの構成と拡張](configuring-and-extending-the-runtime-with-behaviors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0dc81-111">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dc81-112">例</span><span class="sxs-lookup"><span data-stu-id="0dc81-112">Example</span></span>  

 <span data-ttu-id="0dc81-113">下のコード例では、次の項目を順番に示しています。</span><span class="sxs-lookup"><span data-stu-id="0dc81-113">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="0dc81-114">サービス インスペクターの実装</span><span class="sxs-lookup"><span data-stu-id="0dc81-114">A service inspector implementation.</span></span>  
  
- <span data-ttu-id="0dc81-115">インスペクターを挿入するサービス動作</span><span class="sxs-lookup"><span data-stu-id="0dc81-115">A service behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="0dc81-116">サービス アプリケーションに動作を読み込んで実行する構成ファイル</span><span class="sxs-lookup"><span data-stu-id="0dc81-116">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="0dc81-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dc81-117">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="0dc81-118">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="0dc81-118">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
