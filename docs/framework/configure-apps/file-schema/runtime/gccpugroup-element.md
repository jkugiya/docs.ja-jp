---
description: '詳細情報: <GCCpuGroup> 要素'
title: <GCCpuGroup> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: d4b3aa7084cbc2cb23b273bea95ffaec6e3a74d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786994"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="0dd96-103">\<GCCpuGroup> 要素</span><span class="sxs-lookup"><span data-stu-id="0dd96-103">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="0dd96-104">ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="0dd96-104">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="0dd96-105">構文</span><span class="sxs-lookup"><span data-stu-id="0dd96-105">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0dd96-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0dd96-106">Attributes and Elements</span></span>

<span data-ttu-id="0dd96-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0dd96-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0dd96-108">属性</span><span class="sxs-lookup"><span data-stu-id="0dd96-108">Attributes</span></span>

|<span data-ttu-id="0dd96-109">属性</span><span class="sxs-lookup"><span data-stu-id="0dd96-109">Attribute</span></span>|<span data-ttu-id="0dd96-110">説明</span><span class="sxs-lookup"><span data-stu-id="0dd96-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="0dd96-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="0dd96-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="0dd96-112">ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="0dd96-112">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="0dd96-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="0dd96-113">enabled Attribute</span></span>

|<span data-ttu-id="0dd96-114">値</span><span class="sxs-lookup"><span data-stu-id="0dd96-114">Value</span></span>|<span data-ttu-id="0dd96-115">説明</span><span class="sxs-lookup"><span data-stu-id="0dd96-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="0dd96-116">ガベージ コレクションは複数の CPU グループをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="0dd96-116">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="0dd96-117">既定値です。</span><span class="sxs-lookup"><span data-stu-id="0dd96-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="0dd96-118">ガベージ コレクションは、サーバーのガベージ コレクションが有効な場合に複数の CPU グループをサポートします。</span><span class="sxs-lookup"><span data-stu-id="0dd96-118">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0dd96-119">子要素</span><span class="sxs-lookup"><span data-stu-id="0dd96-119">Child Elements</span></span>

<span data-ttu-id="0dd96-120">なし。</span><span class="sxs-lookup"><span data-stu-id="0dd96-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0dd96-121">親要素</span><span class="sxs-lookup"><span data-stu-id="0dd96-121">Parent Elements</span></span>

|<span data-ttu-id="0dd96-122">要素</span><span class="sxs-lookup"><span data-stu-id="0dd96-122">Element</span></span>|<span data-ttu-id="0dd96-123">説明</span><span class="sxs-lookup"><span data-stu-id="0dd96-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0dd96-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="0dd96-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="0dd96-125">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0dd96-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0dd96-126">解説</span><span class="sxs-lookup"><span data-stu-id="0dd96-126">Remarks</span></span>

<span data-ttu-id="0dd96-127">コンピューターに複数の CPU グループがあり、サーバーのガベージコレクションが有効になっている場合 (要素を参照 [\<gcServer>](gcserver-element.md) )、この要素を有効にすると、すべての cpu グループにわたってガベージコレクションが拡張され、ヒープを作成および分散するときにすべてのコアが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="0dd96-127">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="0dd96-128">この要素は、ガベージ コレクション スレッドにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="0dd96-128">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="0dd96-129">ランタイムがすべての CPU グループにユーザースレッドを分散できるようにするには、要素も有効にする必要があり [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="0dd96-129">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="0dd96-130">例</span><span class="sxs-lookup"><span data-stu-id="0dd96-130">Example</span></span>

<span data-ttu-id="0dd96-131">次の例は、複数の CPU グループのガベージ コレクションを有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0dd96-131">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0dd96-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dd96-132">See also</span></span>

- [<span data-ttu-id="0dd96-133">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="0dd96-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0dd96-134">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="0dd96-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0dd96-135">同時実行ガベージコレクションを無効にする</span><span class="sxs-lookup"><span data-stu-id="0dd96-135">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="0dd96-136">ワークステーションとサーバーのガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="0dd96-136">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
