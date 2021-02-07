---
description: '詳細情報: <configSections> の要素 <configuration>'
title: <configuration> の <configSections> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 543ceed8d53fd299e8a0b65594592b64d6b833a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698988"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="368d4-103">\<configuration> の \<configSections> 要素</span><span class="sxs-lookup"><span data-stu-id="368d4-103">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="368d4-104">構成セクションと名前空間の宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="368d4-104">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="368d4-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="368d4-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="368d4-106">属性</span><span class="sxs-lookup"><span data-stu-id="368d4-106">Attributes</span></span>

<span data-ttu-id="368d4-107">なし</span><span class="sxs-lookup"><span data-stu-id="368d4-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="368d4-108">親要素</span><span class="sxs-lookup"><span data-stu-id="368d4-108">Parent element</span></span>

|     | <span data-ttu-id="368d4-109">説明</span><span class="sxs-lookup"><span data-stu-id="368d4-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="368d4-110">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="368d4-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="368d4-111">子要素</span><span class="sxs-lookup"><span data-stu-id="368d4-111">Child elements</span></span>

|     | <span data-ttu-id="368d4-112">説明</span><span class="sxs-lookup"><span data-stu-id="368d4-112">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="368d4-113">構成セクションの宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="368d4-113">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="368d4-114">構成セクションの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="368d4-114">Defines a namespace for configuration sections.</span></span> |

## <a name="remarks"></a><span data-ttu-id="368d4-115">解説</span><span class="sxs-lookup"><span data-stu-id="368d4-115">Remarks</span></span>

<span data-ttu-id="368d4-116">この要素が構成ファイル内にある場合は、要素の最初の子要素である必要があり **\<configuration>** ます。</span><span class="sxs-lookup"><span data-stu-id="368d4-116">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="368d4-117">例</span><span class="sxs-lookup"><span data-stu-id="368d4-117">Example</span></span>

<span data-ttu-id="368d4-118">次の例は、構成セクションを定義し、そのセクションの設定を定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="368d4-118">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="368d4-119">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="368d4-119">Configuration file</span></span>

<span data-ttu-id="368d4-120">この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではないファイル *Web.config* で使用できます。</span><span class="sxs-lookup"><span data-stu-id="368d4-120">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="368d4-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="368d4-121">See also</span></span>

- [<span data-ttu-id="368d4-122">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="368d4-122">Configuration file schema for the .NET Framework</span></span>](index.md)
