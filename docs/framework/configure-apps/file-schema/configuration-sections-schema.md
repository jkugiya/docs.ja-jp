---
description: '詳細情報: 構成セクションスキーマ'
title: 構成セクションのスキーマ
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
ms.openlocfilehash: f16ca16417da0b3ee7a7d0a5ebdd1a446ec0714a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698961"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="91e0c-103">構成セクションのスキーマ</span><span class="sxs-lookup"><span data-stu-id="91e0c-103">Configuration sections schema</span></span>

<span data-ttu-id="91e0c-104">構成セクションスキーマには、構成ファイルのカスタム設定を定義する要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91e0c-104">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="91e0c-105">構成ファイルとスキーマに関する一般的な情報については、 [.NET Framework の構成ファイルスキーマ](index.md)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91e0c-105">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="91e0c-106">説明</span><span class="sxs-lookup"><span data-stu-id="91e0c-106">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="91e0c-107">構成セクションと名前空間の宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91e0c-107">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="91e0c-108">**\<section>** およびの場合 **\<configSections>\*\*\*\*\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="91e0c-108">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="91e0c-109">構成セクションの宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91e0c-109">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="91e0c-110">**\<sectionGroup>** の **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="91e0c-110">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="91e0c-111">構成セクションの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="91e0c-111">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="91e0c-112">未実装の要素</span><span class="sxs-lookup"><span data-stu-id="91e0c-112">Unimplemented elements</span></span>

<span data-ttu-id="91e0c-113">次の要素は影響を与えないため、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="91e0c-113">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**
