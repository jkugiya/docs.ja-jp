---
description: 詳細については、SingleTagSectionHandler のカスタム要素に関するページを参照してください。
title: SingleTagSectionHandler のカスタム要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 83022a1ebf295b89d5f868589e3d9a77c78e3fab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729980"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="06ab0-103">SingleTagSectionHandler のカスタム要素</span><span class="sxs-lookup"><span data-stu-id="06ab0-103">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="06ab0-104">要素によって定義され、クラスを使用するカスタム構成セクションの設定を定義 \<section> し <xref:System.Configuration.SingleTagSectionHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="06ab0-104">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="06ab0-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="06ab0-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="06ab0-106">構文</span><span class="sxs-lookup"><span data-stu-id="06ab0-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="06ab0-107">属性</span><span class="sxs-lookup"><span data-stu-id="06ab0-107">Attributes</span></span>

<span data-ttu-id="06ab0-108">属性と属性値はユーザーが定義します。</span><span class="sxs-lookup"><span data-stu-id="06ab0-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="06ab0-109">親要素</span><span class="sxs-lookup"><span data-stu-id="06ab0-109">Parent element</span></span>

|     | <span data-ttu-id="06ab0-110">説明</span><span class="sxs-lookup"><span data-stu-id="06ab0-110">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="06ab0-111">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="06ab0-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="06ab0-112">子要素</span><span class="sxs-lookup"><span data-stu-id="06ab0-112">Child elements</span></span>

<span data-ttu-id="06ab0-113">なし</span><span class="sxs-lookup"><span data-stu-id="06ab0-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="06ab0-114">解説</span><span class="sxs-lookup"><span data-stu-id="06ab0-114">Remarks</span></span>

<span data-ttu-id="06ab0-115">要素は、 **\<sectionName>** [**\<section>**](section-element.md) 要素内のタグによって定義されたカスタム要素です [**\<configSections>**](configsections-element-for-configuration.md) 。</span><span class="sxs-lookup"><span data-stu-id="06ab0-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="06ab0-116">を呼び出すと、構成システムからオブジェクトが返され <xref:System.Collections.IDictionary> <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="06ab0-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="06ab0-117">例</span><span class="sxs-lookup"><span data-stu-id="06ab0-117">Example</span></span>

<span data-ttu-id="06ab0-118">次の例では、 **\<sampleSection>** クラスによって読み取られた設定を含むというカスタム要素を宣言してい <xref:System.Configuration.SingleTagSectionHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="06ab0-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="06ab0-119">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="06ab0-119">Configuration file</span></span>

<span data-ttu-id="06ab0-120">この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではない *Web.config* ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="06ab0-120">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="06ab0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="06ab0-121">See also</span></span>

- [<span data-ttu-id="06ab0-122">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="06ab0-122">Configuration file schema for the .NET Framework</span></span>](index.md)
