---
description: '詳細情報: <configSections> の <sectionGroup> 要素'
title: <configSections> の <sectionGroup> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: 0d822b98acbc041b9d6e146e9cd15848a73d2f88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639888"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="b5727-103">\<configSections> の \<sectionGroup> 要素</span><span class="sxs-lookup"><span data-stu-id="b5727-103">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="b5727-104">構成セクションの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="b5727-104">Defines a namespace for configuration sections.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a><span data-ttu-id="b5727-105">構文</span><span class="sxs-lookup"><span data-stu-id="b5727-105">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="b5727-106">属性</span><span class="sxs-lookup"><span data-stu-id="b5727-106">Attribute</span></span>

|           | <span data-ttu-id="b5727-107">説明</span><span class="sxs-lookup"><span data-stu-id="b5727-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b5727-108">**name**</span><span class="sxs-lookup"><span data-stu-id="b5727-108">**name**</span></span>  | <span data-ttu-id="b5727-109">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="b5727-109">Required attribute.</span></span><br><br><span data-ttu-id="b5727-110">定義するセクション グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5727-110">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="b5727-111">親要素</span><span class="sxs-lookup"><span data-stu-id="b5727-111">Parent element</span></span>

|     | <span data-ttu-id="b5727-112">説明</span><span class="sxs-lookup"><span data-stu-id="b5727-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b5727-113"> **\<configSections>** 要素</span><span class="sxs-lookup"><span data-stu-id="b5727-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="b5727-114">構成セクションと名前空間宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b5727-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b5727-115">子要素</span><span class="sxs-lookup"><span data-stu-id="b5727-115">Child elements</span></span>

|     | <span data-ttu-id="b5727-116">説明</span><span class="sxs-lookup"><span data-stu-id="b5727-116">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="b5727-117">構成セクション宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b5727-117">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b5727-118">解説</span><span class="sxs-lookup"><span data-stu-id="b5727-118">Remarks</span></span>

<span data-ttu-id="b5727-119">セクション グループを宣言すると、構成セクションのコンテナー タグが作成され、他のユーザーによって定義された構成セクションとの名前の競合が発生しなくなります。</span><span class="sxs-lookup"><span data-stu-id="b5727-119">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="b5727-120">**\<sectionGroup>** 要素は、相互に入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b5727-120">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="b5727-121">例</span><span class="sxs-lookup"><span data-stu-id="b5727-121">Example</span></span>

<span data-ttu-id="b5727-122">次の例は、セクション グループを宣言し、セクション グループ内でセクションを宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b5727-122">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="b5727-123">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="b5727-123">Configuration file</span></span>

<span data-ttu-id="b5727-124">この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーション ディレクトリ レベルではない *Web.config* ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5727-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5727-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5727-125">See also</span></span>

- [<span data-ttu-id="b5727-126">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="b5727-126">Configuration file schema for the .NET Framework</span></span>](index.md)
