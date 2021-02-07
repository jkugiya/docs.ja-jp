---
description: 詳細については、.NET Framework の構成ファイルスキーマに関するページを参照してください。
title: .NET Framework の構成ファイル スキーマ
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: eac6d14f29f5ae0eeb65efe5a1416b8f40583be3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729954"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="b58f6-103">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="b58f6-103">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="b58f6-104">構成ファイルは、設定を変更し、アプリのポリシーを設定するために使用できる標準 XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="b58f6-104">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="b58f6-105">.NET Framework の構成スキーマは、アプリの動作を制御するために構成ファイルで使用できる要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="b58f6-105">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="b58f6-106">このセクションの目次は、スキーマ、起動時の階層、ランタイム、ネットワーク、およびその他の種類の構成設定を反映しています。</span><span class="sxs-lookup"><span data-stu-id="b58f6-106">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="b58f6-107">構成ファイルの種類、形式、および場所の詳細については、「 [アプリの構成](../index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b58f6-107">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="b58f6-108">構成ファイルを直接編集する場合は、XML に関する知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="b58f6-108">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b58f6-109">構成ファイルの XML タグおよび属性では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="b58f6-109">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b58f6-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b58f6-110">In this section</span></span>

<span data-ttu-id="b58f6-111">[**\<configuration>** Element](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-111">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="b58f6-112">すべての構成ファイルの最上位要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-112">The top-level element for all configuration files.</span></span>

<span data-ttu-id="b58f6-113">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-113">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="b58f6-114">構成レベルでのアセンブリ バインディング ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58f6-114">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="b58f6-115">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-115">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="b58f6-116">インクルードする構成ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58f6-116">Specifies a configuration file to include.</span></span>

<span data-ttu-id="b58f6-117">[スタートアップ設定スキーマ](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-117">[Startup Settings Schema](./startup/index.md)</span></span>\
<span data-ttu-id="b58f6-118">使用する共通言語ランタイムのバージョンを指定する要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-118">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="b58f6-119">[ランタイム設定スキーマ](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-119">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="b58f6-120">アセンブリバインディングとランタイム動作を構成する要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-120">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="b58f6-121">[ネットワーク設定スキーマ](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-121">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="b58f6-122">.NET Framework がインターネットに接続する方法を指定する要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-122">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="b58f6-123">[暗号化設定スキーマ](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-123">[Cryptography Settings Schema](./cryptography/index.md)</span></span>\
<span data-ttu-id="b58f6-124">アルゴリズムのフレンドリ名を、暗号化アルゴリズムを実装するクラスにマップする要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-124">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="b58f6-125">[構成セクションのスキーマ](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-125">[Configuration Sections Schema](configuration-sections-schema.md)</span></span>\
<span data-ttu-id="b58f6-126">カスタム設定の構成セクションを作成して使用するために使用される要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-126">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="b58f6-127">[トレースおよびデバッグ設定のスキーマ](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-127">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="b58f6-128">トレーススイッチとリスナーを指定する要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-128">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="b58f6-129">[コンパイラおよび言語プロバイダー設定スキーマ](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-129">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="b58f6-130">使用可能な言語プロバイダーのコンパイラ構成を指定する要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-130">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="b58f6-131">[アプリケーション設定スキーマ](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-131">[Application Settings Schema](application-settings-schema.md)</span></span>\
<span data-ttu-id="b58f6-132">Windows フォームまたは ASP.NET アプリケーションで、アプリケーションスコープの設定とユーザースコープの設定を格納および取得できるようにする要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-132">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="b58f6-133">[アプリ設定スキーマ](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-133">[App Settings Schema](./appsettings/index.md)</span></span>\
<span data-ttu-id="b58f6-134">ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b58f6-134">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="b58f6-135">[Web 設定スキーマ](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-135">[Web Settings Schema](./web/index.md)</span></span>\
<span data-ttu-id="b58f6-136">IIS などのホストアプリケーションで ASP.NET がどのように動作するかを構成するための要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-136">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="b58f6-137">*Aspnet.config* ファイルで使用します。</span><span class="sxs-lookup"><span data-stu-id="b58f6-137">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="b58f6-138">[Windows フォーム構成スキーマ](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-138">[Windows Forms Configuration Schema](winforms/index.md)</span></span>\
<span data-ttu-id="b58f6-139">Windows フォームアプリケーション構成セクション内のすべての要素。マルチモニターや高 DPI のサポートなどのカスタマイズが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b58f6-139">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="b58f6-140">[WCF 構成スキーマ](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-140">[WCF Configuration Schema](./wcf/index.md)</span></span>\
<span data-ttu-id="b58f6-141">WCF サービスおよびクライアントアプリケーションを構成できるすべての要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-141">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="b58f6-142">[WCF ディレクティブの構文](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-142">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="b58f6-143">`@ServiceHost`.Svc コンパイラによって使用されるページ固有の属性を定義するディレクティブについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b58f6-143">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="b58f6-144">[WIF 構成スキーマ](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="b58f6-144">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="b58f6-145">Windows Identity Foundation (WIF) 構成スキーマのすべての要素。</span><span class="sxs-lookup"><span data-stu-id="b58f6-145">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b58f6-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="b58f6-146">Related sections</span></span>

<span data-ttu-id="b58f6-147">[リモート処理設定スキーマ](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b58f6-147">[Remoting Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span>\
<span data-ttu-id="b58f6-148">リモート処理を実装するクライアント アプリケーションとサーバー アプリケーションを構成する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b58f6-148">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="b58f6-149">[ASP.NET 設定スキーマ](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b58f6-149">[ASP.NET Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span>\
<span data-ttu-id="b58f6-150">ASP.NET Web アプリケーションの動作を制御する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b58f6-150">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="b58f6-151">[Web サービス設定スキーマ](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b58f6-151">[Web Services Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span>\
<span data-ttu-id="b58f6-152">ASP.NET Web サービス、およびそれらのクライアントの動作を制御する要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b58f6-152">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="b58f6-153">[.NET Framework アプリの構成](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b58f6-153">[Configuring .NET Framework Apps](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="b58f6-154">セキュリティ、アセンブリのバインディング、および .NET Framework のリモート処理を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b58f6-154">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
