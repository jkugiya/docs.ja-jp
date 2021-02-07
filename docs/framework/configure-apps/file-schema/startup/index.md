---
description: '詳細情報: スタートアップ設定スキーマ'
title: スタートアップ設定スキーマ
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: 268b8d8dc2598add61435dd6b07031aa06831737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726092"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="d7138-103">スタートアップ設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="d7138-103">Startup settings schema</span></span>

<span data-ttu-id="d7138-104">スタートアップ設定は、アプリケーションを実行する必要のある共通言語ランタイムのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="d7138-104">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="d7138-105">要素</span><span class="sxs-lookup"><span data-stu-id="d7138-105">Element</span></span>|<span data-ttu-id="d7138-106">説明</span><span class="sxs-lookup"><span data-stu-id="d7138-106">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="d7138-107">バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d7138-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="d7138-108">ランタイムバージョン1.1 でビルドされたアプリケーションでは、要素を使用する必要があり **\<supportedRuntime>** ます。</span><span class="sxs-lookup"><span data-stu-id="d7138-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="d7138-109">アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="d7138-109">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="d7138-110">要素と要素が含まれてい **\<requiredRuntime>** **\<supportedRuntime>** ます。</span><span class="sxs-lookup"><span data-stu-id="d7138-110">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7138-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7138-111">See also</span></span>

- [<span data-ttu-id="d7138-112">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="d7138-112">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d7138-113">方法: .NET Framework 4 以降のバージョンをサポートするアプリを構成する</span><span class="sxs-lookup"><span data-stu-id="d7138-113">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
