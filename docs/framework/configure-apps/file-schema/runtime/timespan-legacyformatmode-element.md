---
description: '詳細については、次を参照してください: <TimeSpan_LegacyFormatMode> 要素'
title: <TimeSpan_LegacyFormatMode> 要素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: 1fa5c3a15941004ebab9e3622d4b3e7b27130e22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802386"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="2d0a9-103">\<TimeSpan_LegacyFormatMode> 要素</span><span class="sxs-lookup"><span data-stu-id="2d0a9-103">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="2d0a9-104">値を使用して、ランタイムが書式設定操作で従来の動作を保持するかどうかを決定し <xref:System.TimeSpan?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-104">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**  

## <a name="syntax"></a><span data-ttu-id="2d0a9-105">構文</span><span class="sxs-lookup"><span data-stu-id="2d0a9-105">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d0a9-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2d0a9-106">Attributes and Elements</span></span>

<span data-ttu-id="2d0a9-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d0a9-108">属性</span><span class="sxs-lookup"><span data-stu-id="2d0a9-108">Attributes</span></span>

|<span data-ttu-id="2d0a9-109">属性</span><span class="sxs-lookup"><span data-stu-id="2d0a9-109">Attribute</span></span>|<span data-ttu-id="2d0a9-110">説明</span><span class="sxs-lookup"><span data-stu-id="2d0a9-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="2d0a9-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="2d0a9-112">ランタイムが従来の書式設定動作を値と共に使用するかどうかを指定し <xref:System.TimeSpan?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-112">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="2d0a9-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="2d0a9-113">enabled Attribute</span></span>

|<span data-ttu-id="2d0a9-114">値</span><span class="sxs-lookup"><span data-stu-id="2d0a9-114">Value</span></span>|<span data-ttu-id="2d0a9-115">説明</span><span class="sxs-lookup"><span data-stu-id="2d0a9-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="2d0a9-116">ランタイムでは、従来の書式設定動作は復元されません。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-116">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="2d0a9-117">ランタイムは、従来の書式設定動作を復元します。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-117">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2d0a9-118">子要素</span><span class="sxs-lookup"><span data-stu-id="2d0a9-118">Child Elements</span></span>

<span data-ttu-id="2d0a9-119">なし。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d0a9-120">親要素</span><span class="sxs-lookup"><span data-stu-id="2d0a9-120">Parent Elements</span></span>

|<span data-ttu-id="2d0a9-121">要素</span><span class="sxs-lookup"><span data-stu-id="2d0a9-121">Element</span></span>|<span data-ttu-id="2d0a9-122">説明</span><span class="sxs-lookup"><span data-stu-id="2d0a9-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2d0a9-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="2d0a9-124">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2d0a9-125">解説</span><span class="sxs-lookup"><span data-stu-id="2d0a9-125">Remarks</span></span>

<span data-ttu-id="2d0a9-126">.NET Framework 4 以降では、 <xref:System.TimeSpan?displayProperty=nameWithType> 構造体はインターフェイスを実装 <xref:System.IFormattable> し、標準およびカスタムの書式指定文字列を使用した書式設定操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-126">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="2d0a9-127">解析メソッドで、サポートされていない書式指定子または書式指定文字列が検出されると、がスローさ <xref:System.FormatException> れます。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-127">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="2d0a9-128">以前のバージョンの .NET Framework では、構造体がを実装しておらず、 <xref:System.TimeSpan> <xref:System.IFormattable> 書式指定文字列をサポートしていませんでした。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-128">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="2d0a9-129">しかし、多くの開発者は、 <xref:System.TimeSpan> 書式指定文字列のセットをサポートし、などのメソッドを使用して [複合書式指定操作](../../../../standard/base-types/composite-formatting.md) で使用したことを誤って想定していました <xref:System.String.Format%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-129">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2d0a9-130">通常、型がを実装 <xref:System.IFormattable> し、書式指定文字列をサポートする場合、サポートされていない書式指定文字列を使用した書式指定メソッドの呼び出しは、通常、をスロー <xref:System.FormatException> します。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-130">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="2d0a9-131">ただし、が <xref:System.TimeSpan> 実装されていないため、 <xref:System.IFormattable> ランタイムは書式指定文字列を無視し、代わりにメソッドを呼び出しました <xref:System.TimeSpan.ToString?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-131">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2d0a9-132">これは、書式指定文字列が書式設定操作に影響を与えないことを意味しますが、その存在はになりませんでした <xref:System.FormatException> 。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-132">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="2d0a9-133">レガシコードによって複合書式指定メソッドと無効な書式指定文字列が渡され、そのコードを再コンパイルできない場合は、要素を使用して `<TimeSpan_LegacyFormatMode>` 従来の動作を復元でき <xref:System.TimeSpan> ます。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-133">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="2d0a9-134">`enabled`この要素の属性をに設定すると、 `true` 複合書式指定メソッドによってではなくが呼び出され、 <xref:System.TimeSpan.ToString?displayProperty=nameWithType> がスローされ <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.FormatException> ません。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-134">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="2d0a9-135">例</span><span class="sxs-lookup"><span data-stu-id="2d0a9-135">Example</span></span>

<span data-ttu-id="2d0a9-136">次の例では、オブジェクトをインスタンス化 <xref:System.TimeSpan> し、 <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> サポートされていない標準書式指定文字列を使用して、メソッドを使用して書式設定を試みます。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-136">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="2d0a9-137">.NET Framework 3.5 またはそれ以前のバージョンでこの例を実行すると、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-137">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```console
12:30:45
```

<span data-ttu-id="2d0a9-138">これは、.NET Framework 4 以降のバージョンで例を実行した場合の出力とは大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-138">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```console
Invalid Format
```

<span data-ttu-id="2d0a9-139">ただし、次の構成ファイルを例のディレクトリに追加した後、.NET Framework 4 以降のバージョンでこの例を実行すると、出力は、.NET Framework 3.5 で実行されたときに例で生成されたものと同じになります。</span><span class="sxs-lookup"><span data-stu-id="2d0a9-139">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2d0a9-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d0a9-140">See also</span></span>

- [<span data-ttu-id="2d0a9-141">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="2d0a9-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2d0a9-142">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="2d0a9-142">Configuration File Schema</span></span>](../index.md)
