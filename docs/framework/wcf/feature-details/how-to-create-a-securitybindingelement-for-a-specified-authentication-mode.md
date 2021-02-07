---
description: '詳細については、「方法: 指定した認証モードのための説明を作成する」を参照してください。'
title: '方法: 指定した認証モード用の SecurityBindingElement を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: cb0831787b6d54daf561fc2750f1efe81bebfb0f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734478"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="7d926-103">方法: 指定した認証モード用の SecurityBindingElement を作成する</span><span class="sxs-lookup"><span data-stu-id="7d926-103">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>

<span data-ttu-id="7d926-104">Windows Communication Foundation (WCF) では、クライアントとサービスが相互に認証するために使用されるモードがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="7d926-104">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="7d926-105">これらの認証モード用のセキュリティ バインド要素は、次の例のように、<xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの静的メソッドまたは構成を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="7d926-105">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="7d926-106">18認証モードの詳細については、「 [認証モードの認証](securitybindingelement-authentication-modes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d926-106">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d926-107">例</span><span class="sxs-lookup"><span data-stu-id="7d926-107">Example</span></span>  

 <span data-ttu-id="7d926-108">次のコード例では、複数の認証モードのバインディングを作成するメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="7d926-108">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d926-109"><xref:System.ServiceModel.Channels.SecurityBindingElement> オブジェクトのインスタンスが一度作成されると、<xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> や <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A> などの多数のプロパティは変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="7d926-109">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="7d926-110">これらのプロパティで `set` を呼び出しても変更されません。</span><span class="sxs-lookup"><span data-stu-id="7d926-110">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7d926-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d926-111">See also</span></span>

- [<span data-ttu-id="7d926-112">SecurityBindingElement 認証モード</span><span class="sxs-lookup"><span data-stu-id="7d926-112">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)
- [<span data-ttu-id="7d926-113">方法: SecurityBindingElement を使用してカスタム バインドを作成する</span><span class="sxs-lookup"><span data-stu-id="7d926-113">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
