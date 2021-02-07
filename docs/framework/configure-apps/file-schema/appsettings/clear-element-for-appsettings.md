---
description: '詳細情報: <clear> の要素 <appSettings>'
title: <appSettings> の <clear> 要素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 88c6a02441c038619cb74947c024de7712189915
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699338"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="d555f-103">\<appSettings> の \<clear> 要素</span><span class="sxs-lookup"><span data-stu-id="d555f-103">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="d555f-104">カスタムアプリケーション設定をクリアします。</span><span class="sxs-lookup"><span data-stu-id="d555f-104">Clears custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="d555f-105">構文</span><span class="sxs-lookup"><span data-stu-id="d555f-105">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="d555f-106">属性</span><span class="sxs-lookup"><span data-stu-id="d555f-106">Attributes</span></span>

<span data-ttu-id="d555f-107">なし</span><span class="sxs-lookup"><span data-stu-id="d555f-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="d555f-108">親要素</span><span class="sxs-lookup"><span data-stu-id="d555f-108">Parent element</span></span>

|     | <span data-ttu-id="d555f-109">説明</span><span class="sxs-lookup"><span data-stu-id="d555f-109">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="d555f-110">ファイルパス、XML Web サービス Url、その他のカスタムアプリケーション構成情報などのカスタムアプリケーション設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d555f-110">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d555f-111">子要素</span><span class="sxs-lookup"><span data-stu-id="d555f-111">Child elements</span></span>

<span data-ttu-id="d555f-112">なし</span><span class="sxs-lookup"><span data-stu-id="d555f-112">None</span></span>

## <a name="example"></a><span data-ttu-id="d555f-113">例</span><span class="sxs-lookup"><span data-stu-id="d555f-113">Example</span></span>

<span data-ttu-id="d555f-114">次の例は、カスタム構成設定をクリアする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d555f-114">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="d555f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d555f-115">See also</span></span>

- [<span data-ttu-id="d555f-116">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="d555f-116">Configuration file schema for the .NET Framework</span></span>](../index.md)
