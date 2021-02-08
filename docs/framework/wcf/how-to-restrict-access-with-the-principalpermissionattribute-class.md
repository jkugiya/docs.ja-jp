---
description: '詳細については、「方法: PrincipalPermissionAttribute クラスを使用してアクセスを制限する」を参照してください。'
title: '方法: PrincipalPermissionAttribute クラスでアクセスを制限する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 533bd3358d5e337071c6419264d1dac03b8987ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779349"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="fa540-103">方法: PrincipalPermissionAttribute クラスでアクセスを制限する</span><span class="sxs-lookup"><span data-stu-id="fa540-103">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>

<span data-ttu-id="fa540-104">Windows ドメイン コンピューターのリソースへのアクセスを制御することは、基本的なセキュリティ タスクです。</span><span class="sxs-lookup"><span data-stu-id="fa540-104">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="fa540-105">たとえば、給与情報のような機密データは、特定のユーザーだけが表示できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa540-105">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="fa540-106">ここでは、ユーザーが定義済みグループに属していることを要求することによって、メソッドへのアクセスを制限する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa540-106">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="fa540-107">実際のサンプルについては、「 [サービス操作へのアクセスの承認](./samples/authorizing-access-to-service-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa540-107">For a working sample, see [Authorizing Access to Service Operations](./samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="fa540-108">タスクは、2 つの別個の手順で構成されます。</span><span class="sxs-lookup"><span data-stu-id="fa540-108">The task consists of two separate procedures.</span></span> <span data-ttu-id="fa540-109">最初の手順では、グループを作成してユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="fa540-109">The first creates the group and populates it with users.</span></span> <span data-ttu-id="fa540-110">2 番目の手順では、グループを指定するために <xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="fa540-110">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="fa540-111">Windows グループを作成するには</span><span class="sxs-lookup"><span data-stu-id="fa540-111">To create a Windows group</span></span>  
  
1. <span data-ttu-id="fa540-112">コンピューターの **管理** コンソールを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa540-112">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="fa540-113">左側のパネルで、[ **ローカルユーザーとグループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa540-113">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="fa540-114">[ **グループ**] を右クリックし、[ **新しいグループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa540-114">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="fa540-115">[ **グループ名** ] ボックスに、新しいグループの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fa540-115">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="fa540-116">[ **説明** ] ボックスに、新しいグループの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="fa540-116">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="fa540-117">[ **追加** ] ボタンをクリックして、グループに新しいメンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="fa540-117">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="fa540-118">自分自身をグループに追加した場合は、次のコードをテストする前に、コンピューターからいったんログオフし、再度ログオンして自分自身をグループに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa540-118">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="fa540-119">ユーザー メンバーシップを要求するには</span><span class="sxs-lookup"><span data-stu-id="fa540-119">To demand user membership</span></span>  
  
1. <span data-ttu-id="fa540-120">実装されたサービスコントラクトコードを含む Windows Communication Foundation (WCF) コードファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa540-120">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="fa540-121">コントラクトの実装の詳細については、「 [サービスコントラクトの実装](implementing-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa540-121">For more information about implementing a contract, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="fa540-122">特定のグループに制限される必要がある各メソッドに <xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="fa540-122">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="fa540-123"><xref:System.Security.Permissions.SecurityAttribute.Action%2A> プロパティを <xref:System.Security.Permissions.SecurityAction.Demand> に設定し、<xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> プロパティをグループの名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa540-123">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="fa540-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fa540-124">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="fa540-125"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性をコントラクトに適用すると、<xref:System.Security.SecurityException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fa540-125">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="fa540-126">この属性はメソッド レベルにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="fa540-126">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="fa540-127">証明書を使用したメソッドへのアクセスの制御</span><span class="sxs-lookup"><span data-stu-id="fa540-127">Using a Certificate to Control Access to a Method</span></span>  

 <span data-ttu-id="fa540-128">クライアント資格情報の種類が "証明書" の場合は、`PrincipalPermissionAttribute` クラスを使用してメソッドへのアクセスを制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="fa540-128">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="fa540-129">そのためには、証明書のサブジェクトと拇印が必要になります。</span><span class="sxs-lookup"><span data-stu-id="fa540-129">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="fa540-130">証明書のプロパティを調べるには、「 [方法: MMC スナップインを使用して証明書を表示](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa540-130">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="fa540-131">サムプリント値を調べるには、「 [方法: 証明書のサムプリントを取得](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa540-131">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="fa540-132">証明書を使用してアクセスを制御するには</span><span class="sxs-lookup"><span data-stu-id="fa540-132">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="fa540-133">アクセスを制限するメソッドに <xref:System.Security.Permissions.PrincipalPermissionAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="fa540-133">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="fa540-134">属性のアクションを <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType> に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa540-134">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="fa540-135">`Name` プロパティを、サブジェクト名と証明書の拇印で構成される文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa540-135">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="fa540-136">次の例に示すように、2 つの値をセミコロンと空白で区切ってください。</span><span class="sxs-lookup"><span data-stu-id="fa540-136">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="fa540-137">次の構成例に示すように、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> プロパティを <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> に設定します。</span><span class="sxs-lookup"><span data-stu-id="fa540-137">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="fa540-138">この値を `UseAspNetRoles` に設定すると、`Name` の `PrincipalPermissionAttribute` プロパティを使用して文字列が比較されます。</span><span class="sxs-lookup"><span data-stu-id="fa540-138">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="fa540-139">証明書がクライアント資格情報として使用されている場合、既定では、WCF は証明書の共通名と拇印をセミコロンで連結し、クライアントのプライマリ id に一意の値を作成します。</span><span class="sxs-lookup"><span data-stu-id="fa540-139">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="fa540-140">`UseAspNetRoles` をサービスの `PrincipalPermissionMode` として設定している場合、このプライマリ ID の値と `Name` プロパティの値を比較してユーザーのアクセス権が決定されます。</span><span class="sxs-lookup"><span data-stu-id="fa540-140">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="fa540-141">また、自己ホスト型サービスを作成する場合は、次のコードに示すように、コードの <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="fa540-141">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fa540-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa540-142">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="fa540-143">サービス操作へのアクセスの承認</span><span class="sxs-lookup"><span data-stu-id="fa540-143">Authorizing Access to Service Operations</span></span>](./samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="fa540-144">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="fa540-144">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="fa540-145">サービス コントラクトの実装</span><span class="sxs-lookup"><span data-stu-id="fa540-145">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
