---
description: '詳細については、「方法: ProtectionLevel プロパティを設定する」を参照してください。'
title: '方法: ProtectionLevel プロパティを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 526ed923d254f0312c9a2c6d17b7306973d88902
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779245"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="b1b5c-103">方法: ProtectionLevel プロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="b1b5c-103">How to: Set the ProtectionLevel Property</span></span>

<span data-ttu-id="b1b5c-104">適切な属性を適用してプロパティを設定することで、保護レベルを設定できます。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-104">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="b1b5c-105">サービス レベルですべてのメッセージのすべての部分に影響する保護を設定したり、メソッドからメッセージ部分まで、段階的にきめ細かなレベルで保護を設定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-105">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="b1b5c-106">プロパティの詳細につい `ProtectionLevel` ては、「 [保護レベル](understanding-protection-level.md)について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-106">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](understanding-protection-level.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1b5c-107">保護レベルは構成ではなく、コードでのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-107">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="b1b5c-108">サービスのすべてのメッセージに署名するには</span><span class="sxs-lookup"><span data-stu-id="b1b5c-108">To sign all messages for a service</span></span>  
  
1. <span data-ttu-id="b1b5c-109">サービス用のインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-109">Create an interface for the service.</span></span>  
  
2. <span data-ttu-id="b1b5c-110">次のコードに示すように、<xref:System.ServiceModel.ServiceContractAttribute> 属性をサービスに適用し、<xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> プロパティを <xref:System.Net.Security.ProtectionLevel.Sign> に設定します (既定のレベルは <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>)。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-110">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="b1b5c-111">操作のすべてのメッセージ部分に署名するには</span><span class="sxs-lookup"><span data-stu-id="b1b5c-111">To sign all message parts for an operation</span></span>  
  
1. <span data-ttu-id="b1b5c-112">サービスのインターフェイスを作成し、このインターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-112">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2. <span data-ttu-id="b1b5c-113">インターフェイスにメソッド宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-113">Add a method declaration to the interface.</span></span>  
  
3. <span data-ttu-id="b1b5c-114">次のコードに示すように、メソッドに <xref:System.ServiceModel.OperationContractAttribute> 属性を適用し、<xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> プロパティを <xref:System.Net.Security.ProtectionLevel.Sign> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="b1b5c-115">エラー メッセージの保護</span><span class="sxs-lookup"><span data-stu-id="b1b5c-115">Protecting Fault Messages</span></span>  

 <span data-ttu-id="b1b5c-116">サービスでスローされた例外は、SOAP エラーとしてクライアントに送信できます。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-116">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="b1b5c-117">厳密に型指定されたエラーの作成の詳細については、「 [コントラクトとサービスのエラーの指定と処理](specifying-and-handling-faults-in-contracts-and-services.md) 」および「 [方法: サービスコントラクトでエラーを宣言する](how-to-declare-faults-in-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-117">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="b1b5c-118">エラー メッセージを保護するには</span><span class="sxs-lookup"><span data-stu-id="b1b5c-118">To protect a fault message</span></span>  
  
1. <span data-ttu-id="b1b5c-119">エラー メッセージを表す型を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-119">Create a type that represents the fault message.</span></span> <span data-ttu-id="b1b5c-120">次の例では、2 つのフィールドを持つ `MathFault` という名前のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-120">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2. <span data-ttu-id="b1b5c-121">次のコードに示すように、型に <xref:System.Runtime.Serialization.DataContractAttribute> 属性を適用し、シリアル化する必要のある各フィールドに <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-121">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. <span data-ttu-id="b1b5c-122">エラーを返すインターフェイスで、エラーを返すメソッドに <xref:System.ServiceModel.FaultContractAttribute> 属性を適用し、エラー クラスの型に `detailType` パラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-122">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4. <span data-ttu-id="b1b5c-123">次のコードに示すように、コンストラクターでも、<xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> プロパティを <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-123">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="b1b5c-124">メッセージ部分の保護</span><span class="sxs-lookup"><span data-stu-id="b1b5c-124">Protecting Message Parts</span></span>  

 <span data-ttu-id="b1b5c-125">メッセージ部分を保護するには、メッセージ コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-125">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="b1b5c-126">メッセージコントラクトの詳細については、「 [Using Message contracts](./feature-details/using-message-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-126">For more information about message contracts, see [Using Message Contracts](./feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="b1b5c-127">メッセージ本文を保護するには</span><span class="sxs-lookup"><span data-stu-id="b1b5c-127">To protect a message body</span></span>  
  
1. <span data-ttu-id="b1b5c-128">メッセージを表す型を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-128">Create a type that represents the message.</span></span> <span data-ttu-id="b1b5c-129">次の例では、`Company` と `CompanyName` の 2 つのフィールドを持つ `CompanyID` クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-129">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2. <span data-ttu-id="b1b5c-130">このクラスに <xref:System.ServiceModel.MessageContractAttribute> 属性を適用し、<xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> プロパティを <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-130">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3. <span data-ttu-id="b1b5c-131">メッセージ ヘッダーとして表現されるフィールドに <xref:System.ServiceModel.MessageHeaderAttribute> 属性を適用し、`ProtectionLevel` プロパティを <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-131">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4. <span data-ttu-id="b1b5c-132">次の <xref:System.ServiceModel.MessageBodyMemberAttribute> `ProtectionLevel` 例に示すように、メッセージ本文の一部として表現される任意のフィールドにを適用し、プロパティをに設定し <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> ます。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-132">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b1b5c-133">例</span><span class="sxs-lookup"><span data-stu-id="b1b5c-133">Example</span></span>  

 <span data-ttu-id="b1b5c-134">次の例では、サービスのいろいろな場所で、いくつかの属性クラスの `ProtectionLevel` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-134">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1b5c-135">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b1b5c-135">Compiling the Code</span></span>  

 <span data-ttu-id="b1b5c-136">コード例のコンパイルに必要な名前空間を、次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b1b5c-136">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="b1b5c-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1b5c-137">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="b1b5c-138">保護レベルの理解</span><span class="sxs-lookup"><span data-stu-id="b1b5c-138">Understanding Protection Level</span></span>](understanding-protection-level.md)
