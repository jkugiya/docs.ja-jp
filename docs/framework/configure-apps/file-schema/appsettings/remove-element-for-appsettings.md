---
description: '詳細情報: <remove> の要素 <appSettings>'
title: <appSettings> の <remove> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: a67003d310377ee4b896843003306201353dae91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699273"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="d1dd2-103">\<appSettings> の \<remove> 要素</span><span class="sxs-lookup"><span data-stu-id="d1dd2-103">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="d1dd2-104">カスタムアプリケーション設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="d1dd2-104">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="d1dd2-105">構文</span><span class="sxs-lookup"><span data-stu-id="d1dd2-105">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="d1dd2-106">属性</span><span class="sxs-lookup"><span data-stu-id="d1dd2-106">Attribute</span></span>

|         | <span data-ttu-id="d1dd2-107">説明</span><span class="sxs-lookup"><span data-stu-id="d1dd2-107">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="d1dd2-108">**key**</span><span class="sxs-lookup"><span data-stu-id="d1dd2-108">**key**</span></span> | <span data-ttu-id="d1dd2-109">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="d1dd2-109">Required attribute.</span></span><br><br><span data-ttu-id="d1dd2-110">削除するキーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1dd2-110">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="d1dd2-111">親要素</span><span class="sxs-lookup"><span data-stu-id="d1dd2-111">Parent element</span></span>

|     | <span data-ttu-id="d1dd2-112">説明</span><span class="sxs-lookup"><span data-stu-id="d1dd2-112">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="d1dd2-113">ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1dd2-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d1dd2-114">子要素</span><span class="sxs-lookup"><span data-stu-id="d1dd2-114">Child elements</span></span>

<span data-ttu-id="d1dd2-115">なし</span><span class="sxs-lookup"><span data-stu-id="d1dd2-115">None</span></span>

## <a name="example"></a><span data-ttu-id="d1dd2-116">例</span><span class="sxs-lookup"><span data-stu-id="d1dd2-116">Example</span></span>

<span data-ttu-id="d1dd2-117">次の例は、のカスタム構成設定を削除する方法を示してい `ApplicationName` ます。</span><span class="sxs-lookup"><span data-stu-id="d1dd2-117">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="d1dd2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1dd2-118">See also</span></span>

- [<span data-ttu-id="d1dd2-119">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="d1dd2-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
