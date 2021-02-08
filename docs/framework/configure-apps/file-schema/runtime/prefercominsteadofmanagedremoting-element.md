---
description: '詳細情報: <PreferComInsteadOfManagedRemoting> 要素'
title: <PreferComInsteadOfManagedRemoting> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: b621af9b584d1ea2623ffe5a44f74b5b7bd520e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782274"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="50e4c-103">\<PreferComInsteadOfManagedRemoting> 要素</span><span class="sxs-lookup"><span data-stu-id="50e4c-103">\<PreferComInsteadOfManagedRemoting> Element</span></span>

<span data-ttu-id="50e4c-104">アプリケーションドメインの境界を越えたすべての呼び出しに対して、ランタイムがリモート処理の代わりに COM 相互運用を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="50e4c-104">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="50e4c-105">構文</span><span class="sxs-lookup"><span data-stu-id="50e4c-105">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50e4c-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="50e4c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="50e4c-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="50e4c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50e4c-108">属性</span><span class="sxs-lookup"><span data-stu-id="50e4c-108">Attributes</span></span>  
  
|<span data-ttu-id="50e4c-109">属性</span><span class="sxs-lookup"><span data-stu-id="50e4c-109">Attribute</span></span>|<span data-ttu-id="50e4c-110">説明</span><span class="sxs-lookup"><span data-stu-id="50e4c-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="50e4c-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="50e4c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="50e4c-112">アプリケーションドメインの境界を越えて、ランタイムがリモート処理ではなく COM 相互運用を使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="50e4c-112">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="50e4c-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="50e4c-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="50e4c-114">値</span><span class="sxs-lookup"><span data-stu-id="50e4c-114">Value</span></span>|<span data-ttu-id="50e4c-115">説明</span><span class="sxs-lookup"><span data-stu-id="50e4c-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="50e4c-116">ランタイムは、アプリケーションドメインの境界を越えてリモート処理を使用します。</span><span class="sxs-lookup"><span data-stu-id="50e4c-116">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="50e4c-117">既定値です。</span><span class="sxs-lookup"><span data-stu-id="50e4c-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="50e4c-118">ランタイムは、アプリケーションドメインの境界を越えて COM 相互運用を使用します。</span><span class="sxs-lookup"><span data-stu-id="50e4c-118">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50e4c-119">子要素</span><span class="sxs-lookup"><span data-stu-id="50e4c-119">Child Elements</span></span>  

 <span data-ttu-id="50e4c-120">なし。</span><span class="sxs-lookup"><span data-stu-id="50e4c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50e4c-121">親要素</span><span class="sxs-lookup"><span data-stu-id="50e4c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="50e4c-122">要素</span><span class="sxs-lookup"><span data-stu-id="50e4c-122">Element</span></span>|<span data-ttu-id="50e4c-123">説明</span><span class="sxs-lookup"><span data-stu-id="50e4c-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="50e4c-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="50e4c-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="50e4c-125">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="50e4c-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e4c-126">解説</span><span class="sxs-lookup"><span data-stu-id="50e4c-126">Remarks</span></span>  

 <span data-ttu-id="50e4c-127">属性をに設定すると `enabled` `true` 、ランタイムは次のように動作します。</span><span class="sxs-lookup"><span data-stu-id="50e4c-127">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="50e4c-128">[Iunknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)インターフェイスが COM インターフェイス経由でドメインに入るとき、ランタイムは[Imanagedobject](../../../unmanaged-api/hosting/imanagedobject-interface.md)インターフェイスに対して[iunknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))を呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="50e4c-128">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="50e4c-129">代わりに、オブジェクトをラップする [ランタイム呼び出し可能ラッパー](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) を構築します。</span><span class="sxs-lookup"><span data-stu-id="50e4c-129">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="50e4c-130">ランタイムは、 `QueryInterface` このドメインで作成されたすべての[COM 呼び出し可能ラッパー](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) に対して[imanagedobject](../../../unmanaged-api/hosting/imanagedobject-interface.md)インターフェイスの呼び出しを受信したときに、E_NOINTERFACE を返します。</span><span class="sxs-lookup"><span data-stu-id="50e4c-130">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="50e4c-131">これらの2つの動作により、アプリケーションドメインの境界を越えたマネージオブジェクト間の COM インターフェイス経由のすべての呼び出しで、リモート処理ではなく COM と COM の相互運用が使用されるようになります。</span><span class="sxs-lookup"><span data-stu-id="50e4c-131">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50e4c-132">例</span><span class="sxs-lookup"><span data-stu-id="50e4c-132">Example</span></span>  

 <span data-ttu-id="50e4c-133">次の例では、ランタイムが分離の境界を越えて COM 相互運用機能を使用するように指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="50e4c-133">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="50e4c-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="50e4c-134">See also</span></span>

- [<span data-ttu-id="50e4c-135">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="50e4c-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="50e4c-136">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="50e4c-136">Configuration File Schema</span></span>](../index.md)
