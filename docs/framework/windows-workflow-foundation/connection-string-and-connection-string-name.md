---
description: 詳細については、接続文字列と接続文字列名に関するページを参照してください。
title: 接続文字列と接続文字列名
ms.date: 03/30/2017
ms.assetid: 473e7a3c-c88a-4a01-914a-bea82ba42866
ms.openlocfilehash: 5de81228434d3099df6e60664db0fea22f63c6ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792740"
---
# <a name="connection-string-and-connection-string-name"></a><span data-ttu-id="15ac0-103">接続文字列と接続文字列名</span><span class="sxs-lookup"><span data-stu-id="15ac0-103">Connection String and Connection String Name</span></span>

<span data-ttu-id="15ac0-104">**接続文字列** プロパティは、SQL Workflow Instance Store が永続性データベースに接続するために使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-104">**Connection String** property specifies the connection string that the SQL Workflow Instance Store should use to connect to a persistence database.</span></span> <span data-ttu-id="15ac0-105">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="15ac0-105">This parameter is an optional parameter.</span></span> <span data-ttu-id="15ac0-106">"**接続文字列名**" プロパティは、SQL Workflow Instance Store が永続性データベースに接続するために使用する名前付き接続文字列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="15ac0-106">**Connection String Name** property specifies the name of the named connection string that the SQL Workflow Instance Store should use to connect to the persistence database.</span></span> <span data-ttu-id="15ac0-107">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="15ac0-107">This parameter is an optional parameter.</span></span> <span data-ttu-id="15ac0-108">SQL Workflow Instance Store で既定の名前付き接続文字列 **DefaultSqlWorkflowInstanceStoreConnectionString** を使用しない場合は、"接続文字列名" プロパティまたは "接続文字列" プロパティの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ac0-108">You should specify a value for the Connection String Name property or the Connection String property if you do not want the SQL Workflow Instance Store to use the default named connection string **DefaultSqlWorkflowInstanceStoreConnectionString**.</span></span>
