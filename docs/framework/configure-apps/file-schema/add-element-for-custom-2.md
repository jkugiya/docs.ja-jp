---
description: '詳細情報: <add> NameValueSectionHandler および DictionarySectionHandler の要素'
title: <add> NameValueSectionHandler および DictionarySectionHandler の要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 5a8cf22b21370e60086408f792f8137386d07aa3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713053"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="2c956-103">\<add> NameValueSectionHandler および DictionarySectionHandler の要素</span><span class="sxs-lookup"><span data-stu-id="2c956-103">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="2c956-104">カスタムアプリケーション設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="2c956-104">Adds custom application settings.</span></span> <span data-ttu-id="2c956-105">各 **\<add>** タグには、キーと値のペアが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2c956-105">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="2c956-106">構文</span><span class="sxs-lookup"><span data-stu-id="2c956-106">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="2c956-107">属性</span><span class="sxs-lookup"><span data-stu-id="2c956-107">Attributes</span></span>

| <span data-ttu-id="2c956-108">属性</span><span class="sxs-lookup"><span data-stu-id="2c956-108">Attribute</span></span> | <span data-ttu-id="2c956-109">説明</span><span class="sxs-lookup"><span data-stu-id="2c956-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="2c956-110">**key**</span><span class="sxs-lookup"><span data-stu-id="2c956-110">**key**</span></span>   | <span data-ttu-id="2c956-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="2c956-111">Required attribute.</span></span><br><br><span data-ttu-id="2c956-112">設定の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c956-112">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="2c956-113">**value**</span><span class="sxs-lookup"><span data-stu-id="2c956-113">**value**</span></span> | <span data-ttu-id="2c956-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="2c956-114">Required attribute.</span></span><br><br><span data-ttu-id="2c956-115">設定の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c956-115">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="2c956-116">親要素</span><span class="sxs-lookup"><span data-stu-id="2c956-116">Parent element</span></span>

| <span data-ttu-id="2c956-117">要素</span><span class="sxs-lookup"><span data-stu-id="2c956-117">Element</span></span> | <span data-ttu-id="2c956-118">説明</span><span class="sxs-lookup"><span data-stu-id="2c956-118">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="2c956-119">**\<sectionName>** 要素</span><span class="sxs-lookup"><span data-stu-id="2c956-119">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="2c956-120">クラスおよびクラスを使用するカスタム構成セクションの設定を定義し <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> ます。</span><span class="sxs-lookup"><span data-stu-id="2c956-120">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2c956-121">子要素</span><span class="sxs-lookup"><span data-stu-id="2c956-121">Child elements</span></span>

<span data-ttu-id="2c956-122">なし</span><span class="sxs-lookup"><span data-stu-id="2c956-122">None</span></span>

## <a name="example"></a><span data-ttu-id="2c956-123">例</span><span class="sxs-lookup"><span data-stu-id="2c956-123">Example</span></span>

<span data-ttu-id="2c956-124">次の例は、カスタム構成セクションを定義し、要素を使用して設定をセクションに格納する方法を示してい **\<add>** ます。</span><span class="sxs-lookup"><span data-stu-id="2c956-124">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="2c956-125">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="2c956-125">Configuration file</span></span>

<span data-ttu-id="2c956-126">この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではないファイル *Web.config* で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2c956-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c956-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c956-127">See also</span></span>

- [<span data-ttu-id="2c956-128">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="2c956-128">Configuration file schema for the .NET Framework</span></span>](index.md)
