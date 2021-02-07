---
description: '詳細については、「方法: 承認中にメタデータ要求を許可する」を参照してください。'
title: '方法: 承認中にメタデータ要求を許可する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: a9f5ab7db73aaa8a2a420a60c3172f1b1a738fb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742746"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="7daea-103">方法: 承認中にメタデータ要求を許可する</span><span class="sxs-lookup"><span data-stu-id="7daea-103">How To: Allow Metadata Requests While Authorizing</span></span>

<span data-ttu-id="7daea-104">カスタム承認中に、メタデータの処理要求を許可することがあります。</span><span class="sxs-lookup"><span data-stu-id="7daea-104">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="7daea-105">ここでは、このような要求を検証する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="7daea-105">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="7daea-106">Windows Communication Foundation (WCF) 承認の詳細については、「 [承認](authorization-in-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7daea-106">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="7daea-107">承認中にメタデータ要求を許可するには</span><span class="sxs-lookup"><span data-stu-id="7daea-107">To allow metadata requests during authorization</span></span>  
  
1. <span data-ttu-id="7daea-108"><xref:System.ServiceModel.ServiceAuthorizationManager> クラスの拡張を作成します。</span><span class="sxs-lookup"><span data-stu-id="7daea-108">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2. <span data-ttu-id="7daea-109"><xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="7daea-109">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="7daea-110">このメソッドは、承認が許可されるかどうかによって、`true` または `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="7daea-110">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="7daea-111">現在のプロシージャに関する情報は、メソッドへのパラメーターとして渡される <xref:System.ServiceModel.OperationContext> にあります。</span><span class="sxs-lookup"><span data-stu-id="7daea-111">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3. <span data-ttu-id="7daea-112">オーバーライドで、コントラクト名、名前空間、およびアクションを確認します。次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7daea-112">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="7daea-113">条件が有効な場合は、`true.` を返します。</span><span class="sxs-lookup"><span data-stu-id="7daea-113">If the conditions are valid, then return `true.`</span></span>  
  
4. <span data-ttu-id="7daea-114">クラスを使用するための拡張ポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7daea-114">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="7daea-115">詳細については、「 [方法: サービスのカスタム承認マネージャーを作成](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7daea-115">For more information, see [How to: Create a Custom Authorization Manager for a Service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7daea-116">例</span><span class="sxs-lookup"><span data-stu-id="7daea-116">Example</span></span>  

 <span data-ttu-id="7daea-117"><xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> メソッドのオーバーライドを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="7daea-117">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7daea-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7daea-118">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="7daea-119">承認</span><span class="sxs-lookup"><span data-stu-id="7daea-119">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="7daea-120">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="7daea-120">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
