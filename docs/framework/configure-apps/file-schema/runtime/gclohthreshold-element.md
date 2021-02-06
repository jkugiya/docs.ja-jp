---
description: '詳細情報: GCLOHThreshold 要素'
title: GCLOHThreshold 要素
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: 5d4ef4e6aaf44642c2307dc27ac2e99e966d3ad0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652810"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="03057-103">GCLOHThreshold 要素</span><span class="sxs-lookup"><span data-stu-id="03057-103">GCLOHThreshold element</span></span>

<span data-ttu-id="03057-104">ガベージコレクターがラージオブジェクトヒープ (LOH) にオブジェクトを配置するしきい値のサイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="03057-104">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="03057-105">構文</span><span class="sxs-lookup"><span data-stu-id="03057-105">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="03057-106">属性</span><span class="sxs-lookup"><span data-stu-id="03057-106">Attributes</span></span>

|<span data-ttu-id="03057-107">属性</span><span class="sxs-lookup"><span data-stu-id="03057-107">Attribute</span></span>|<span data-ttu-id="03057-108">説明</span><span class="sxs-lookup"><span data-stu-id="03057-108">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="03057-109">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="03057-109">Required attribute.</span></span><br /><br /><span data-ttu-id="03057-110">オブジェクトが大きなオブジェクトヒープに対して実行されるしきい値のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="03057-110">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="03057-111">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="03057-111">enabled attribute</span></span>

|<span data-ttu-id="03057-112">値</span><span class="sxs-lookup"><span data-stu-id="03057-112">Value</span></span>|<span data-ttu-id="03057-113">説明</span><span class="sxs-lookup"><span data-stu-id="03057-113">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="03057-114">オブジェクトが大きなオブジェクトヒープに対して実行されるしきい値のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="03057-114">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="03057-115">子要素</span><span class="sxs-lookup"><span data-stu-id="03057-115">Child elements</span></span>

<span data-ttu-id="03057-116">なし。</span><span class="sxs-lookup"><span data-stu-id="03057-116">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="03057-117">親要素</span><span class="sxs-lookup"><span data-stu-id="03057-117">Parent elements</span></span>

|<span data-ttu-id="03057-118">要素</span><span class="sxs-lookup"><span data-stu-id="03057-118">Element</span></span>|<span data-ttu-id="03057-119">説明</span><span class="sxs-lookup"><span data-stu-id="03057-119">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="03057-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="03057-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="03057-121">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="03057-121">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="03057-122">解説</span><span class="sxs-lookup"><span data-stu-id="03057-122">Remarks</span></span>

<span data-ttu-id="03057-123">この設定は .NET Framework 4.8 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="03057-123">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="03057-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="03057-124">See also</span></span>

- [<span data-ttu-id="03057-125">実行時設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="03057-125">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="03057-126">構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="03057-126">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="03057-127">ガベージ コレクションの基礎</span><span class="sxs-lookup"><span data-stu-id="03057-127">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="03057-128">GC の NET Core ランタイム構成オプション</span><span class="sxs-lookup"><span data-stu-id="03057-128">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
