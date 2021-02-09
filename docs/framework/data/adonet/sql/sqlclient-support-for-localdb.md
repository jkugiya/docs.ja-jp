---
description: '詳細情報: SqlClient による LocalDB のサポート'
title: SqlClient による LocalDB のサポート
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: f99c46277638c810c91f7ceffd0e47c896125c63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767168"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="36695-103">SqlClient による LocalDB のサポート</span><span class="sxs-lookup"><span data-stu-id="36695-103">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="36695-104">この記事では、LocalDB データベースに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="36695-104">This article discusses how to connect to a LocalDB database.</span></span> <span data-ttu-id="36695-105">LocalDB は SQL Server の軽量バージョンです。</span><span class="sxs-lookup"><span data-stu-id="36695-105">LocalDB is a lightweight version of SQL Server.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="36695-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="36695-106">Remarks</span></span>
  
 <span data-ttu-id="36695-107">LocalDB で実行できる操作の概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="36695-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="36695-108">sqllocaldb.exe または app.config ファイルを使用して LocalDB インスタンスを作成および開始する。</span><span class="sxs-lookup"><span data-stu-id="36695-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="36695-109">sqlcmd.exe を使用して LocalDB インスタンスにデータベースを追加および変更する。</span><span class="sxs-lookup"><span data-stu-id="36695-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="36695-110">たとえば、 `sqlcmd -S (localdb)\myinst`のようにします。</span><span class="sxs-lookup"><span data-stu-id="36695-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="36695-111">`AttachDBFilename` 接続文字列キーワードを使用して LocalDB インスタンスにデータベースを追加する。</span><span class="sxs-lookup"><span data-stu-id="36695-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="36695-112">`AttachDBFilename`を使用していて、 `Database` 接続文字列キーワードでデータベースの名前を指定しない場合、アプリケーションを閉じると、データベースは LocalDB インスタンスから削除されます。</span><span class="sxs-lookup"><span data-stu-id="36695-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="36695-113">接続文字列に LocalDB インスタンスを指定する。</span><span class="sxs-lookup"><span data-stu-id="36695-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="36695-114">たとえば、インスタンス名が `myInstance`の場合、接続文字列には次の行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="36695-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="36695-115">`User Instance=True` は LocalDB データベースに接続するときに使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="36695-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
<span data-ttu-id="36695-116">LocalDB のインストールの詳細については、「[SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36695-116">For information about installing LocalDB, see [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb).</span></span>
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="36695-117">名前付きインスタンスをプログラムによって作成する</span><span class="sxs-lookup"><span data-stu-id="36695-117">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="36695-118">アプリケーションは、次のように名前付きインスタンスを作成してデータベースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="36695-118">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="36695-119">app.config ファイルに作成するための LocalDB インスタンスを次のように指定する。</span><span class="sxs-lookup"><span data-stu-id="36695-119">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="36695-120">インスタンスのバージョン番号は LocalDB インストールのバージョン番号と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="36695-120">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- <span data-ttu-id="36695-121">`server` 接続文字列キーワードを使用してインスタンス名を指定する。</span><span class="sxs-lookup"><span data-stu-id="36695-121">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="36695-122">`server` 接続文字列キーワードで指定されたインスタンス名は app.config ファイルで指定された名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36695-122">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="36695-123">.MDF ファイルを指定するには、 `AttachDBFilename` 接続文字列キーワードを使用する。</span><span class="sxs-lookup"><span data-stu-id="36695-123">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36695-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="36695-124">See also</span></span>

- [<span data-ttu-id="36695-125">SQL Server の機能と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="36695-125">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="36695-126">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="36695-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
