---
description: '詳細情報: <oidMap> 要素'
title: <oidMap> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: 9a71cc54546f49fcada90a0f9915d44d1fc65e89
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729993"
---
# <a name="oidmap-element"></a><span data-ttu-id="891a2-103">\<oidMap> 要素</span><span class="sxs-lookup"><span data-stu-id="891a2-103">\<oidMap> Element</span></span>

<span data-ttu-id="891a2-104">クラスに対する asn.1 オブジェクト識別子 (OID) マッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="891a2-104">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="891a2-105">構文</span><span class="sxs-lookup"><span data-stu-id="891a2-105">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="891a2-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="891a2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="891a2-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="891a2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="891a2-108">属性</span><span class="sxs-lookup"><span data-stu-id="891a2-108">Attributes</span></span>  

 <span data-ttu-id="891a2-109">なし。</span><span class="sxs-lookup"><span data-stu-id="891a2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="891a2-110">子要素</span><span class="sxs-lookup"><span data-stu-id="891a2-110">Child Elements</span></span>  
  
|<span data-ttu-id="891a2-111">要素</span><span class="sxs-lookup"><span data-stu-id="891a2-111">Element</span></span>|<span data-ttu-id="891a2-112">説明</span><span class="sxs-lookup"><span data-stu-id="891a2-112">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="891a2-113">Asn.1 OID をフレンドリ名にマップします。</span><span class="sxs-lookup"><span data-stu-id="891a2-113">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="891a2-114">親要素</span><span class="sxs-lookup"><span data-stu-id="891a2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="891a2-115">要素</span><span class="sxs-lookup"><span data-stu-id="891a2-115">Element</span></span>|<span data-ttu-id="891a2-116">説明</span><span class="sxs-lookup"><span data-stu-id="891a2-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="891a2-117">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="891a2-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="891a2-118">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="891a2-118">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="891a2-119">要素が含まれてい `cryptographySettings` ます。</span><span class="sxs-lookup"><span data-stu-id="891a2-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="891a2-120">例</span><span class="sxs-lookup"><span data-stu-id="891a2-120">Example</span></span>  

 <span data-ttu-id="891a2-121">次の例は、要素を使用して、 **\<oidMap>** RIPEMD-160 ハッシュアルゴリズムの OID とそのハッシュアルゴリズムの実装とのマッピングを格納する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="891a2-121">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="891a2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="891a2-122">See also</span></span>

- [<span data-ttu-id="891a2-123">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="891a2-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="891a2-124">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="891a2-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="891a2-125">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="891a2-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="891a2-126">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="891a2-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="891a2-127">暗号化アルゴリズムへのオブジェクト ID の割り当て</span><span class="sxs-lookup"><span data-stu-id="891a2-127">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
