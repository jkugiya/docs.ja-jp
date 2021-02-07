---
description: '詳細情報: <oidEntry> 要素'
title: <oidEntry> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: d5fe22018377e247ffa0b6addb58cbeee7119e66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698753"
---
# <a name="oidentry-element"></a><span data-ttu-id="865ca-103">\<oidEntry> 要素</span><span class="sxs-lookup"><span data-stu-id="865ca-103">\<oidEntry> Element</span></span>

<span data-ttu-id="865ca-104">ASN.1 オブジェクト識別子 (OID) を表示名にマップします。</span><span class="sxs-lookup"><span data-stu-id="865ca-104">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="865ca-105">構文</span><span class="sxs-lookup"><span data-stu-id="865ca-105">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="865ca-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="865ca-106">Attributes and Elements</span></span>  

 <span data-ttu-id="865ca-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="865ca-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="865ca-108">属性</span><span class="sxs-lookup"><span data-stu-id="865ca-108">Attributes</span></span>  
  
|<span data-ttu-id="865ca-109">属性</span><span class="sxs-lookup"><span data-stu-id="865ca-109">Attribute</span></span>|<span data-ttu-id="865ca-110">説明</span><span class="sxs-lookup"><span data-stu-id="865ca-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="865ca-111">**OID**</span><span class="sxs-lookup"><span data-stu-id="865ca-111">**OID**</span></span>|<span data-ttu-id="865ca-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="865ca-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="865ca-113">クラスによって実装されたアルゴリズムに対応する asn.1 OID を指定します。</span><span class="sxs-lookup"><span data-stu-id="865ca-113">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="865ca-114">**name**</span><span class="sxs-lookup"><span data-stu-id="865ca-114">**name**</span></span>|<span data-ttu-id="865ca-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="865ca-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="865ca-116">タグの **name** 属性の値を指定し [\<nameEntry>](nameentry-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="865ca-116">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="865ca-117">子要素</span><span class="sxs-lookup"><span data-stu-id="865ca-117">Child Elements</span></span>  

 <span data-ttu-id="865ca-118">なし。</span><span class="sxs-lookup"><span data-stu-id="865ca-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="865ca-119">親要素</span><span class="sxs-lookup"><span data-stu-id="865ca-119">Parent Elements</span></span>  
  
|<span data-ttu-id="865ca-120">要素</span><span class="sxs-lookup"><span data-stu-id="865ca-120">Element</span></span>|<span data-ttu-id="865ca-121">説明</span><span class="sxs-lookup"><span data-stu-id="865ca-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="865ca-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="865ca-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="865ca-123">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="865ca-123">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="865ca-124">要素が含まれてい `cryptographySettings` ます。</span><span class="sxs-lookup"><span data-stu-id="865ca-124">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="865ca-125">クラスに対する asn.1 オブジェクト識別子 (OID) マッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="865ca-125">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="865ca-126">解説</span><span class="sxs-lookup"><span data-stu-id="865ca-126">Remarks</span></span>  

 <span data-ttu-id="865ca-127">Asn.1 オブジェクト識別子は、一部の暗号化形式でアルゴリズムを識別します。</span><span class="sxs-lookup"><span data-stu-id="865ca-127">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="865ca-128">オブジェクト識別子を、識別するアルゴリズムのフレンドリ名にマップします。</span><span class="sxs-lookup"><span data-stu-id="865ca-128">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="865ca-129">例</span><span class="sxs-lookup"><span data-stu-id="865ca-129">Example</span></span>  

 <span data-ttu-id="865ca-130">次の例では、要素を使用して、 **\<oidEntry>** 160 RIPEMD ハッシュアルゴリズムのオブジェクト識別子をそのハッシュアルゴリズムの実装にマップする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="865ca-130">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="865ca-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="865ca-131">See also</span></span>

- [<span data-ttu-id="865ca-132">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="865ca-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="865ca-133">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="865ca-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="865ca-134">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="865ca-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="865ca-135">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="865ca-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="865ca-136">暗号化アルゴリズムへのオブジェクト ID の割り当て</span><span class="sxs-lookup"><span data-stu-id="865ca-136">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
