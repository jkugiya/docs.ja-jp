---
description: '詳細情報: <nameEntry> 要素'
title: <nameEntry> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 0ca227a2ba17a6b1e67fb75ec91aac9194b54737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730006"
---
# <a name="nameentry-element"></a><span data-ttu-id="49c66-103">\<nameEntry> 要素</span><span class="sxs-lookup"><span data-stu-id="49c66-103">\<nameEntry> Element</span></span>

<span data-ttu-id="49c66-104">アルゴリズムの表示名にクラス名をマップして、1 つのクラスが多くの表示名を持つことを許可します。</span><span class="sxs-lookup"><span data-stu-id="49c66-104">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="49c66-105">構文</span><span class="sxs-lookup"><span data-stu-id="49c66-105">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49c66-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="49c66-106">Attributes and Elements</span></span>  

 <span data-ttu-id="49c66-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="49c66-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49c66-108">属性</span><span class="sxs-lookup"><span data-stu-id="49c66-108">Attributes</span></span>  
  
|<span data-ttu-id="49c66-109">属性</span><span class="sxs-lookup"><span data-stu-id="49c66-109">Attribute</span></span>|<span data-ttu-id="49c66-110">説明</span><span class="sxs-lookup"><span data-stu-id="49c66-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49c66-111">**name**</span><span class="sxs-lookup"><span data-stu-id="49c66-111">**name**</span></span>|<span data-ttu-id="49c66-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="49c66-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="49c66-113">暗号化クラスが実装するアルゴリズムのフレンドリ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="49c66-113">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="49c66-114">**class**</span><span class="sxs-lookup"><span data-stu-id="49c66-114">**class**</span></span>|<span data-ttu-id="49c66-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="49c66-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="49c66-116">要素の **name** 属性の値を指定し [\<cryptoClass>](cryptoclass-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="49c66-116">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49c66-117">子要素</span><span class="sxs-lookup"><span data-stu-id="49c66-117">Child Elements</span></span>  

 <span data-ttu-id="49c66-118">なし。</span><span class="sxs-lookup"><span data-stu-id="49c66-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49c66-119">親要素</span><span class="sxs-lookup"><span data-stu-id="49c66-119">Parent Elements</span></span>  
  
|<span data-ttu-id="49c66-120">要素</span><span class="sxs-lookup"><span data-stu-id="49c66-120">Element</span></span>|<span data-ttu-id="49c66-121">説明</span><span class="sxs-lookup"><span data-stu-id="49c66-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="49c66-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="49c66-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="49c66-123">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="49c66-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49c66-124">解説</span><span class="sxs-lookup"><span data-stu-id="49c66-124">Remarks</span></span>  

 <span data-ttu-id="49c66-125">**Name** 属性には、名前空間で見つかった抽象クラスの1つの名前を指定でき <xref:System.Security.Cryptography> ます。</span><span class="sxs-lookup"><span data-stu-id="49c66-125">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="49c66-126">抽象暗号化クラスで **Create** メソッドを呼び出すと、抽象クラス名がメソッドに渡され <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="49c66-126">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="49c66-127">**CreateFromName** は、 **class** 属性で示される型のインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="49c66-127">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="49c66-128">**Name** 属性が RSA などの短い名前である場合は、 **CreateFromName** メソッドを呼び出すときにその名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="49c66-128">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49c66-129">例</span><span class="sxs-lookup"><span data-stu-id="49c66-129">Example</span></span>  

 <span data-ttu-id="49c66-130">次の例は、要素を使用して **\<nameEntry>** 暗号化クラスを参照し、ランタイムを構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="49c66-130">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="49c66-131">その後、文字列 "RSA" をメソッドに渡し <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 、メソッドを使用して <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> オブジェクトを返すことができ `MyCryptoRSAClass` ます。</span><span class="sxs-lookup"><span data-stu-id="49c66-131">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="49c66-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="49c66-132">See also</span></span>

- [<span data-ttu-id="49c66-133">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="49c66-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="49c66-134">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="49c66-134">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="49c66-135">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="49c66-135">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="49c66-136">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="49c66-136">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
