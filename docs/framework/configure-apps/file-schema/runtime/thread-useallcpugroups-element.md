---
description: '詳細については、次を参照してください: <Thread_UseAllCpuGroups> 要素'
title: <Thread_UseAllCpuGroups> 要素
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: 3f11ba6855caab25bd261de71c80c78232f2690f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802412"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="e4773-103">\<Thread_UseAllCpuGroups> 要素</span><span class="sxs-lookup"><span data-stu-id="e4773-103">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="e4773-104">ランタイムによって、すべての CPU グループにマネージド スレッドを分散するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4773-104">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="e4773-105">構文</span><span class="sxs-lookup"><span data-stu-id="e4773-105">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4773-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e4773-106">Attributes and Elements</span></span>

<span data-ttu-id="e4773-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4773-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4773-108">属性</span><span class="sxs-lookup"><span data-stu-id="e4773-108">Attributes</span></span>

|<span data-ttu-id="e4773-109">属性</span><span class="sxs-lookup"><span data-stu-id="e4773-109">Attribute</span></span>|<span data-ttu-id="e4773-110">説明</span><span class="sxs-lookup"><span data-stu-id="e4773-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e4773-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="e4773-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="e4773-112">ランタイムによって、すべての CPU グループにマネージド スレッドを分散するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4773-112">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="e4773-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="e4773-113">enabled Attribute</span></span>

|<span data-ttu-id="e4773-114">値</span><span class="sxs-lookup"><span data-stu-id="e4773-114">Value</span></span>|<span data-ttu-id="e4773-115">説明</span><span class="sxs-lookup"><span data-stu-id="e4773-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="e4773-116">ランタイムは、複数の CPU グループにマネージド スレッドを分散しません。</span><span class="sxs-lookup"><span data-stu-id="e4773-116">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="e4773-117">既定値です。</span><span class="sxs-lookup"><span data-stu-id="e4773-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="e4773-118">コンピューターに複数の CPU グループがあり、 [\<GCCpuGroup>](gccpugroup-element.md) 要素が有効になっている場合、ランタイムは複数の cpu グループにマネージスレッドを分散します。</span><span class="sxs-lookup"><span data-stu-id="e4773-118">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e4773-119">子要素</span><span class="sxs-lookup"><span data-stu-id="e4773-119">Child Elements</span></span>

<span data-ttu-id="e4773-120">なし。</span><span class="sxs-lookup"><span data-stu-id="e4773-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e4773-121">親要素</span><span class="sxs-lookup"><span data-stu-id="e4773-121">Parent Elements</span></span>

|<span data-ttu-id="e4773-122">要素</span><span class="sxs-lookup"><span data-stu-id="e4773-122">Element</span></span>|<span data-ttu-id="e4773-123">説明</span><span class="sxs-lookup"><span data-stu-id="e4773-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e4773-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="e4773-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e4773-125">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e4773-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4773-126">解説</span><span class="sxs-lookup"><span data-stu-id="e4773-126">Remarks</span></span>

<span data-ttu-id="e4773-127">コンピューターに複数の CPU グループがある場合、この要素を有効にすると、ランタイムは、すべての CPU グループにマネージド スレッドを分散します。</span><span class="sxs-lookup"><span data-stu-id="e4773-127">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="e4773-128">この機能を使用するには、要素を有効にする必要もあります。これにより、 [\<GCCpuGroup>](gccpugroup-element.md) ガベージコレクションがすべての CPU グループに拡張され、ヒープを作成および分散するときにすべてのコアが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="e4773-128">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="e4773-129">要素を有効にする [\<GCCpuGroup>](gccpugroup-element.md) には、要素を有効にする必要があり [\<gcServer>](gcserver-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="e4773-129">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="e4773-130">これらの要素が有効でない場合、`<Thread_UseAllCpuGroups>` 要素を有効にしても効力はありません。</span><span class="sxs-lookup"><span data-stu-id="e4773-130">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="e4773-131">例</span><span class="sxs-lookup"><span data-stu-id="e4773-131">Example</span></span>

<span data-ttu-id="e4773-132">次の例は、複数の CPU グループのサポートを有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e4773-132">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e4773-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4773-133">See also</span></span>

- [<span data-ttu-id="e4773-134">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="e4773-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e4773-135">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="e4773-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e4773-136">\<GCCpuGroup> 要素</span><span class="sxs-lookup"><span data-stu-id="e4773-136">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
