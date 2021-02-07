---
description: 詳細については、「アプリ設定スキーマ」を参照してください。
title: アプリ設定スキーマ
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: a98a60b0470e0fa2c03313f25de9b310f5fce785
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699351"
---
# <a name="app-settings-schema"></a><span data-ttu-id="fb5e9-103">アプリ設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="fb5e9-103">App Settings schema</span></span>

<span data-ttu-id="fb5e9-104">ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-104">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="fb5e9-105">要素</span><span class="sxs-lookup"><span data-stu-id="fb5e9-105">Element</span></span> | <span data-ttu-id="fb5e9-106">説明</span><span class="sxs-lookup"><span data-stu-id="fb5e9-106">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="fb5e9-107">**\<add>** **\<clear>** **\<remove>** アプリケーション設定を制御するための、、およびのタグが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-107">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="fb5e9-108">省略可能な **file** 属性があります。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-108">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="fb5e9-109">設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-109">Defines a setting.</span></span> <span data-ttu-id="fb5e9-110">の子 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-110">Child of **\<appSettings>**.</span></span> <span data-ttu-id="fb5e9-111">**key** 属性と **value** 属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-111">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="fb5e9-112">すべての設定をクリアします。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-112">Clears all settings.</span></span> <span data-ttu-id="fb5e9-113">の子 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-113">Child of **\<appSettings>**.</span></span> <span data-ttu-id="fb5e9-114">属性はありません。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-114">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="fb5e9-115">設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-115">Removes a setting.</span></span> <span data-ttu-id="fb5e9-116">の子 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="fb5e9-117">**key** 属性が必要です。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-117">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="fb5e9-118">\<appSettings> 要素</span><span class="sxs-lookup"><span data-stu-id="fb5e9-118">\<appSettings> element</span></span>

<span data-ttu-id="fb5e9-119">この要素に **\<add>** は、 **\<clear>** **\<remove>** アプリケーションの設定を制御するための、、およびのタグが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-119">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="fb5e9-120">**file** の省略可能な属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-120">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="fb5e9-121">\<add> 要素</span><span class="sxs-lookup"><span data-stu-id="fb5e9-121">\<add> element</span></span>

<span data-ttu-id="fb5e9-122">カスタム アプリケーション設定を名前/値のペアとしてアプリケーション設定コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-122">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="fb5e9-123">**key** および **value** の属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-123">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="fb5e9-124">\<clear> 要素</span><span class="sxs-lookup"><span data-stu-id="fb5e9-124">\<clear> element</span></span>

<span data-ttu-id="fb5e9-125">継承されたカスタムアプリケーション設定へのすべての参照を削除し、要素の後にある要素によって追加された参照だけを許可し **\<add>** **\<clear>** ます。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-125">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="fb5e9-126">属性は定義されません。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-126">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="fb5e9-127">\<remove> 要素</span><span class="sxs-lookup"><span data-stu-id="fb5e9-127">\<remove> element</span></span>

<span data-ttu-id="fb5e9-128">アプリケーション設定コレクションから継承したカスタム アプリケーション設定への参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-128">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="fb5e9-129">**key** の属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-129">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="fb5e9-130">例</span><span class="sxs-lookup"><span data-stu-id="fb5e9-130">Example</span></span>

<span data-ttu-id="fb5e9-131">次の例は、カスタム アプリケーション設定を定義する外部アプリケーション設定ファイル (*custom.config*) を示しています。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-131">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="fb5e9-132">次の例は、外部設定ファイルで設定を使用して、独自のアプリケーション設定を設定するアプリケーション構成ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="fb5e9-132">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="fb5e9-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb5e9-133">See also</span></span>

- [<span data-ttu-id="fb5e9-134">アプリケーション設定の概要</span><span class="sxs-lookup"><span data-stu-id="fb5e9-134">Application Settings Overview</span></span>](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [<span data-ttu-id="fb5e9-135">アプリケーション設定アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="fb5e9-135">Application Settings Architecture</span></span>](/dotnet/desktop/winforms/advanced/application-settings-architecture)
