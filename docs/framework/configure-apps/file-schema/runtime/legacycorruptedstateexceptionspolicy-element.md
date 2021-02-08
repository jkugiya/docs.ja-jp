---
description: '詳細情報: <legacyCorruptedStateExceptionsPolicy> 要素'
title: <legacyCorruptedStateExceptionsPolicy> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: 34082c0779b09400a875894359cf7cf501173508
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786955"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="1f6e2-103">\<legacyCorruptedStateExceptionsPolicy> 要素</span><span class="sxs-lookup"><span data-stu-id="1f6e2-103">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>

<span data-ttu-id="1f6e2-104">共通言語ランタイムで、マネージコードがアクセス違反とその他の破損状態例外をキャッチできるようにするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-104">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="1f6e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="1f6e2-105">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f6e2-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1f6e2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1f6e2-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f6e2-108">属性</span><span class="sxs-lookup"><span data-stu-id="1f6e2-108">Attributes</span></span>  
  
|<span data-ttu-id="1f6e2-109">属性</span><span class="sxs-lookup"><span data-stu-id="1f6e2-109">Attribute</span></span>|<span data-ttu-id="1f6e2-110">説明</span><span class="sxs-lookup"><span data-stu-id="1f6e2-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1f6e2-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="1f6e2-112">アプリケーションがアクセス違反などの破損状態の例外エラーをキャッチすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-112">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1f6e2-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="1f6e2-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="1f6e2-114">値</span><span class="sxs-lookup"><span data-stu-id="1f6e2-114">Value</span></span>|<span data-ttu-id="1f6e2-115">説明</span><span class="sxs-lookup"><span data-stu-id="1f6e2-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1f6e2-116">アプリケーションでは、アクセス違反などの破損状態の例外エラーはキャッチされません。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-116">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="1f6e2-117">既定値です。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="1f6e2-118">アプリケーションは、アクセス違反などの破損状態の例外エラーをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-118">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f6e2-119">子要素</span><span class="sxs-lookup"><span data-stu-id="1f6e2-119">Child Elements</span></span>  

 <span data-ttu-id="1f6e2-120">なし。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f6e2-121">親要素</span><span class="sxs-lookup"><span data-stu-id="1f6e2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1f6e2-122">要素</span><span class="sxs-lookup"><span data-stu-id="1f6e2-122">Element</span></span>|<span data-ttu-id="1f6e2-123">説明</span><span class="sxs-lookup"><span data-stu-id="1f6e2-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1f6e2-124">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1f6e2-125">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f6e2-126">解説</span><span class="sxs-lookup"><span data-stu-id="1f6e2-126">Remarks</span></span>  

 <span data-ttu-id="1f6e2-127">.NET Framework バージョン3.5 以前では、共通言語ランタイムは、破損したプロセス状態によって発生した例外をキャッチするために、マネージコードを許可しました。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-127">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="1f6e2-128">この種類の例外の例として、アクセス違反があります。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-128">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="1f6e2-129">.NET Framework 4 以降では、マネージコードはブロック内のこれらの種類の例外をキャッチしなくなりました `catch` 。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-129">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="1f6e2-130">ただし、次の2つの方法で、この変更をオーバーライドし、破損状態例外の処理を維持することができます。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-130">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="1f6e2-131">`<legacyCorruptedStateExceptionsPolicy>`要素の `enabled` 属性をに設定 `true` します。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-131">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="1f6e2-132">この構成設定は、プロセス全体に適用され、すべてのメソッドに影響します。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-132">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="1f6e2-133">\- または -</span><span class="sxs-lookup"><span data-stu-id="1f6e2-133">-or-</span></span>  
  
- <span data-ttu-id="1f6e2-134"><xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>例外ブロックを含むメソッドに属性を適用 `catch` します。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-134">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="1f6e2-135">この構成要素は、.NET Framework 4 以降でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-135">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f6e2-136">例</span><span class="sxs-lookup"><span data-stu-id="1f6e2-136">Example</span></span>  

 <span data-ttu-id="1f6e2-137">次の例では、アプリケーションが .NET Framework 4 より前の動作に戻し、すべての破損状態の例外エラーをキャッチするように指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f6e2-137">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f6e2-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f6e2-138">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="1f6e2-139">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="1f6e2-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1f6e2-140">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="1f6e2-140">Configuration File Schema</span></span>](../index.md)
