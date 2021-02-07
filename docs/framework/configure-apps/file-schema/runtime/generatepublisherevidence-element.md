---
description: '詳細情報: <generatePublisherEvidence> 要素'
title: <generatePublisherEvidence> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 2a949b52abe5ec10872d2cade49a0556063b2018
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754525"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="b70e0-103">\<generatePublisherEvidence> 要素</span><span class="sxs-lookup"><span data-stu-id="b70e0-103">\<generatePublisherEvidence> Element</span></span>

<span data-ttu-id="b70e0-104">ランタイムが <xref:System.Security.Policy.Publisher> コードアクセスセキュリティ (CAS) の証拠を作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b70e0-104">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="b70e0-105">構文</span><span class="sxs-lookup"><span data-stu-id="b70e0-105">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b70e0-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b70e0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b70e0-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b70e0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b70e0-108">属性</span><span class="sxs-lookup"><span data-stu-id="b70e0-108">Attributes</span></span>  
  
|<span data-ttu-id="b70e0-109">属性</span><span class="sxs-lookup"><span data-stu-id="b70e0-109">Attribute</span></span>|<span data-ttu-id="b70e0-110">説明</span><span class="sxs-lookup"><span data-stu-id="b70e0-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b70e0-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="b70e0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="b70e0-112">ランタイムが証拠を作成するかどうかを指定し <xref:System.Security.Policy.Publisher> ます。</span><span class="sxs-lookup"><span data-stu-id="b70e0-112">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b70e0-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="b70e0-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="b70e0-114">値</span><span class="sxs-lookup"><span data-stu-id="b70e0-114">Value</span></span>|<span data-ttu-id="b70e0-115">説明</span><span class="sxs-lookup"><span data-stu-id="b70e0-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b70e0-116">は <xref:System.Security.Policy.Publisher> 証拠を作成しません。</span><span class="sxs-lookup"><span data-stu-id="b70e0-116">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="b70e0-117"><xref:System.Security.Policy.Publisher>証拠を作成します。</span><span class="sxs-lookup"><span data-stu-id="b70e0-117">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="b70e0-118">既定値です。</span><span class="sxs-lookup"><span data-stu-id="b70e0-118">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b70e0-119">子要素</span><span class="sxs-lookup"><span data-stu-id="b70e0-119">Child Elements</span></span>  

 <span data-ttu-id="b70e0-120">なし。</span><span class="sxs-lookup"><span data-stu-id="b70e0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b70e0-121">親要素</span><span class="sxs-lookup"><span data-stu-id="b70e0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b70e0-122">要素</span><span class="sxs-lookup"><span data-stu-id="b70e0-122">Element</span></span>|<span data-ttu-id="b70e0-123">説明</span><span class="sxs-lookup"><span data-stu-id="b70e0-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b70e0-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="b70e0-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b70e0-125">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="b70e0-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b70e0-126">解説</span><span class="sxs-lookup"><span data-stu-id="b70e0-126">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b70e0-127">.NET Framework 4 以降では、この要素はアセンブリの読み込み時間に影響しません。</span><span class="sxs-lookup"><span data-stu-id="b70e0-127">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="b70e0-128">詳細については、「セキュリティの [変更](/previous-versions/dotnet/framework/security/security-changes)」の「セキュリティポリシーの簡略化」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b70e0-128">For more information, see the "Security Policy Simplification" section in [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="b70e0-129">共通言語ランタイム (CLR) は、読み込み時に Authenticode 署名を検証して、アセンブリの証拠を作成しようとし <xref:System.Security.Policy.Publisher> ます。</span><span class="sxs-lookup"><span data-stu-id="b70e0-129">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="b70e0-130">ただし、既定では、ほとんどのアプリケーションは証拠を必要としません <xref:System.Security.Policy.Publisher> 。</span><span class="sxs-lookup"><span data-stu-id="b70e0-130">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="b70e0-131">標準の CAS ポリシーは、に依存 <xref:System.Security.Policy.PublisherMembershipCondition> しません。</span><span class="sxs-lookup"><span data-stu-id="b70e0-131">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="b70e0-132">カスタム CAS ポリシーを使用しているコンピューターでアプリケーションを実行する場合や、部分信頼環境での要求を満たす場合を除き、発行元の署名の検証に関連する不要な起動コストを回避する必要があり <xref:System.Security.Permissions.PublisherIdentityPermission> ます。</span><span class="sxs-lookup"><span data-stu-id="b70e0-132">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="b70e0-133">(Id 権限の要求は、完全に信頼された環境では常に成功します)。</span><span class="sxs-lookup"><span data-stu-id="b70e0-133">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b70e0-134">サービスでは、要素を使用して起動時のパフォーマンスを向上させることをお勧めし `<generatePublisherEvidence>` ます。</span><span class="sxs-lookup"><span data-stu-id="b70e0-134">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="b70e0-135">また、この要素を使用すると、タイムアウトを発生させたり、サービスの開始をキャンセルしたりする可能性がある遅延を回避することもできます。</span><span class="sxs-lookup"><span data-stu-id="b70e0-135">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b70e0-136">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="b70e0-136">Configuration File</span></span>  

 <span data-ttu-id="b70e0-137">この要素は、アプリケーション構成ファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b70e0-137">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b70e0-138">例</span><span class="sxs-lookup"><span data-stu-id="b70e0-138">Example</span></span>  

 <span data-ttu-id="b70e0-139">次の例は、要素を使用して、 `<generatePublisherEvidence>` アプリケーションの CAS 発行者ポリシーのチェックを無効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b70e0-139">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b70e0-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="b70e0-140">See also</span></span>

- [<span data-ttu-id="b70e0-141">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="b70e0-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b70e0-142">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="b70e0-142">Configuration File Schema</span></span>](../index.md)
