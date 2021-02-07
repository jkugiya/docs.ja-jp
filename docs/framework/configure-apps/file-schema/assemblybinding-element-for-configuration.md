---
description: '詳細情報: <assemblyBinding> の要素 <configuration>'
title: <configuration> の <assemblyBinding> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 5cc3fc7cccd4b9dc7b62815734ff76e32e2243d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730110"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="3288f-103">\<configuration> の \<assemblyBinding> 要素</span><span class="sxs-lookup"><span data-stu-id="3288f-103">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="3288f-104">構成レベルでのアセンブリ バインディング ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="3288f-104">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="3288f-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="3288f-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3288f-106">構文</span><span class="sxs-lookup"><span data-stu-id="3288f-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="3288f-107">属性</span><span class="sxs-lookup"><span data-stu-id="3288f-107">Attribute</span></span>

|           | <span data-ttu-id="3288f-108">説明</span><span class="sxs-lookup"><span data-stu-id="3288f-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="3288f-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="3288f-109">**xmlns**</span></span> | <span data-ttu-id="3288f-110">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3288f-110">Required attribute.</span></span><br><br><span data-ttu-id="3288f-111">アセンブリのバインディングに必要な XML 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="3288f-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="3288f-112">値として、文字列 "urn:schemas-microsoft-com:asm.v1" を使用します。</span><span class="sxs-lookup"><span data-stu-id="3288f-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="3288f-113">親要素</span><span class="sxs-lookup"><span data-stu-id="3288f-113">Parent element</span></span>

|     | <span data-ttu-id="3288f-114">説明</span><span class="sxs-lookup"><span data-stu-id="3288f-114">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="3288f-115">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="3288f-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="3288f-116">子要素</span><span class="sxs-lookup"><span data-stu-id="3288f-116">Child element</span></span>

|     | <span data-ttu-id="3288f-117">説明</span><span class="sxs-lookup"><span data-stu-id="3288f-117">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="3288f-118">インクルードする構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="3288f-118">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3288f-119">解説</span><span class="sxs-lookup"><span data-stu-id="3288f-119">Remarks</span></span>

<span data-ttu-id="3288f-120">要素は、 [**\<linkedConfiguration>**](linkedconfiguration-element.md) アセンブリ構成設定を複製するのではなく、アプリケーション構成ファイルに既知の場所にアセンブリ構成ファイルを含めることができるようにすることで、コンポーネントアセンブリの管理を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="3288f-120">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="3288f-121">**\<linkedConfiguration>** 要素は、Windows サイドバイサイドマニフェストを持つアプリケーションではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3288f-121">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="3288f-122">例</span><span class="sxs-lookup"><span data-stu-id="3288f-122">Example</span></span>

<span data-ttu-id="3288f-123">次の例は、ローカルのハードディスクに構成ファイルを含める方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3288f-123">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3288f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="3288f-124">See also</span></span>

- [<span data-ttu-id="3288f-125">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="3288f-125">Configuration file schema for the .NET Framework</span></span>](index.md)
