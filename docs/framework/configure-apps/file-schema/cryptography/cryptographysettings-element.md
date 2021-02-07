---
description: '詳細情報: <cryptographySettings> 要素'
title: <cryptographySettings> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: afd4fdbc24dfaac60ce24b7a439a8d4d8a9427ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730097"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="f15df-103">\<cryptographySettings> 要素</span><span class="sxs-lookup"><span data-stu-id="f15df-103">\<cryptographySettings> Element</span></span>

<span data-ttu-id="f15df-104">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="f15df-104">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="f15df-105">構文</span><span class="sxs-lookup"><span data-stu-id="f15df-105">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f15df-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f15df-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f15df-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f15df-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f15df-108">属性</span><span class="sxs-lookup"><span data-stu-id="f15df-108">Attributes</span></span>  

 <span data-ttu-id="f15df-109">なし。</span><span class="sxs-lookup"><span data-stu-id="f15df-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f15df-110">子要素</span><span class="sxs-lookup"><span data-stu-id="f15df-110">Child Elements</span></span>  
  
|<span data-ttu-id="f15df-111">要素</span><span class="sxs-lookup"><span data-stu-id="f15df-111">Element</span></span>|<span data-ttu-id="f15df-112">説明</span><span class="sxs-lookup"><span data-stu-id="f15df-112">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="f15df-113">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="f15df-113">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="f15df-114">クラスに対する asn.1 オブジェクト識別子 (OID) マッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f15df-114">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f15df-115">親要素</span><span class="sxs-lookup"><span data-stu-id="f15df-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f15df-116">要素</span><span class="sxs-lookup"><span data-stu-id="f15df-116">Element</span></span>|<span data-ttu-id="f15df-117">説明</span><span class="sxs-lookup"><span data-stu-id="f15df-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f15df-118">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="f15df-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="f15df-119">要素が含まれてい `cryptographySettings` ます。</span><span class="sxs-lookup"><span data-stu-id="f15df-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f15df-120">例</span><span class="sxs-lookup"><span data-stu-id="f15df-120">Example</span></span>  

 <span data-ttu-id="f15df-121">次の例では、要素を使用して、 **\<cryptographySettings>** 暗号化名マッピングと OID マッピングを格納する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f15df-121">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="f15df-122">この例では、がオブジェクトを返すようにランタイムを構成 <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> `MyHashClass` し、クラスを `MyCryptoClass` オブジェクト識別子1.3.36.2.1 にマップします。</span><span class="sxs-lookup"><span data-stu-id="f15df-122">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f15df-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f15df-123">See also</span></span>

- [<span data-ttu-id="f15df-124">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="f15df-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f15df-125">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="f15df-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f15df-126">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="f15df-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
