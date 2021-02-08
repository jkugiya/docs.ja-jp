---
description: '詳細情報: <appSettings> の要素 <configuration>'
title: <configuration> の <appSettings> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: 74a25bb0dffd97057cda45575745b6f51ad2a675
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802490"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="c3129-103">\<configuration> の \<appSettings> 要素</span><span class="sxs-lookup"><span data-stu-id="c3129-103">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="c3129-104">カスタムアプリケーション設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c3129-104">Contains custom application settings.</span></span> <span data-ttu-id="c3129-105">これは、.NET Framework によって提供される定義済みの構成セクションです。</span><span class="sxs-lookup"><span data-stu-id="c3129-105">This is a predefined configuration section provided by the .NET Framework.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a><span data-ttu-id="c3129-106">構文</span><span class="sxs-lookup"><span data-stu-id="c3129-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="c3129-107">属性</span><span class="sxs-lookup"><span data-stu-id="c3129-107">Attribute</span></span>

|           | <span data-ttu-id="c3129-108">説明</span><span class="sxs-lookup"><span data-stu-id="c3129-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c3129-109">**file**</span><span class="sxs-lookup"><span data-stu-id="c3129-109">**file**</span></span>  | <span data-ttu-id="c3129-110">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="c3129-110">Optional attribute.</span></span><br><br><span data-ttu-id="c3129-111">カスタムアプリケーション構成設定を含む外部ファイルへの相対パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3129-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="c3129-112">指定したファイルには、、、およびの各要素で指定したものと同じ種類の設定が含まれて **\<add>** **\<remove>** おり、これらの **\<clear>** 要素と同じキー/値ペアの形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3129-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="c3129-113">指定されたパスは、メイン構成ファイルに対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="c3129-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="c3129-114">Windows フォームアプリケーションの場合、これはアプリケーション構成ファイルの場所ではなく、バイナリフォルダー ( */bin/debug* など) です。</span><span class="sxs-lookup"><span data-stu-id="c3129-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="c3129-115">Web フォームアプリケーションの場合、パスはアプリケーションルートに対して相対的で、 *web.config* ファイルが配置されます。</span><span class="sxs-lookup"><span data-stu-id="c3129-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="c3129-116">指定されたファイルが見つからない場合、ランタイムは属性を無視します。</span><span class="sxs-lookup"><span data-stu-id="c3129-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c3129-117">親要素</span><span class="sxs-lookup"><span data-stu-id="c3129-117">Parent element</span></span>

|     | <span data-ttu-id="c3129-118">説明</span><span class="sxs-lookup"><span data-stu-id="c3129-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c3129-119">**\<configuration>** 要素</span><span class="sxs-lookup"><span data-stu-id="c3129-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="c3129-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="c3129-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c3129-121">子要素</span><span class="sxs-lookup"><span data-stu-id="c3129-121">Child elements</span></span>

|     | <span data-ttu-id="c3129-122">説明</span><span class="sxs-lookup"><span data-stu-id="c3129-122">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="c3129-123">カスタムアプリケーション設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3129-123">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="c3129-124">以前に定義したアプリケーション設定をすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="c3129-124">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="c3129-125">以前に定義したアプリケーション設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="c3129-125">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c3129-126">解説</span><span class="sxs-lookup"><span data-stu-id="c3129-126">Remarks</span></span>

<span data-ttu-id="c3129-127">要素には、 **\<appSettings>** データベース接続文字列、ファイルパス、XML Web サービス url などのカスタムアプリケーション構成情報、またはアプリケーションのその他のカスタム構成情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c3129-127">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="c3129-128">要素で指定されたキーと値のペア **\<appSettings>** は、クラスを使用してコードでアクセスされ <xref:System.Configuration.ConfigurationSettings> ます。</span><span class="sxs-lookup"><span data-stu-id="c3129-128">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="c3129-129">**ファイル** 属性は、 **\<appSettings>** *Web.config* とアプリケーション構成ファイルの要素で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3129-129">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="c3129-130">この属性は、追加設定を提供するか、要素で指定された設定をオーバーライドする構成ファイルを指定し **\<appSettings>** ます。</span><span class="sxs-lookup"><span data-stu-id="c3129-130">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="c3129-131">**ファイル** 属性は、アプリケーション構成ファイルで指定されたプロジェクト設定をユーザーがオーバーライドする必要がある場合など、ソース管理チームの開発シナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3129-131">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="c3129-132">**File** 属性で指定される構成ファイルは、ではなく、のルートノードである必要があり **\<appSettings>** **\<configuration>** ます。</span><span class="sxs-lookup"><span data-stu-id="c3129-132">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="c3129-133">例</span><span class="sxs-lookup"><span data-stu-id="c3129-133">Example</span></span>

<span data-ttu-id="c3129-134">次の例は、カスタム アプリケーション設定を定義する外部アプリケーション設定ファイル (*custom.config*) を示しています。</span><span class="sxs-lookup"><span data-stu-id="c3129-134">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="c3129-135">次の例は、外部設定ファイルで設定を使用して、独自のアプリケーション設定を設定するアプリケーション構成ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="c3129-135">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c3129-136">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="c3129-136">Configuration file</span></span>

<span data-ttu-id="c3129-137">この要素は、アプリケーション構成ファイル、マシン構成ファイル (*Machine.config*)、およびアプリケーションディレクトリレベルではないファイル *Web.config* で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3129-137">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3129-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3129-138">See also</span></span>

- [<span data-ttu-id="c3129-139">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="c3129-139">Configuration file schema for the .NET Framework</span></span>](../index.md)
