---
description: '詳細情報: <remove> NameValueSectionHandler および DictionarySectionHandler の要素'
title: <remove> NameValueSectionHandler および DictionarySectionHandler の要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: bf1434b257aa014c8f46e34f2d57d109bd510452
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740081"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="5041a-103">\<remove> NameValueSectionHandler および DictionarySectionHandler の要素</span><span class="sxs-lookup"><span data-stu-id="5041a-103">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="5041a-104">以前に定義した設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="5041a-104">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="5041a-105">構文</span><span class="sxs-lookup"><span data-stu-id="5041a-105">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="5041a-106">属性</span><span class="sxs-lookup"><span data-stu-id="5041a-106">Attribute</span></span>

|           | <span data-ttu-id="5041a-107">説明</span><span class="sxs-lookup"><span data-stu-id="5041a-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="5041a-108">**key**</span><span class="sxs-lookup"><span data-stu-id="5041a-108">**key**</span></span>   | <span data-ttu-id="5041a-109">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="5041a-109">Required attribute.</span></span><br><br><span data-ttu-id="5041a-110">削除する設定の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5041a-110">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="5041a-111">親要素</span><span class="sxs-lookup"><span data-stu-id="5041a-111">Parent element</span></span>

| <span data-ttu-id="5041a-112">要素</span><span class="sxs-lookup"><span data-stu-id="5041a-112">Element</span></span> | <span data-ttu-id="5041a-113">説明</span><span class="sxs-lookup"><span data-stu-id="5041a-113">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="5041a-114">**\<sectionName>** 要素</span><span class="sxs-lookup"><span data-stu-id="5041a-114">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="5041a-115">クラスおよびクラスを使用するカスタム構成セクションの設定を定義し <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="5041a-115">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5041a-116">子要素</span><span class="sxs-lookup"><span data-stu-id="5041a-116">Child elements</span></span>

<span data-ttu-id="5041a-117">なし</span><span class="sxs-lookup"><span data-stu-id="5041a-117">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5041a-118">解説</span><span class="sxs-lookup"><span data-stu-id="5041a-118">Remarks</span></span>

<span data-ttu-id="5041a-119">要素を使用して、 **\<remove>** 構成ファイル階層の上位レベルで定義されているアプリケーションから設定を削除できます。</span><span class="sxs-lookup"><span data-stu-id="5041a-119">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="5041a-120">例</span><span class="sxs-lookup"><span data-stu-id="5041a-120">Example</span></span>

<span data-ttu-id="5041a-121">次の例は、 **\<remove>** アプリケーション構成ファイルで要素を使用して、マシン構成ファイルで以前に定義した設定を削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5041a-121">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="5041a-122">次のマシン構成ファイルのコードでは、セクションを宣言 **\<mySection>** し、2つの設定 ( `key1` と `key2` ) を追加します。</span><span class="sxs-lookup"><span data-stu-id="5041a-122">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="5041a-123">次のアプリケーション構成ファイルのコードは、から設定を削除し `key2` **\<mySection>** ます。</span><span class="sxs-lookup"><span data-stu-id="5041a-123">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="5041a-124">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="5041a-124">Configuration file</span></span>

<span data-ttu-id="5041a-125">この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではないファイル *Web.config* で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5041a-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5041a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5041a-126">See also</span></span>

- [<span data-ttu-id="5041a-127">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="5041a-127">Configuration file schema for the .NET Framework</span></span>](index.md)
