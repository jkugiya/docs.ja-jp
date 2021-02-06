---
description: '詳細情報: <add> の要素 <appSettings>'
title: <appSettings> の <add> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: f10ffe517b3b25543bc7baed0c7d2af13f48ab02
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652888"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="c07d9-103">\<appSettings> の \<add> 要素</span><span class="sxs-lookup"><span data-stu-id="c07d9-103">\<add> element for \<appSettings></span></span>

<span data-ttu-id="c07d9-104">カスタムアプリケーション設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="c07d9-104">Adds a custom application setting.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="c07d9-105">構文</span><span class="sxs-lookup"><span data-stu-id="c07d9-105">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="c07d9-106">属性</span><span class="sxs-lookup"><span data-stu-id="c07d9-106">Attributes</span></span>

|           | <span data-ttu-id="c07d9-107">説明</span><span class="sxs-lookup"><span data-stu-id="c07d9-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c07d9-108">**key**</span><span class="sxs-lookup"><span data-stu-id="c07d9-108">**key**</span></span>   | <span data-ttu-id="c07d9-109">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="c07d9-109">Required attribute.</span></span><br><br><span data-ttu-id="c07d9-110">追加するキーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c07d9-110">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="c07d9-111">**value**</span><span class="sxs-lookup"><span data-stu-id="c07d9-111">**value**</span></span> | <span data-ttu-id="c07d9-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="c07d9-112">Required attribute.</span></span><br><br><span data-ttu-id="c07d9-113">追加するキーの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c07d9-113">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c07d9-114">親要素</span><span class="sxs-lookup"><span data-stu-id="c07d9-114">Parent element</span></span>

|     | <span data-ttu-id="c07d9-115">説明</span><span class="sxs-lookup"><span data-stu-id="c07d9-115">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="c07d9-116">ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c07d9-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c07d9-117">子要素</span><span class="sxs-lookup"><span data-stu-id="c07d9-117">Child elements</span></span>

<span data-ttu-id="c07d9-118">なし</span><span class="sxs-lookup"><span data-stu-id="c07d9-118">None</span></span>

## <a name="example"></a><span data-ttu-id="c07d9-119">例</span><span class="sxs-lookup"><span data-stu-id="c07d9-119">Example</span></span>

<span data-ttu-id="c07d9-120">次の例は、アプリケーション名のカスタム構成設定を追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c07d9-120">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="c07d9-121">次の例では、要素を使用して、 `<add>` ASP.NET アプリケーションで2つの互換性設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="c07d9-121">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="c07d9-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="c07d9-122">See also</span></span>

- [<span data-ttu-id="c07d9-123">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="c07d9-123">Configuration file schema for the .NET Framework</span></span>](../index.md)
