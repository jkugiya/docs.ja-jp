---
description: '詳細情報: <cryptoClass> 要素'
title: <cryptoClass> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: 503a079ea78a71a11e4c750a629cf67c9244a25d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698937"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="115bf-103">\<cryptoClass> 要素</span><span class="sxs-lookup"><span data-stu-id="115bf-103">\<cryptoClass> Element</span></span>

<span data-ttu-id="115bf-104">要素内のフレンドリ名へのマッピングを持つ暗号化クラスを格納 [\<nameEntry>](nameentry-element.md) します。</span><span class="sxs-lookup"><span data-stu-id="115bf-104">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a><span data-ttu-id="115bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="115bf-105">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="115bf-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="115bf-106">Attributes and Elements</span></span>  

 <span data-ttu-id="115bf-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="115bf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="115bf-108">属性</span><span class="sxs-lookup"><span data-stu-id="115bf-108">Attributes</span></span>  
  
|<span data-ttu-id="115bf-109">属性</span><span class="sxs-lookup"><span data-stu-id="115bf-109">Attribute</span></span>|<span data-ttu-id="115bf-110">説明</span><span class="sxs-lookup"><span data-stu-id="115bf-110">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="115bf-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="115bf-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="115bf-112">暗号化クラスの情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="115bf-112">Contains the information for the cryptography class.</span></span> <span data-ttu-id="115bf-113">この属性を使用して、クラスの短い名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="115bf-113">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="115bf-114">[「完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定した要件を満たす文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="115bf-114">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="115bf-115">子要素</span><span class="sxs-lookup"><span data-stu-id="115bf-115">Child Elements</span></span>  

 <span data-ttu-id="115bf-116">なし。</span><span class="sxs-lookup"><span data-stu-id="115bf-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="115bf-117">親要素</span><span class="sxs-lookup"><span data-stu-id="115bf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="115bf-118">要素</span><span class="sxs-lookup"><span data-stu-id="115bf-118">Element</span></span>|<span data-ttu-id="115bf-119">説明</span><span class="sxs-lookup"><span data-stu-id="115bf-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="115bf-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="115bf-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="115bf-121">要素内の表示名へのマッピングを持つ暗号化クラスの一覧が含まれてい [\<nameEntry>](nameentry-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="115bf-121">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="115bf-122">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="115bf-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="115bf-123">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="115bf-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="115bf-124">要素が含まれてい [\<cryptographySettings>](cryptographysettings-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="115bf-124">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="115bf-125">例</span><span class="sxs-lookup"><span data-stu-id="115bf-125">Example</span></span>  

 <span data-ttu-id="115bf-126">次の例は、要素を使用して暗号化クラスを参照し、ランタイムを構成する方法を示して **\<cryptoClass>** います。</span><span class="sxs-lookup"><span data-stu-id="115bf-126">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="115bf-127">その後、文字列 "RSA" をメソッドに渡し <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 、メソッドを使用して <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> オブジェクトを返すことができ `MyCryptoRSAClass` ます。</span><span class="sxs-lookup"><span data-stu-id="115bf-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="115bf-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="115bf-128">See also</span></span>

- [<span data-ttu-id="115bf-129">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="115bf-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="115bf-130">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="115bf-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="115bf-131">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="115bf-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="115bf-132">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="115bf-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
