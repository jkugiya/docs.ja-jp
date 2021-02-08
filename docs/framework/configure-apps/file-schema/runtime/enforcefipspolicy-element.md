---
description: '詳細情報: <enforceFIPSPolicy> 要素'
title: <enforceFIPSPolicy> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: d445570db634867a15b6d97d4e20186bd0641c2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787072"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="b560e-103">\<enforceFIPSPolicy> 要素</span><span class="sxs-lookup"><span data-stu-id="b560e-103">\<enforceFIPSPolicy> Element</span></span>

<span data-ttu-id="b560e-104">暗号化アルゴリズムが連邦情報処理規格 (FIPS: Federal Information Processing Standard) に準拠する必要があるコンピューターの構成要件を強制するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b560e-104">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="b560e-105">構文</span><span class="sxs-lookup"><span data-stu-id="b560e-105">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b560e-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b560e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b560e-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b560e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b560e-108">属性</span><span class="sxs-lookup"><span data-stu-id="b560e-108">Attributes</span></span>  
  
|<span data-ttu-id="b560e-109">属性</span><span class="sxs-lookup"><span data-stu-id="b560e-109">Attribute</span></span>|<span data-ttu-id="b560e-110">説明</span><span class="sxs-lookup"><span data-stu-id="b560e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b560e-111">enabled</span><span class="sxs-lookup"><span data-stu-id="b560e-111">enabled</span></span>|<span data-ttu-id="b560e-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="b560e-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="b560e-113">暗号化アルゴリズムが FIPS に準拠している必要があるコンピューター構成要件の適用を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b560e-113">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b560e-114">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="b560e-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="b560e-115">値</span><span class="sxs-lookup"><span data-stu-id="b560e-115">Value</span></span>|<span data-ttu-id="b560e-116">説明</span><span class="sxs-lookup"><span data-stu-id="b560e-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="b560e-117">暗号化アルゴリズムが FIPS に準拠するようにコンピューターが構成されている場合は、その要件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b560e-117">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="b560e-118">クラスが FIPS に準拠していないアルゴリズムを実装している場合、そのクラスのコンストラクターまたはメソッドは、その `Create` コンピューターで実行されるときに例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b560e-118">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="b560e-119">既定値です。</span><span class="sxs-lookup"><span data-stu-id="b560e-119">This is the default.</span></span>|  
|`false`|<span data-ttu-id="b560e-120">アプリケーションで使用される暗号化アルゴリズムは、コンピューターの構成に関係なく、FIPS に準拠している必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b560e-120">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b560e-121">子要素</span><span class="sxs-lookup"><span data-stu-id="b560e-121">Child Elements</span></span>  

 <span data-ttu-id="b560e-122">なし。</span><span class="sxs-lookup"><span data-stu-id="b560e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b560e-123">親要素</span><span class="sxs-lookup"><span data-stu-id="b560e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b560e-124">要素</span><span class="sxs-lookup"><span data-stu-id="b560e-124">Element</span></span>|<span data-ttu-id="b560e-125">説明</span><span class="sxs-lookup"><span data-stu-id="b560e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b560e-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="b560e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b560e-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b560e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b560e-128">解説</span><span class="sxs-lookup"><span data-stu-id="b560e-128">Remarks</span></span>  

 <span data-ttu-id="b560e-129">.NET Framework 2.0 以降では、暗号化アルゴリズムを実装するクラスの作成は、コンピューターの構成によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="b560e-129">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="b560e-130">アルゴリズムが FIPS に準拠していることを必要とするようにコンピューターが構成されており、クラスが FIPS に準拠していないアルゴリズムを実装している場合、そのクラスのインスタンスを作成しようとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b560e-130">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="b560e-131">コンストラクターは <xref:System.InvalidOperationException> 例外をスローし、 `Create` メソッドは <xref:System.Reflection.TargetInvocationException> 内部例外を使用して例外をスローし <xref:System.InvalidOperationException> ます。</span><span class="sxs-lookup"><span data-stu-id="b560e-131">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="b560e-132">構成が FIPS に準拠しているコンピューターでアプリケーションを実行していて、アプリケーションが fips に準拠していないアルゴリズムを使用している場合は、構成ファイルでこの要素を使用して、共通言語ランタイム (CLR) が FIPS 準拠を強制しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b560e-132">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="b560e-133">この要素は、.NET Framework 2.0 Service Pack 1 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="b560e-133">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b560e-134">例</span><span class="sxs-lookup"><span data-stu-id="b560e-134">Example</span></span>  

 <span data-ttu-id="b560e-135">次の例は、CLR が FIPS 準拠を強制しないようにする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b560e-135">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b560e-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b560e-136">See also</span></span>

- [<span data-ttu-id="b560e-137">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="b560e-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b560e-138">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="b560e-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b560e-139">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="b560e-139">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
