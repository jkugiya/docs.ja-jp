---
description: '詳細については、「方法: セッションを必要とするサービスを作成する」を参照してください。'
title: '方法: セッションを必要とするサービスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 362aee23437bb7f45af5a265a9d3ef47bf62915c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734465"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="3261b-103">方法: セッションを必要とするサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="3261b-103">How to: Create a Service That Requires Sessions</span></span>

<span data-ttu-id="3261b-104">セッションでは、複数のエンドポイント間で共有される状態が作成されます。これにより、クライアントとサービス インスタンス間でのコールバック、マルチホップ セキュリティ、関連付けなどの便利な機能を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3261b-104">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="3261b-105">Windows Communication Foundation (WCF) アプリケーションのセッションの詳細については、「 [セッションの使用](../using-sessions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3261b-105">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="3261b-106">バインディングによるセッションのサポートを要求するコントラクトを指定するには</span><span class="sxs-lookup"><span data-stu-id="3261b-106">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="3261b-107">操作を 1 つ以上含むサービス コントラクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3261b-107">Create a service contract with at least one operation.</span></span> <span data-ttu-id="3261b-108">サービスコントラクトを作成する方法の例については、「 [方法: サービスコントラクトを定義](../how-to-define-a-wcf-service-contract.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3261b-108">For an example of how to create a service contract, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="3261b-109">コントラクトを宣言する <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> を変更します。<xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> プロパティを次のいずれかに設定します。</span><span class="sxs-lookup"><span data-stu-id="3261b-109">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    - <span data-ttu-id="3261b-110">セッション内でこのコントラクトの実行を要求する場合は <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3261b-110"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    - <span data-ttu-id="3261b-111">セッション内でこのコントラクトを実行できる場合は <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3261b-111"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    - <span data-ttu-id="3261b-112">セッション内でこのコントラクトの実行を許可しない場合は <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3261b-112"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="3261b-113">セッションをサポートするバインディングを使用するようにサービス エンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="3261b-113">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="3261b-114">次の構成例は、WS<xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>ReliableMessaging セッションをサポートする `-` の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3261b-114">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a><span data-ttu-id="3261b-115">例</span><span class="sxs-lookup"><span data-stu-id="3261b-115">Example</span></span>  

 <span data-ttu-id="3261b-116">コントラクト レベルのセッション要件を指定し、構成ファイルを使用して、その要件を <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> バインディングでサポートする方法を、次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="3261b-116">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a><span data-ttu-id="3261b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3261b-117">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
