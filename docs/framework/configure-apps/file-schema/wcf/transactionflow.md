---
description: '詳細情報: <transactionFlow>'
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 8a853beaec1837606ecb96156b8ec9381fa3e07a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773551"
---
# \<transactionFlow>

<span data-ttu-id="a7549-102">カスタム バインドのトランザクション フロー サポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7549-102">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="a7549-103">構文</span><span class="sxs-lookup"><span data-stu-id="a7549-103">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7549-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a7549-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a7549-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7549-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7549-106">属性</span><span class="sxs-lookup"><span data-stu-id="a7549-106">Attributes</span></span>  
  
|<span data-ttu-id="a7549-107">属性</span><span class="sxs-lookup"><span data-stu-id="a7549-107">Attribute</span></span>|<span data-ttu-id="a7549-108">説明</span><span class="sxs-lookup"><span data-stu-id="a7549-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7549-109">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="a7549-109">transactionProtocol</span></span>|<span data-ttu-id="a7549-110">使用されるトランザクション プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7549-110">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="a7549-111">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a7549-111">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a7549-112">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="a7549-112">-   OleTransactions</span></span><br /><span data-ttu-id="a7549-113">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="a7549-113">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="a7549-114">既定値は OleTransactions です。</span><span class="sxs-lookup"><span data-stu-id="a7549-114">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="a7549-115">この属性は <xref:System.ServiceModel.TransactionProtocol> 型です。</span><span class="sxs-lookup"><span data-stu-id="a7549-115">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7549-116">子要素</span><span class="sxs-lookup"><span data-stu-id="a7549-116">Child Elements</span></span>  

 <span data-ttu-id="a7549-117">なし。</span><span class="sxs-lookup"><span data-stu-id="a7549-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7549-118">親要素</span><span class="sxs-lookup"><span data-stu-id="a7549-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a7549-119">要素</span><span class="sxs-lookup"><span data-stu-id="a7549-119">Element</span></span>|<span data-ttu-id="a7549-120">説明</span><span class="sxs-lookup"><span data-stu-id="a7549-120">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a7549-121">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="a7549-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7549-122">解説</span><span class="sxs-lookup"><span data-stu-id="a7549-122">Remarks</span></span>  

 <span data-ttu-id="a7549-123">この要素により、受信トランザクションの目的のプロトコル形式を指定できるだけでなく、エンドポイントのバインディング設定で受信トランザクション フローを有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="a7549-123">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="a7549-124">この構成要素の使用方法の詳細については、「 [ServiceModel トランザクション構成](../../../wcf/feature-details/servicemodel-transaction-configuration.md) 」および「 [トランザクションフローの有効化](../../../wcf/feature-details/enabling-transaction-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7549-124">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="a7549-125">`OleTransactions` プロトコルを使用してエンドポイント間でトランザクションをフローさせるとき、フロー先のエンドポイントが `OleTransactions` 以外のプロトコルを使用して再びフローを試みると、トランザクション タイムアウトが失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7549-125">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="a7549-126">その結果、OleTransactions ホップより後のすべてのダウンレベル ノードが、予想より遅くタイムアウトする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a7549-126">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7549-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7549-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a7549-128">ServiceModel トランザクションの構成</span><span class="sxs-lookup"><span data-stu-id="a7549-128">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="a7549-129">トランザクション フローの有効化</span><span class="sxs-lookup"><span data-stu-id="a7549-129">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="a7549-130">バインド</span><span class="sxs-lookup"><span data-stu-id="a7549-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a7549-131">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="a7549-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a7549-132">カスタムバインド</span><span class="sxs-lookup"><span data-stu-id="a7549-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
