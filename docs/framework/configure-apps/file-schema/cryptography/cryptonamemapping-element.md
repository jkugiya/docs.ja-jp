---
description: '詳細情報: <cryptoNameMapping> 要素'
title: <cryptoNameMapping> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: b7dac458fdda0aabf36df96b43dca1529ffe4743
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698909"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="b3bdf-103">\<cryptoNameMapping> 要素</span><span class="sxs-lookup"><span data-stu-id="b3bdf-103">\<cryptoNameMapping> Element</span></span>

<span data-ttu-id="b3bdf-104">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-104">Contains mappings of classes to friendly names.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**

## <a name="syntax"></a><span data-ttu-id="b3bdf-105">構文</span><span class="sxs-lookup"><span data-stu-id="b3bdf-105">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3bdf-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b3bdf-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b3bdf-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3bdf-108">属性</span><span class="sxs-lookup"><span data-stu-id="b3bdf-108">Attributes</span></span>  

 <span data-ttu-id="b3bdf-109">なし。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b3bdf-110">子要素</span><span class="sxs-lookup"><span data-stu-id="b3bdf-110">Child Elements</span></span>  
  
|<span data-ttu-id="b3bdf-111">要素</span><span class="sxs-lookup"><span data-stu-id="b3bdf-111">Element</span></span>|<span data-ttu-id="b3bdf-112">説明</span><span class="sxs-lookup"><span data-stu-id="b3bdf-112">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="b3bdf-113">要素内の表示名へのマッピングを持つ暗号化クラスの一覧が含まれてい **\<nameEntry>** ます。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-113">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="b3bdf-114">アルゴリズムの表示名にクラス名をマップして、1 つのクラスが多くの表示名を持つことを許可します。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-114">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3bdf-115">親要素</span><span class="sxs-lookup"><span data-stu-id="b3bdf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b3bdf-116">要素</span><span class="sxs-lookup"><span data-stu-id="b3bdf-116">Element</span></span>|<span data-ttu-id="b3bdf-117">説明</span><span class="sxs-lookup"><span data-stu-id="b3bdf-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b3bdf-118">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="b3bdf-119">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-119">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="b3bdf-120">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-120">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="b3bdf-121">要素が含まれてい \<cryptographySettings> ます。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-121">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3bdf-122">例</span><span class="sxs-lookup"><span data-stu-id="b3bdf-122">Example</span></span>  

 <span data-ttu-id="b3bdf-123">次の例は、要素を使用して **\<cryptoNameMapping>** 暗号化クラスを参照し、ランタイムを構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-123">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="b3bdf-124">その後、文字列 "RSA" をメソッドに渡し <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 、メソッドを使用して <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> オブジェクトを返すことができ `MyCryptoRSAClass` ます。</span><span class="sxs-lookup"><span data-stu-id="b3bdf-124">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3bdf-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3bdf-125">See also</span></span>

- [<span data-ttu-id="b3bdf-126">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="b3bdf-126">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b3bdf-127">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="b3bdf-127">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b3bdf-128">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="b3bdf-128">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="b3bdf-129">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="b3bdf-129">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
