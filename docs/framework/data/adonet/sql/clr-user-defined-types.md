---
description: '詳細情報: CLR ユーザー定義型'
title: CLR ユーザー定義型
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: f1732c254d3bf3cb8aa4ba727c420c46ef55c2cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663366"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="56b42-103">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="56b42-103">CLR User-Defined Types</span></span>

<span data-ttu-id="56b42-104">Microsoft SQL Server では、Microsoft .NET Framework 共通言語ランタイム (CLR) を使用して実装されるユーザー定義型 (UDT) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="56b42-104">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="56b42-105">CLR は SQL Server に統合されており、この機構を利用すると、データベースの型システムを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="56b42-105">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="56b42-106">UDT を利用すれば、SQL Server データ型システムのユーザー拡張が可能であり、複雑な構造化型を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="56b42-106">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="56b42-107">UDT は、アプリケーション アーキテクチャの観点から見て 2 つの重要な利点を備えています。</span><span class="sxs-lookup"><span data-stu-id="56b42-107">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
- <span data-ttu-id="56b42-108">内部状態と外部動作の間の (クライアントとサーバーの両方での) 強力なカプセル化。</span><span class="sxs-lookup"><span data-stu-id="56b42-108">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
- <span data-ttu-id="56b42-109">他の関連するサーバー機能との緊密な統合。</span><span class="sxs-lookup"><span data-stu-id="56b42-109">Deep integration with other related server features.</span></span> <span data-ttu-id="56b42-110">独自の UDT を定義すると、列定義、変数、パラメーター、関数の結果、カーソル、トリガー、およびレプリケーションなど、SQL Server のシステム型を利用できるすべてのコンテキストでその UDT を使用できます。</span><span class="sxs-lookup"><span data-stu-id="56b42-110">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="56b42-111">詳細については、ご使用中の SQL Server のバージョンに対応する [SQL Server ドキュメント](/sql)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56b42-111">For more detailed information, see the [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="56b42-112">**SQL Server のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="56b42-112">**SQL Server documentation**</span></span>
  
1. [<span data-ttu-id="56b42-113">CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="56b42-113">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a><span data-ttu-id="56b42-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="56b42-114">See also</span></span>

- [<span data-ttu-id="56b42-115">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="56b42-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
