---
description: '詳細情報: モデリングとマッピング'
title: モデリングとマッピング
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 063cac072b7a205a471cd808fc85ad9a3ac71288
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795002"
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="46741-103">モデリングとマッピング</span><span class="sxs-lookup"><span data-stu-id="46741-103">Modeling and Mapping</span></span>

<span data-ttu-id="46741-104">Entity Framework では、概念モデル、ストレージ モデル、およびこの 2 つのモデル間のマッピングをアプリケーションに最適な方法で定義できます。</span><span class="sxs-lookup"><span data-stu-id="46741-104">In the Entity Framework, you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="46741-105">Visual Studio の Entity Data Model ツールを使用すると、データベースまたはグラフィカルなモデルから [.edmx ファイル](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))を作成し、データベースまたはモデルが変更されたときにそのファイルを更新できます。</span><span class="sxs-lookup"><span data-stu-id="46741-105">The Entity Data Model Tools in Visual Studio allow you to create an .[edmx file](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="46741-106">Entity Framework 4.1 以降では、Code First の開発を使用してモデルをプログラムで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="46741-106">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="46741-107">Code First の開発に対しては、2 つの異なるシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="46741-107">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="46741-108">どちらの場合でも、開発者は .NET Framework のクラス定義をコーディングしてモデルを定義し、データ注釈または Fluent API を使用してオプションで追加のマッピングまたは構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="46741-108">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="46741-109">詳しくは、「[モデルの作成](/ef/ef6/modeling/)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="46741-109">For more information, see [Creating a Model](/ef/ef6/modeling/).</span></span>  
  
 <span data-ttu-id="46741-110">.NET Framework に含まれている EDM ジェネレーターを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="46741-110">You can also use the EDM Generator, which is included with the .NET Framework.</span></span> <span data-ttu-id="46741-111">EdmGen.exe は、既存のデータ ソースから .csdl ファイル、.ssdl ファイル、および .msl ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="46741-111">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="46741-112">モデルとマッピングの内容を手動で作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="46741-112">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="46741-113">詳しくは、「[EDM ジェネレーター (EdmGen.exe)](edm-generator-edmgen-exe.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="46741-113">For more information, see [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md).</span></span>
