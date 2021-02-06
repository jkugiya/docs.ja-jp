---
description: '詳細については、「方法: パラメーターを検査または変更する」を参照してください。'
title: '方法: パラメーターを検査または変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 90358f2fbd7366b11135ec2ebd044f7864d8a1e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653785"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="aafbe-103">方法: パラメーターを検査または変更する</span><span class="sxs-lookup"><span data-stu-id="aafbe-103">How to: Inspect or Modify Parameters</span></span>

<span data-ttu-id="aafbe-104">インターフェイスを実装 <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> してクライアントまたはサービスのランタイムに挿入することによって、Windows Communication Foundation (wcf) クライアントオブジェクトまたは wcf サービスでの1つの操作について、受信メッセージまたは送信メッセージを検査または変更できます。</span><span class="sxs-lookup"><span data-stu-id="aafbe-104">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="aafbe-105">通常、操作の動作は、1 回の操作に対してパラメーター インスペクターを追加するために使用します。他の動作は、広い範囲でランタイムへの簡単なアクセスを提供するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="aafbe-105">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="aafbe-106">詳細については、「 [クライアントの拡張](extending-clients.md) 」および「 [ディスパッチャーの拡張](extending-dispatchers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aafbe-106">For more information, see [Extending Clients](extending-clients.md) and [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="aafbe-107">パラメーターの検査と変更</span><span class="sxs-lookup"><span data-stu-id="aafbe-107">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="aafbe-108"><xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="aafbe-108">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="aafbe-109">要求されるスコープに応じて <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> または <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> を実装し、パラメーター インスペクターを <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> プロパティまたは <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="aafbe-109">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="aafbe-110"><xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> に対して <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> メソッドまたは <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> メソッドを呼び出す前に、動作を挿入します。</span><span class="sxs-lookup"><span data-stu-id="aafbe-110">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aafbe-111">詳細については、「動作を使用した [ランタイムの構成と拡張](configuring-and-extending-the-runtime-with-behaviors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aafbe-111">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aafbe-112">例</span><span class="sxs-lookup"><span data-stu-id="aafbe-112">Example</span></span>  

 <span data-ttu-id="aafbe-113">下のコード例では、次の項目を順番に示しています。</span><span class="sxs-lookup"><span data-stu-id="aafbe-113">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="aafbe-114">パラメーター インスペクターの実装</span><span class="sxs-lookup"><span data-stu-id="aafbe-114">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="aafbe-115"><xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、および <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> を使用してパラメーター インスペクターを挿入する動作実装</span><span class="sxs-lookup"><span data-stu-id="aafbe-115">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="aafbe-116">クライアント上にパラメーター インスペクターを挿入するために、クライアント アプリケーションでエンドポイント動作を読み込み、実行する構成ファイル</span><span class="sxs-lookup"><span data-stu-id="aafbe-116">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="aafbe-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="aafbe-117">See also</span></span>

- [<span data-ttu-id="aafbe-118">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="aafbe-118">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
