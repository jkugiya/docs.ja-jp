---
description: '詳細情報: <configuration> 要素'
title: <configuration> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: ee48a45ddb987201e84213a0d7674da004951ab1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698999"
---
# <a name="configuration-element"></a><span data-ttu-id="5e093-103">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="5e093-103">\<configuration> element</span></span>

<span data-ttu-id="5e093-104">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="5e093-104">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="5e093-105">構文</span><span class="sxs-lookup"><span data-stu-id="5e093-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="5e093-106">属性</span><span class="sxs-lookup"><span data-stu-id="5e093-106">Attributes</span></span>

<span data-ttu-id="5e093-107">なし</span><span class="sxs-lookup"><span data-stu-id="5e093-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="5e093-108">親要素</span><span class="sxs-lookup"><span data-stu-id="5e093-108">Parent element</span></span>

<span data-ttu-id="5e093-109">なし</span><span class="sxs-lookup"><span data-stu-id="5e093-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="5e093-110">子要素</span><span class="sxs-lookup"><span data-stu-id="5e093-110">Child elements</span></span>

|     | <span data-ttu-id="5e093-111">説明</span><span class="sxs-lookup"><span data-stu-id="5e093-111">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="5e093-112">構成レベルでのアセンブリ バインディング ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="5e093-112">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="5e093-113">**\<startup>** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="5e093-113">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="5e093-114">スタートアップ設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="5e093-114">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="5e093-115">**\<runtime>** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="5e093-115">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="5e093-116">ランタイム設定スキーマ内のすべての要素。</span><span class="sxs-lookup"><span data-stu-id="5e093-116">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="5e093-117">[**\<system.runtime.remoting>** 設定スキーマ](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5e093-117">[**\<system.runtime.remoting>** Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="5e093-118">リモート処理設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="5e093-118">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="5e093-119">**\<system.Net>** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="5e093-119">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="5e093-120">ネットワーク設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="5e093-120">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="5e093-121">**\<cryptographySettings>** 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="5e093-121">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="5e093-122">暗号化設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="5e093-122">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="5e093-123">**\<configuration>** セクションスキーマ</span><span class="sxs-lookup"><span data-stu-id="5e093-123">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="5e093-124">構成セクション設定スキーマ内のすべての要素。</span><span class="sxs-lookup"><span data-stu-id="5e093-124">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="5e093-125">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="5e093-125">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="5e093-126">トレースおよびデバッグ設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="5e093-126">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="5e093-127">[ASP.NET 構成設定スキーマ](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5e093-127">[ASP.NET Configuration Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="5e093-128">ASP.NET 構成スキーマのすべての要素。 ASP.NET Web サイトおよびアプリケーションを構成するための要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5e093-128">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="5e093-129">*Web.config* ファイルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="5e093-129">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="5e093-130">[**\<webServices>** 設定スキーマ](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5e093-130">[**\<webServices>** Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="5e093-131">Web サービス設定スキーマ内のすべての要素。</span><span class="sxs-lookup"><span data-stu-id="5e093-131">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="5e093-132">Web 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="5e093-132">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="5e093-133">IIS などのホスト アプリケーションと ASP.NET の連携を構成する要素も含め、Web 設定スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="5e093-133">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="5e093-134">*aspnet.config* ファイルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="5e093-134">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="5e093-135">解説</span><span class="sxs-lookup"><span data-stu-id="5e093-135">Remarks</span></span>

<span data-ttu-id="5e093-136">各構成ファイルには、要素が1つだけ含まれている必要があり **\<configuration>** ます。</span><span class="sxs-lookup"><span data-stu-id="5e093-136">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e093-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e093-137">See also</span></span>

- [<span data-ttu-id="5e093-138">.NET Framework の構成ファイルスキーマ</span><span class="sxs-lookup"><span data-stu-id="5e093-138">Configuration file schema for the .NET Framework</span></span>](index.md)
