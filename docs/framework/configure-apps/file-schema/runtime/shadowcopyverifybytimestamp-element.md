---
description: '詳細情報: <shadowCopyVerifyByTimestamp> 要素'
title: <shadowCopyVerifyByTimestamp> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 273bf4c5b01b300cfd564de4ee29c402c6f3e7ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740094"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="c9ac3-103">\<shadowCopyVerifyByTimestamp> 要素</span><span class="sxs-lookup"><span data-stu-id="c9ac3-103">\<shadowCopyVerifyByTimestamp> Element</span></span>

<span data-ttu-id="c9ac3-104">シャドウコピーで .NET Framework 4 で導入された既定の起動動作を使用するか、以前のバージョンの .NET Framework の起動動作に戻すかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-104">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="c9ac3-105">構文</span><span class="sxs-lookup"><span data-stu-id="c9ac3-105">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9ac3-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c9ac3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c9ac3-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9ac3-108">属性</span><span class="sxs-lookup"><span data-stu-id="c9ac3-108">Attributes</span></span>  
  
|<span data-ttu-id="c9ac3-109">属性</span><span class="sxs-lookup"><span data-stu-id="c9ac3-109">Attribute</span></span>|<span data-ttu-id="c9ac3-110">説明</span><span class="sxs-lookup"><span data-stu-id="c9ac3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9ac3-111">enabled</span><span class="sxs-lookup"><span data-stu-id="c9ac3-111">enabled</span></span>|<span data-ttu-id="c9ac3-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9ac3-113">シャドウコピーを使用するアプリケーションドメインが起動時にアセンブリのタイムスタンプを比較するかどうかを指定し、アセンブリをシャドウコピーする前に更新したかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-113">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c9ac3-114">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="c9ac3-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="c9ac3-115">値</span><span class="sxs-lookup"><span data-stu-id="c9ac3-115">Value</span></span>|<span data-ttu-id="c9ac3-116">説明</span><span class="sxs-lookup"><span data-stu-id="c9ac3-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9ac3-117">true</span><span class="sxs-lookup"><span data-stu-id="c9ac3-117">true</span></span>|<span data-ttu-id="c9ac3-118">起動時に、はシャドウコピーディレクトリに最後にコピーされてから更新されたアセンブリのみをコピーします。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-118">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="c9ac3-119">これは .NET Framework 4 の既定値です。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-119">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="c9ac3-120">false</span><span class="sxs-lookup"><span data-stu-id="c9ac3-120">false</span></span>|<span data-ttu-id="c9ac3-121">以前のバージョンの .NET Framework の起動動作に戻ります。これは、起動時にすべてのファイルをコピーすることでした。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-121">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9ac3-122">子要素</span><span class="sxs-lookup"><span data-stu-id="c9ac3-122">Child Elements</span></span>  

 <span data-ttu-id="c9ac3-123">なし。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9ac3-124">親要素</span><span class="sxs-lookup"><span data-stu-id="c9ac3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c9ac3-125">要素</span><span class="sxs-lookup"><span data-stu-id="c9ac3-125">Element</span></span>|<span data-ttu-id="c9ac3-126">説明</span><span class="sxs-lookup"><span data-stu-id="c9ac3-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c9ac3-127">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c9ac3-128">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9ac3-129">解説</span><span class="sxs-lookup"><span data-stu-id="c9ac3-129">Remarks</span></span>  

 <span data-ttu-id="c9ac3-130">.NET Framework 4 以降、アセンブリはシャドウコピーディレクトリに最後にコピーされてから変更されたことを示すタイムスタンプがある場合にのみ、シャドウコピーされます。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-130">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="c9ac3-131">これにより、「 [アセンブリのシャドウコピー](../../../app-domains/shadow-copy-assemblies.md)」で説明されているように、シャドウコピーを使用する多くのアプリケーションの起動時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-131">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="c9ac3-132">アセンブリ更新の割合と頻度が高いアプリケーションでは、この動作の変更によるメリットが得られない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-132">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="c9ac3-133">その場合は、この要素を使用して、.NET Framework の以前のバージョンの動作を復元できます。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-133">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9ac3-134">例</span><span class="sxs-lookup"><span data-stu-id="c9ac3-134">Example</span></span>  

 <span data-ttu-id="c9ac3-135">次の例は、.NET Framework 4 でシャドウコピーの既定の起動動作を無効にして、以前のバージョンの .NET Framework の起動動作に戻す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c9ac3-135">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9ac3-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9ac3-136">See also</span></span>

- [<span data-ttu-id="c9ac3-137">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c9ac3-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c9ac3-138">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="c9ac3-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c9ac3-139">アセンブリのシャドウ コピー</span><span class="sxs-lookup"><span data-stu-id="c9ac3-139">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
