---
description: '詳細については、次を参照してください: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> 要素'
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: ca4099d3bf812cb25e6a611b9b51b3752b1ad361
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782287"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="db828-103">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> 要素</span><span class="sxs-lookup"><span data-stu-id="db828-103">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="db828-104">ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドで固定量のメモリを使用してハッシュ コードを計算するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="db828-104">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="db828-105">構文</span><span class="sxs-lookup"><span data-stu-id="db828-105">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db828-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="db828-106">Attributes and Elements</span></span>

<span data-ttu-id="db828-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="db828-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="db828-108">属性</span><span class="sxs-lookup"><span data-stu-id="db828-108">Attributes</span></span>

|<span data-ttu-id="db828-109">属性</span><span class="sxs-lookup"><span data-stu-id="db828-109">Attribute</span></span>|<span data-ttu-id="db828-110">説明</span><span class="sxs-lookup"><span data-stu-id="db828-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="db828-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="db828-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="db828-112">ハッシュ コードを計算するときに、共通言語ランタイムが固定メモリを割り当てるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="db828-112">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="db828-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="db828-113">enabled Attribute</span></span>

|<span data-ttu-id="db828-114">値</span><span class="sxs-lookup"><span data-stu-id="db828-114">Value</span></span>|<span data-ttu-id="db828-115">説明</span><span class="sxs-lookup"><span data-stu-id="db828-115">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="db828-116">0</span><span class="sxs-lookup"><span data-stu-id="db828-116">0</span></span>|<span data-ttu-id="db828-117">共通言語ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドに可変メモリを割り当ててハッシュ コードを計算します。</span><span class="sxs-lookup"><span data-stu-id="db828-117">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="db828-118">既定値です。</span><span class="sxs-lookup"><span data-stu-id="db828-118">This is the default.</span></span>|
|<span data-ttu-id="db828-119">1</span><span class="sxs-lookup"><span data-stu-id="db828-119">1</span></span>|<span data-ttu-id="db828-120">共通言語ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドに固定メモリを割り当ててハッシュ コードを計算します。</span><span class="sxs-lookup"><span data-stu-id="db828-120">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="db828-121">子要素</span><span class="sxs-lookup"><span data-stu-id="db828-121">Child Elements</span></span>

<span data-ttu-id="db828-122">なし。</span><span class="sxs-lookup"><span data-stu-id="db828-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="db828-123">親要素</span><span class="sxs-lookup"><span data-stu-id="db828-123">Parent Elements</span></span>

|<span data-ttu-id="db828-124">要素</span><span class="sxs-lookup"><span data-stu-id="db828-124">Element</span></span>|<span data-ttu-id="db828-125">説明</span><span class="sxs-lookup"><span data-stu-id="db828-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="db828-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="db828-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="db828-127">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="db828-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db828-128">解説</span><span class="sxs-lookup"><span data-stu-id="db828-128">Remarks</span></span>

<span data-ttu-id="db828-129">既定では、共通言語ランタイムが <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドに可変メモリを割り当て、メソッドが非常に長い文字列 (数メガバイト以上) のハッシュ コードを計算しようとすると <xref:System.ArgumentException> 例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="db828-129">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="db828-130">この要素をアプリケーション構成ファイルに追加し、 `enabled` 属性を 1 に設定すると、 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> メソッドでハッシュ コードの計算時に固定メモリを割り当てる別のアルゴリズムを使用することを指定できます。</span><span class="sxs-lookup"><span data-stu-id="db828-130">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db828-131">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`要素は、Windows 8 以降のバージョンでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="db828-131">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="db828-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="db828-132">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="db828-133">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="db828-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="db828-134">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="db828-134">Configuration File Schema</span></span>](../index.md)
