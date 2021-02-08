---
description: '詳細情報: <EnableAmPmParseAdjustment> 要素'
title: <EnableAmPmParseAdjustment> 要素
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 86fd04ab536f44f0cffdb5a37f4718fc03698485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787059"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="81fc0-103">\<EnableAmPmParseAdjustment> 要素</span><span class="sxs-lookup"><span data-stu-id="81fc0-103">\<EnableAmPmParseAdjustment> Element</span></span>

<span data-ttu-id="81fc0-104">日付と時刻の解析メソッドが、日、月、時、および午前/午後の指定子を含む日付文字列を解析するために調整されたルールセットを使用するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="81fc0-104">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="81fc0-105">構文</span><span class="sxs-lookup"><span data-stu-id="81fc0-105">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81fc0-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="81fc0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="81fc0-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="81fc0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81fc0-108">属性</span><span class="sxs-lookup"><span data-stu-id="81fc0-108">Attributes</span></span>  
  
|<span data-ttu-id="81fc0-109">属性</span><span class="sxs-lookup"><span data-stu-id="81fc0-109">Attribute</span></span>|<span data-ttu-id="81fc0-110">説明</span><span class="sxs-lookup"><span data-stu-id="81fc0-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="81fc0-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="81fc0-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="81fc0-112">日付と時刻の解析メソッドが、日、月、時、および午前/午後の指定子のみを含む日付文字列を解析するために調整されたルールセットを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="81fc0-112">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="81fc0-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="81fc0-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="81fc0-114">値</span><span class="sxs-lookup"><span data-stu-id="81fc0-114">Value</span></span>|<span data-ttu-id="81fc0-115">説明</span><span class="sxs-lookup"><span data-stu-id="81fc0-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81fc0-116">0</span><span class="sxs-lookup"><span data-stu-id="81fc0-116">0</span></span>|<span data-ttu-id="81fc0-117">日付と時刻の解析メソッドでは、日、月、時、および AM/PM 指定子のみを含む日付文字列を解析するために調整された規則は使用されません。</span><span class="sxs-lookup"><span data-stu-id="81fc0-117">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="81fc0-118">1</span><span class="sxs-lookup"><span data-stu-id="81fc0-118">1</span></span>|<span data-ttu-id="81fc0-119">日付と時刻の解析メソッドでは、日、月、時、および AM/PM 指定子のみを含む日付文字列を解析するための調整された規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="81fc0-119">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81fc0-120">子要素</span><span class="sxs-lookup"><span data-stu-id="81fc0-120">Child Elements</span></span>  

 <span data-ttu-id="81fc0-121">なし。</span><span class="sxs-lookup"><span data-stu-id="81fc0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81fc0-122">親要素</span><span class="sxs-lookup"><span data-stu-id="81fc0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="81fc0-123">要素</span><span class="sxs-lookup"><span data-stu-id="81fc0-123">Element</span></span>|<span data-ttu-id="81fc0-124">説明</span><span class="sxs-lookup"><span data-stu-id="81fc0-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="81fc0-125">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="81fc0-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="81fc0-126">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="81fc0-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81fc0-127">解説</span><span class="sxs-lookup"><span data-stu-id="81fc0-127">Remarks</span></span>  

 <span data-ttu-id="81fc0-128">要素は、 `<EnableAmPmParseAdjustment>` 次のメソッドが日付文字列を解析する方法を制御します。これには、数字と月の後に1時間と AM/PM 指定子 ("4/10 6 am" など) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="81fc0-128">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="81fc0-129">その他のパターンは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="81fc0-129">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="81fc0-130">`<EnableAmPmParseAdjustment>`要素は <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 、、、 <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> 、およびの各 <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> メソッドには影響しません <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="81fc0-130">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="81fc0-131">.NET Core と .NET Native では、調整された AM/PM 解析規則は既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="81fc0-131">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="81fc0-132">解析調整規則が有効になっていない場合、文字列の最初の桁は12時間形式の時刻として解釈され、AM/PM 指定子を除く文字列の残りの部分は無視されます。</span><span class="sxs-lookup"><span data-stu-id="81fc0-132">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="81fc0-133">解析メソッドによって返される日付と時刻は、現在の日付と、日付文字列から抽出された日の時刻で構成されます。</span><span class="sxs-lookup"><span data-stu-id="81fc0-133">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="81fc0-134">解析の調整規則が有効になっている場合、解析メソッドは、日付と月を現在の年に属するものとして解釈し、時刻を12時間形式の時間として解釈します。</span><span class="sxs-lookup"><span data-stu-id="81fc0-134">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="81fc0-135">次の表は、 <xref:System.DateTime> メソッドを使用して、 <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> `<EnableAmPmParseAdjustment>` 要素の `enabled` プロパティが "0" または "1" に設定された文字列 "" 4/10 6 AM "を解析する場合の値の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="81fc0-135">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="81fc0-136">今日の日付が2017年1月5日であると想定し、指定したカルチャの "G" 書式設定文字列を使用して書式設定されているかのように日付を表示します。</span><span class="sxs-lookup"><span data-stu-id="81fc0-136">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="81fc0-137">カルチャ名</span><span class="sxs-lookup"><span data-stu-id="81fc0-137">Culture name</span></span>|<span data-ttu-id="81fc0-138">enabled = "0"</span><span class="sxs-lookup"><span data-stu-id="81fc0-138">enabled="0"</span></span>|<span data-ttu-id="81fc0-139">enabled = "1"</span><span class="sxs-lookup"><span data-stu-id="81fc0-139">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="81fc0-140">en-US</span><span class="sxs-lookup"><span data-stu-id="81fc0-140">en-US</span></span>|<span data-ttu-id="81fc0-141">1/5/2017 4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="81fc0-141">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="81fc0-142">4/10/2017 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="81fc0-142">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="81fc0-143">en-GB</span><span class="sxs-lookup"><span data-stu-id="81fc0-143">en-GB</span></span>|<span data-ttu-id="81fc0-144">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="81fc0-144">5/1/2017 6:00:00</span></span>|<span data-ttu-id="81fc0-145">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="81fc0-145">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81fc0-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="81fc0-146">See also</span></span>

- [<span data-ttu-id="81fc0-147">\<runtime> 要素</span><span class="sxs-lookup"><span data-stu-id="81fc0-147">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="81fc0-148">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="81fc0-148">\<configuration> Element</span></span>](../configuration-element.md)
