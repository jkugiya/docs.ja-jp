---
description: '詳細情報: ASP.NET での LINQ to SQL N 層'
title: ASP.NET での LINQ to SQL N 層
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: a455525f8f0bbef38487b058d89fd2c9b4dda377
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803803"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="97b15-103">ASP.NET での LINQ to SQL N 層</span><span class="sxs-lookup"><span data-stu-id="97b15-103">LINQ to SQL N-Tier with ASP.NET</span></span>

<span data-ttu-id="97b15-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が使われる ASP.NET アプリケーションでは、<xref:System.Web.UI.WebControls.LinqDataSource> Web サーバー コントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="97b15-104">In ASP.NET applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="97b15-105">コントロールでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に対するクエリの実行、ブラウザーへのデータ送信、データの取得、データベースを更新する [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.DataContext> へのデータ送信などを行う必要があるロジックのほとんどが処理されます。</span><span class="sxs-lookup"><span data-stu-id="97b15-105">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="97b15-106">マークアップでこのコントロールを構成するだけで、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] とブラウザーの間のすべてのデータ転送をコントロールが処理するようになります。</span><span class="sxs-lookup"><span data-stu-id="97b15-106">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="97b15-107">コントロールによってプレゼンテーション層との対話が処理され、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によってデータ層との通信が処理されるため、開発者が ASP.NET の多層アプリケーションで主に注目するのは、カスタム ビジネス ロジックの作成になります。</span><span class="sxs-lookup"><span data-stu-id="97b15-107">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in ASP.NET multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="97b15-108">`LINQDataSource` について詳しくは、「[LinqDataSource Web サーバー コントロールの概要](/previous-versions/aspnet/bb547113(v=vs.100))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97b15-108">For more information about `LINQDataSource`, see [LinqDataSource Web Server Control Overview](/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b15-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="97b15-109">See also</span></span>

- [<span data-ttu-id="97b15-110">LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション</span><span class="sxs-lookup"><span data-stu-id="97b15-110">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
