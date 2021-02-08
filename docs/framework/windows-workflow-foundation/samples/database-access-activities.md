---
description: 詳細については、「データベースアクセスアクティビティ」を参照してください。
title: データベース アクセス アクティビティ
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 421da4a55997dac62ccc5c598bc401a20711ec61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792545"
---
# <a name="database-access-activities"></a><span data-ttu-id="01031-103">データベース アクセス アクティビティ</span><span class="sxs-lookup"><span data-stu-id="01031-103">Database Access Activities</span></span>

<span data-ttu-id="01031-104">データベース アクセス アクティビティを使用すると、ワークフロー内でデータベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="01031-104">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="01031-105">これらのアクティビティにより、データベースにアクセスして情報を取得または変更したり、 [ADO.NET](../../data/adonet/index.md) を使用してデータベースにアクセスしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="01031-105">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01031-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="01031-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01031-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="01031-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="01031-108">このディレクトリが存在しない場合は、(ダウンロードページ) にアクセスして、すべての Windows Communication Foundation (WCF) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="01031-108">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01031-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="01031-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="01031-110">データベース アクティビティ</span><span class="sxs-lookup"><span data-stu-id="01031-110">Database Activities</span></span>

<span data-ttu-id="01031-111">以降では、このサンプルに含まれている一連のアクティビティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="01031-111">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="01031-112">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="01031-112">DbUpdate</span></span>

<span data-ttu-id="01031-113">データベースを変更する SQL クエリを実行します (挿入、更新、削除、およびその他の変更)。</span><span class="sxs-lookup"><span data-stu-id="01031-113">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

<span data-ttu-id="01031-114">このクラスは作業を非同期に実行します (<xref:System.Activities.AsyncCodeActivity> から派生し、その非同期機能を使用します)。</span><span class="sxs-lookup"><span data-stu-id="01031-114">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="01031-115">接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="01031-115">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="01031-116">実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。</span><span class="sxs-lookup"><span data-stu-id="01031-116">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="01031-117">`DbUpdate` の実行が完了すると、影響を受けたレコードの数が `AffectedRecords` プロパティで返されます。</span><span class="sxs-lookup"><span data-stu-id="01031-117">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```csharp
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|<span data-ttu-id="01031-118">引数</span><span class="sxs-lookup"><span data-stu-id="01031-118">Argument</span></span>|<span data-ttu-id="01031-119">説明</span><span class="sxs-lookup"><span data-stu-id="01031-119">Description</span></span>|
|-|-|
|<span data-ttu-id="01031-120">ProviderName</span><span class="sxs-lookup"><span data-stu-id="01031-120">ProviderName</span></span>|<span data-ttu-id="01031-121">ADO.NET プロバイダーの不変名。</span><span class="sxs-lookup"><span data-stu-id="01031-121">ADO.NET provider invariant name.</span></span> <span data-ttu-id="01031-122">この引数を設定する場合は、`ConnectionString` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01031-122">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="01031-123">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="01031-123">ConnectionString</span></span>|<span data-ttu-id="01031-124">データベースに接続するための接続文字列。</span><span class="sxs-lookup"><span data-stu-id="01031-124">Connection string to connect to the database.</span></span> <span data-ttu-id="01031-125">この引数を設定する場合は、`ProviderName` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01031-125">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="01031-126">ConfigName</span><span class="sxs-lookup"><span data-stu-id="01031-126">ConfigName</span></span>|<span data-ttu-id="01031-127">接続情報が格納されている構成ファイル セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="01031-127">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="01031-128">この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="01031-128">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="01031-129">CommandType</span><span class="sxs-lookup"><span data-stu-id="01031-129">CommandType</span></span>|<span data-ttu-id="01031-130">実行する <xref:System.Data.Common.DbCommand> の種類。</span><span class="sxs-lookup"><span data-stu-id="01031-130">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="01031-131">Sql</span><span class="sxs-lookup"><span data-stu-id="01031-131">Sql</span></span>|<span data-ttu-id="01031-132">実行する SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="01031-132">The SQL command to be executed.</span></span>|
|<span data-ttu-id="01031-133">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01031-133">Parameters</span></span>|<span data-ttu-id="01031-134">SQL クエリのパラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="01031-134">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="01031-135">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="01031-135">AffectedRecords</span></span>|<span data-ttu-id="01031-136">最後の操作の影響を受けたレコードの数。</span><span class="sxs-lookup"><span data-stu-id="01031-136">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="01031-137">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="01031-137">DbQueryScalar</span></span>

<span data-ttu-id="01031-138">データベースから 1 つの値を取得するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="01031-138">Executes a query that retrieves a single value from the database.</span></span>

<span data-ttu-id="01031-139">このクラスは作業を非同期に実行します (<xref:System.Activities.AsyncCodeActivity%601> から派生し、その非同期機能を使用します)。</span><span class="sxs-lookup"><span data-stu-id="01031-139">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="01031-140">接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="01031-140">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="01031-141">実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。</span><span class="sxs-lookup"><span data-stu-id="01031-141">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="01031-142">`DbQueryScalar`が実行されると、スカラーが `Result out` 引数 (型は `TResult` 、基本クラスで定義されている) で返され <xref:System.Activities.AsyncCodeActivity%601> ます。</span><span class="sxs-lookup"><span data-stu-id="01031-142">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="01031-143">引数</span><span class="sxs-lookup"><span data-stu-id="01031-143">Argument</span></span>|<span data-ttu-id="01031-144">説明</span><span class="sxs-lookup"><span data-stu-id="01031-144">Description</span></span>|
|-|-|
|<span data-ttu-id="01031-145">ProviderName</span><span class="sxs-lookup"><span data-stu-id="01031-145">ProviderName</span></span>|<span data-ttu-id="01031-146">ADO.NET プロバイダーの不変名。</span><span class="sxs-lookup"><span data-stu-id="01031-146">ADO.NET provider invariant name.</span></span> <span data-ttu-id="01031-147">この引数を設定する場合は、`ConnectionString` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01031-147">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="01031-148">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="01031-148">ConnectionString</span></span>|<span data-ttu-id="01031-149">データベースに接続するための接続文字列。</span><span class="sxs-lookup"><span data-stu-id="01031-149">Connection string to connect to the database.</span></span> <span data-ttu-id="01031-150">この引数を設定する場合は、`ProviderName` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01031-150">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="01031-151">ConfigName</span><span class="sxs-lookup"><span data-stu-id="01031-151">ConfigName</span></span>|<span data-ttu-id="01031-152">接続情報が格納されている構成ファイル セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="01031-152">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="01031-153">この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="01031-153">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="01031-154">CommandType</span><span class="sxs-lookup"><span data-stu-id="01031-154">CommandType</span></span>|<span data-ttu-id="01031-155">実行する <xref:System.Data.Common.DbCommand> の種類。</span><span class="sxs-lookup"><span data-stu-id="01031-155">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="01031-156">Sql</span><span class="sxs-lookup"><span data-stu-id="01031-156">Sql</span></span>|<span data-ttu-id="01031-157">実行する SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="01031-157">The SQL command to be executed.</span></span>|
|<span data-ttu-id="01031-158">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01031-158">Parameters</span></span>|<span data-ttu-id="01031-159">SQL クエリのパラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="01031-159">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="01031-160">結果</span><span class="sxs-lookup"><span data-stu-id="01031-160">Result</span></span>|<span data-ttu-id="01031-161">クエリの実行後に取得されたスカラー。</span><span class="sxs-lookup"><span data-stu-id="01031-161">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="01031-162">この引数は `TResult` 型です。</span><span class="sxs-lookup"><span data-stu-id="01031-162">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="01031-163">DbQuery</span><span class="sxs-lookup"><span data-stu-id="01031-163">DbQuery</span></span>

<span data-ttu-id="01031-164">オブジェクトのリストを取得するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="01031-164">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="01031-165">クエリが実行されると、マッピング関数が実行されます (つまり <xref:System.Func%601> < `DbDataReader` 、、 `TResult`> または <xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult`>)。</span><span class="sxs-lookup"><span data-stu-id="01031-165">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="01031-166">このマッピング関数は、`DbDataReader` 内のレコードを取得して、返されるオブジェクトにマップします。</span><span class="sxs-lookup"><span data-stu-id="01031-166">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

<span data-ttu-id="01031-167">接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="01031-167">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="01031-168">実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。</span><span class="sxs-lookup"><span data-stu-id="01031-168">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="01031-169">SQL クエリの結果は、`DbDataReader` を使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="01031-169">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="01031-170">`DbDataReader` が反復処理されて、`DbDataReader` の行が `TResult` のインスタンスにマップされます。</span><span class="sxs-lookup"><span data-stu-id="01031-170">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="01031-171">のユーザーは、 `DbQuery` マッピングコードを指定する必要があります。これは、、>、または> の使用という2つの方法で行うことができ <xref:System.Func%601> < `DbDataReader` `TResult` <xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult` ます。</span><span class="sxs-lookup"><span data-stu-id="01031-171">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="01031-172">1 つ目の方法は、マッピングが 1 つのパルスで実行されるので</span><span class="sxs-lookup"><span data-stu-id="01031-172">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="01031-173">高速ですが、XAML にシリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="01031-173">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="01031-174">2 つ目の方法は、マッピングが複数のパルスで実行されるので</span><span class="sxs-lookup"><span data-stu-id="01031-174">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="01031-175">時間がかかることがありますが、XAML へのシリアル化や宣言による作成が可能です (既存のアクティビティをマッピングに参加させることができます)。</span><span class="sxs-lookup"><span data-stu-id="01031-175">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```csharp
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|<span data-ttu-id="01031-176">引数</span><span class="sxs-lookup"><span data-stu-id="01031-176">Argument</span></span>|<span data-ttu-id="01031-177">説明</span><span class="sxs-lookup"><span data-stu-id="01031-177">Description</span></span>|
|-|-|
|<span data-ttu-id="01031-178">ProviderName</span><span class="sxs-lookup"><span data-stu-id="01031-178">ProviderName</span></span>|<span data-ttu-id="01031-179">ADO.NET プロバイダーの不変名。</span><span class="sxs-lookup"><span data-stu-id="01031-179">ADO.NET provider invariant name.</span></span> <span data-ttu-id="01031-180">この引数を設定する場合は、`ConnectionString` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01031-180">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="01031-181">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="01031-181">ConnectionString</span></span>|<span data-ttu-id="01031-182">データベースに接続するための接続文字列。</span><span class="sxs-lookup"><span data-stu-id="01031-182">Connection string to connect to the database.</span></span> <span data-ttu-id="01031-183">この引数を設定する場合は、`ProviderName` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01031-183">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="01031-184">ConfigName</span><span class="sxs-lookup"><span data-stu-id="01031-184">ConfigName</span></span>|<span data-ttu-id="01031-185">接続情報が格納されている構成ファイル セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="01031-185">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="01031-186">この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="01031-186">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="01031-187">CommandType</span><span class="sxs-lookup"><span data-stu-id="01031-187">CommandType</span></span>|<span data-ttu-id="01031-188">実行する <xref:System.Data.Common.DbCommand> の種類。</span><span class="sxs-lookup"><span data-stu-id="01031-188">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="01031-189">Sql</span><span class="sxs-lookup"><span data-stu-id="01031-189">Sql</span></span>|<span data-ttu-id="01031-190">実行する SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="01031-190">The SQL command to be executed.</span></span>|
|<span data-ttu-id="01031-191">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01031-191">Parameters</span></span>|<span data-ttu-id="01031-192">SQL クエリのパラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="01031-192">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="01031-193">Mapper</span><span class="sxs-lookup"><span data-stu-id="01031-193">Mapper</span></span>|<span data-ttu-id="01031-194"><xref:System.Func%601> < `DbDataReader` `TResult` クエリの `DataReader` 実行結果として取得された内のレコードを取得し、 `TResult` コレクションに追加する型のオブジェクトのインスタンスを返すマッピング関数 (、>) `Result` 。</span><span class="sxs-lookup"><span data-stu-id="01031-194">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="01031-195">この場合、マッピングは 1 つのパルスで実行されますが、デザイナーを使用して宣言で作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="01031-195">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="01031-196">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="01031-196">MapperFunc</span></span>|<span data-ttu-id="01031-197"><xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult` クエリの `DataReader` 実行結果として取得された内のレコードを取得し、 `TResult` コレクションに追加する型のオブジェクトのインスタンスを返すマッピング関数 (、>) `Result` 。</span><span class="sxs-lookup"><span data-stu-id="01031-197">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="01031-198">この場合、マッピングは複数のパルスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="01031-198">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="01031-199">この関数は、XAML へのシリアル化や宣言による作成が可能です (既存のアクティビティをマッピングに参加させることができます)。</span><span class="sxs-lookup"><span data-stu-id="01031-199">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="01031-200">結果</span><span class="sxs-lookup"><span data-stu-id="01031-200">Result</span></span>|<span data-ttu-id="01031-201">クエリを実行し、`DataReader` の各レコードに対してマッピング関数を実行した結果として取得されたオブジェクトのリスト。</span><span class="sxs-lookup"><span data-stu-id="01031-201">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="01031-202">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="01031-202">DbQueryDataSet</span></span>

<span data-ttu-id="01031-203"><xref:System.Data.DataSet> を返すクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="01031-203">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="01031-204">このクラスは作業を非同期に実行します </span><span class="sxs-lookup"><span data-stu-id="01031-204">This class performs its work asynchronously.</span></span> <span data-ttu-id="01031-205">> から派生 <xref:System.Activities.AsyncCodeActivity> < `TResult` し、その非同期機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="01031-205">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

<span data-ttu-id="01031-206">接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="01031-206">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="01031-207">実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。</span><span class="sxs-lookup"><span data-stu-id="01031-207">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="01031-208">`DbQueryDataSet`が実行された後、 `DataSet` は、 `Result out` 基本クラスで定義されている型の引数で返され `TResult` <xref:System.Activities.AsyncCodeActivity%601> ます。</span><span class="sxs-lookup"><span data-stu-id="01031-208">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="01031-209">引数</span><span class="sxs-lookup"><span data-stu-id="01031-209">Argument</span></span>|<span data-ttu-id="01031-210">説明</span><span class="sxs-lookup"><span data-stu-id="01031-210">Description</span></span>|
|-|-|
|<span data-ttu-id="01031-211">ProviderName</span><span class="sxs-lookup"><span data-stu-id="01031-211">ProviderName</span></span>|<span data-ttu-id="01031-212">ADO.NET プロバイダーの不変名。</span><span class="sxs-lookup"><span data-stu-id="01031-212">ADO.NET provider invariant name.</span></span> <span data-ttu-id="01031-213">この引数を設定する場合は、`ConnectionString` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01031-213">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="01031-214">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="01031-214">ConnectionString</span></span>|<span data-ttu-id="01031-215">データベースに接続するための接続文字列。</span><span class="sxs-lookup"><span data-stu-id="01031-215">Connection string to connect to the database.</span></span> <span data-ttu-id="01031-216">この引数を設定する場合は、`ProviderName` も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01031-216">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="01031-217">ConfigName</span><span class="sxs-lookup"><span data-stu-id="01031-217">ConfigName</span></span>|<span data-ttu-id="01031-218">接続情報が格納されている構成ファイル セクションの名前。</span><span class="sxs-lookup"><span data-stu-id="01031-218">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="01031-219">この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="01031-219">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="01031-220">CommandType</span><span class="sxs-lookup"><span data-stu-id="01031-220">CommandType</span></span>|<span data-ttu-id="01031-221">実行する <xref:System.Data.Common.DbCommand> の種類。</span><span class="sxs-lookup"><span data-stu-id="01031-221">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="01031-222">Sql</span><span class="sxs-lookup"><span data-stu-id="01031-222">Sql</span></span>|<span data-ttu-id="01031-223">実行する SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="01031-223">The SQL command to be executed.</span></span>|
|<span data-ttu-id="01031-224">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01031-224">Parameters</span></span>|<span data-ttu-id="01031-225">SQL クエリのパラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="01031-225">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="01031-226">結果</span><span class="sxs-lookup"><span data-stu-id="01031-226">Result</span></span>|<span data-ttu-id="01031-227">クエリの実行後に取得された <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="01031-227"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="01031-228">接続情報の構成</span><span class="sxs-lookup"><span data-stu-id="01031-228">Configuring Connection Information</span></span>

<span data-ttu-id="01031-229">すべての DbActivities は同じ構成パラメーターを共有します。</span><span class="sxs-lookup"><span data-stu-id="01031-229">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="01031-230">パラメーターを構成するには次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="01031-230">They can be configured in two ways:</span></span>

- <span data-ttu-id="01031-231">`ConnectionString + InvariantName`: ADO.NET プロバイダーの不変名と接続文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="01031-231">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<DateTime>()
  {
      ProviderName = "System.Data.SqlClient",
      ConnectionString = @"Data Source=.\SQLExpress;
                            Initial Catalog=DbActivitiesSample;
                            Integrated Security=True",
      Sql = "SELECT GetDate()"
  };
  ```

- <span data-ttu-id="01031-232">`ConfigName`: 接続情報を含む構成セクションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="01031-232">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- <span data-ttu-id="01031-233">アクティビティで次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="01031-233">In the activity:</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a><span data-ttu-id="01031-234">このサンプルの実行</span><span class="sxs-lookup"><span data-stu-id="01031-234">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="01031-235">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="01031-235">Setup instructions</span></span>

<span data-ttu-id="01031-236">このサンプルはデータベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="01031-236">This sample uses a database.</span></span> <span data-ttu-id="01031-237">設定と読み込みのためのスクリプト (Setup.cmd) がサンプルに付属しているので、</span><span class="sxs-lookup"><span data-stu-id="01031-237">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="01031-238">そのファイルを、コマンド プロンプトを使用して実行してください。</span><span class="sxs-lookup"><span data-stu-id="01031-238">You must execute that file using the command prompt.</span></span>

<span data-ttu-id="01031-239">Setup.cmd スクリプトは、CreateDb.sql スクリプト ファイルを呼び出します。このスクリプト ファイルには、次の操作を実行する SQL コマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="01031-239">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="01031-240">DbActivitiesSample という名前のデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="01031-240">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="01031-241">Roles テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="01031-241">Creates the Roles table.</span></span>

- <span data-ttu-id="01031-242">Employees テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="01031-242">Creates Employees table.</span></span>

- <span data-ttu-id="01031-243">3 個のレコードを Roles テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="01031-243">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="01031-244">12 個のレコードを Employees テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="01031-244">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="01031-245">Setup.cmd を実行するには</span><span class="sxs-lookup"><span data-stu-id="01031-245">To run Setup.cmd</span></span>

1. <span data-ttu-id="01031-246">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="01031-246">Open a command prompt.</span></span>

2. <span data-ttu-id="01031-247">DbActivities サンプル フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="01031-247">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="01031-248">「Setup. cmd」と入力し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="01031-248">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    > <span data-ttu-id="01031-249">Setup.cmd は、ローカル コンピューターの SqlExpress インスタンスにサンプルをインストールしようとします。</span><span class="sxs-lookup"><span data-stu-id="01031-249">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="01031-250">他の SQL Server インスタンスにインストールする場合は、その新しいインスタンス名を使用して Setup.cmd を編集します。</span><span class="sxs-lookup"><span data-stu-id="01031-250">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="01031-251">サンプル データベースをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="01031-251">To uninstall the sample database</span></span>

1. <span data-ttu-id="01031-252">コマンド プロンプトで、サンプル フォルダーから Cleanup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="01031-252">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="01031-253">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="01031-253">To run the sample</span></span>

1. <span data-ttu-id="01031-254">Visual Studio 2010 でソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="01031-254">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="01031-255">ソリューションをコンパイルするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="01031-255">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="01031-256">Ctrl キーを押しながら F5 キーを押して、サンプルをデバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="01031-256">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01031-257">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="01031-257">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01031-258">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="01031-258">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="01031-259">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="01031-259">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01031-260">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="01031-260">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
