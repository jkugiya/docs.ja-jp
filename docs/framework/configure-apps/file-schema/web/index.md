---
description: '詳細情報: Web 設定スキーマ'
title: Web 設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: 262a53ae062788143cbacdc1012085186f4c9652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681917"
---
# <a name="web-settings-schema"></a><span data-ttu-id="e04eb-103">Web 設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="e04eb-103">Web Settings Schema</span></span>

<span data-ttu-id="e04eb-104">Web 設定は、CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e04eb-104">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="e04eb-105">これらの設定は、ASP.NET アプリケーションの Web.config ファイルで指定されているアプリケーション ドメインの種類の設定とは異なります。</span><span class="sxs-lookup"><span data-stu-id="e04eb-105">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
<span data-ttu-id="e04eb-106">Web 設定は、.NET Framework のバージョンのインストール フォルダーに配置された Aspnet.config ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e04eb-106">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="e04eb-107">たとえば、.NET Framework 2.0 の Aspnet.config ファイルは次のフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="e04eb-107">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
<span data-ttu-id="e04eb-108">Web 設定は、machine.config ファイル、ルート、Web.config ファイル、アプリケーション レベルの Web.config ファイルなどの他の構成ファイルでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="e04eb-108">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|<span data-ttu-id="e04eb-109">要素</span><span class="sxs-lookup"><span data-stu-id="e04eb-109">Element</span></span>|<span data-ttu-id="e04eb-110">説明</span><span class="sxs-lookup"><span data-stu-id="e04eb-110">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="e04eb-111">ASP.NET ホスト層が使用する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e04eb-111">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="e04eb-112">CPU と、ASP.NET ホスト層によって管理されているプロセス全体の動作に適用される CPU および ASP.NET 設定の実行レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e04eb-112">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e04eb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e04eb-113">See also</span></span>

- [<span data-ttu-id="e04eb-114">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="e04eb-114">Configuration File Schema</span></span>](../index.md)
