---
title: プラグインがある .NET Core アプリケーションを作成する
description: プラグインをサポートする .NET Core アプリケーションを作成する方法について説明します。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: d3b532ae72a80eef9603fc6f3ada8c11cae966dd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187900"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="63ba0-103">プラグインがある .NET Core アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="63ba0-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="63ba0-104">このチュートリアルでは、カスタムの <xref:System.Runtime.Loader.AssemblyLoadContext> を作成してプラグインを読み込む方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="63ba0-105">プラグインの依存関係を解決するために <xref:System.Runtime.Loader.AssemblyDependencyResolver> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="63ba0-106">このチュートリアルでは、ホスト アプリケーションからプラグインの依存関係を正しく分離します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="63ba0-107">学習内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="63ba0-107">You'll learn how to:</span></span>

- <span data-ttu-id="63ba0-108">プロジェクトを構造化してプラグインをサポートする。</span><span class="sxs-lookup"><span data-stu-id="63ba0-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="63ba0-109">カスタム <xref:System.Runtime.Loader.AssemblyLoadContext> を作成して各プラグインを読み込む。</span><span class="sxs-lookup"><span data-stu-id="63ba0-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="63ba0-110"><xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> 型を使用して、プラグインが依存関係を持てるようにする。</span><span class="sxs-lookup"><span data-stu-id="63ba0-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="63ba0-111">ビルド成果物をコピーするだけで簡単にデプロイできるプラグインを作成する。</span><span class="sxs-lookup"><span data-stu-id="63ba0-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63ba0-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="63ba0-112">Prerequisites</span></span>

- <span data-ttu-id="63ba0-113">[.NET 5 SDK](https://dotnet.microsoft.com/download) 以降のバージョンをインストールする。</span><span class="sxs-lookup"><span data-stu-id="63ba0-113">Install the [.NET 5 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

> [!NOTE]
> <span data-ttu-id="63ba0-114">このサンプル コードのターゲットは .NET 5 ですが、使用されるすべての機能が .NET Core 3.0 で導入されており、それ以降のすべての .NET リリースで使用可能です。</span><span class="sxs-lookup"><span data-stu-id="63ba0-114">The sample code targets .NET 5, but all the features it uses were introduced in .NET Core 3.0 and are available in all .NET releases since then.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="63ba0-115">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="63ba0-115">Create the application</span></span>

<span data-ttu-id="63ba0-116">最初にアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-116">The first step is to create the application:</span></span>

1. <span data-ttu-id="63ba0-117">新しいフォルダーを作成し、そのフォルダーで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-117">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="63ba0-118">プロジェクトのビルドをより容易にするため、同じフォルダー内に Visual Studio のソリューション ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-118">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="63ba0-119">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-119">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="63ba0-120">次のコマンドを実行して、アプリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-120">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="63ba0-121">これで、アプリケーションのスケルトンに入力できます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-121">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="63ba0-122">*AppWithPlugin/Program.cs* ファイル内のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-122">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

```csharp
using PluginBase;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;

namespace AppWithPlugin
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length == 1 && args[0] == "/d")
                {
                    Console.WriteLine("Waiting for any key...");
                    Console.ReadLine();
                }

                // Load commands from plugins.

                if (args.Length == 0)
                {
                    Console.WriteLine("Commands: ");
                    // Output the loaded commands.
                }
                else
                {
                    foreach (string commandName in args)
                    {
                        Console.WriteLine($"-- {commandName} --");

                        // Execute the command with the name passed as an argument.

                        Console.WriteLine();
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
        }
    }
}

```

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="63ba0-123">プラグイン インターフェイスを作成する</span><span class="sxs-lookup"><span data-stu-id="63ba0-123">Create the plugin interfaces</span></span>

<span data-ttu-id="63ba0-124">プラグインがあるアプリをビルドする次の手順は、プラグインで実装する必要があるインターフェイスを定義することです。</span><span class="sxs-lookup"><span data-stu-id="63ba0-124">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="63ba0-125">アプリとプラグイン間の通信に使用する予定のすべての型を含むクラス ライブラリを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="63ba0-125">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="63ba0-126">この分割により、完全なアプリケーションを出荷することなく、プラグイン インターフェイスをパッケージとして公開することができます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-126">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="63ba0-127">プロジェクトのルート フォルダーで `dotnet new classlib -o PluginBase` を実行します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-127">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="63ba0-128">また、`dotnet sln add PluginBase/PluginBase.csproj` を実行してプロジェクトをソリューション ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-128">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="63ba0-129">`PluginBase/Class1.cs` ファイルを削除して、次のインターフェイス定義を使用して、`PluginBase` フォルダー内に `ICommand.cs` という名前の新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-129">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

<span data-ttu-id="63ba0-130">この `ICommand` インターフェイスは、すべてのプラグインで実装されるインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="63ba0-130">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="63ba0-131">これで `ICommand` インターフェイスが定義されたので、アプリケーション プロジェクトをもう少し詳しく入力することができます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-131">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="63ba0-132">ルート フォルダーから `dotnet add AppWithPlugin/AppWithPlugin.csproj reference PluginBase/PluginBase.csproj` コマンドを使用して、参照を `AppWithPlugin` プロジェクトから `PluginBase` に追加します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-132">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin/AppWithPlugin.csproj reference PluginBase/PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="63ba0-133">`// Load commands from plugins` コメントを次のコード スニペットに置き換えて、指定したファイル パスからプラグインを読み込めるようにします。</span><span class="sxs-lookup"><span data-stu-id="63ba0-133">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

```csharp
string[] pluginPaths = new string[]
{
    // Paths to plugins to load.
};

IEnumerable<ICommand> commands = pluginPaths.SelectMany(pluginPath =>
{
    Assembly pluginAssembly = LoadPlugin(pluginPath);
    return CreateCommands(pluginAssembly);
}).ToList();
```

<span data-ttu-id="63ba0-134">次に、`// Output the loaded commands` コメントを次のコード スニペットに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-134">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="63ba0-135">`// Execute the command with the name passed as an argument` コメントを、次のスニペットに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-135">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="63ba0-136">最後に、次に示すように、静的メソッドを `LoadPlugin` と `CreateCommands` という名前の `Program` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-136">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    throw new NotImplementedException();
}

static IEnumerable<ICommand> CreateCommands(Assembly assembly)
{
    int count = 0;

    foreach (Type type in assembly.GetTypes())
    {
        if (typeof(ICommand).IsAssignableFrom(type))
        {
            ICommand result = Activator.CreateInstance(type) as ICommand;
            if (result != null)
            {
                count++;
                yield return result;
            }
        }
    }

    if (count == 0)
    {
        string availableTypes = string.Join(",", assembly.GetTypes().Select(t => t.FullName));
        throw new ApplicationException(
            $"Can't find any type which implements ICommand in {assembly} from {assembly.Location}.\n" +
            $"Available types: {availableTypes}");
    }
}
```

## <a name="load-plugins"></a><span data-ttu-id="63ba0-137">プラグインを読み込む</span><span class="sxs-lookup"><span data-stu-id="63ba0-137">Load plugins</span></span>

<span data-ttu-id="63ba0-138">これでアプリケーションが正しく読み込まれ、読み込んだプラグイン アセンブリからコマンドをインスタンス化できるようになりましたが、まだプラグイン アセンブリを読み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="63ba0-138">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="63ba0-139">次のコンテンツを使用して、*AppWithPlugin* フォルダー内に *PluginLoadContext.cs* という名前のファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-139">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="63ba0-140">`PluginLoadContext` 型は <xref:System.Runtime.Loader.AssemblyLoadContext> から派生します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-140">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="63ba0-141">`AssemblyLoadContext` 型は、アセンブリのバージョンが競合しないように、開発者が読み込んだアセンブリを別のグループに隔離できるようにするランタイムの特殊な型です。</span><span class="sxs-lookup"><span data-stu-id="63ba0-141">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="63ba0-142">さらに、カスタム `AssemblyLoadContext` は、アセンブリを読み込むためにさまざまなパスから選択して、既定の動作をオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-142">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="63ba0-143">`PluginLoadContext` は、.NET Core 3.0 で導入された `AssemblyDependencyResolver` 型のインスタンスを使用して、アセンブリ名をパスに解決します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-143">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="63ba0-144">`AssemblyDependencyResolver` オブジェクトは、.NET クラス ライブラリへのパスを使用して構築されます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-144">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="63ba0-145">これは、パスが `AssemblyDependencyResolver` コンストラクターに渡されたクラス ライブラリの *.deps.json* ファイルに基づいて、アセンブリとネイティブ ライブラリをその相対パスに解決します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-145">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="63ba0-146">カスタム `AssemblyLoadContext` は、プラグインが独自の依存関係を持てるようにし、`AssemblyDependencyResolver` は依存関係を正しく読み込むことを容易にします。</span><span class="sxs-lookup"><span data-stu-id="63ba0-146">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="63ba0-147">これで、`AppWithPlugin` プロジェクトに `PluginLoadContext` 型が追加されたので、次の本文を使用して `Program.LoadPlugin`メソッドを更新します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-147">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    // Navigate up to the solution root
    string root = Path.GetFullPath(Path.Combine(
        Path.GetDirectoryName(
            Path.GetDirectoryName(
                Path.GetDirectoryName(
                    Path.GetDirectoryName(
                        Path.GetDirectoryName(typeof(Program).Assembly.Location)))))));

    string pluginLocation = Path.GetFullPath(Path.Combine(root, relativePath.Replace('\\', Path.DirectorySeparatorChar)));
    Console.WriteLine($"Loading commands from: {pluginLocation}");
    PluginLoadContext loadContext = new PluginLoadContext(pluginLocation);
    return loadContext.LoadFromAssemblyName(new AssemblyName(Path.GetFileNameWithoutExtension(pluginLocation)));
}
```

<span data-ttu-id="63ba0-148">プラグインごとに異なる `PluginLoadContext` インスタンスを使用することで、プラグインは異なる依存関係、または競合する依存関係であっても問題なく持つことができます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-148">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="63ba0-149">依存関係のない単純なプラグイン</span><span class="sxs-lookup"><span data-stu-id="63ba0-149">Simple plugin with no dependencies</span></span>

<span data-ttu-id="63ba0-150">ルート フォルダーに戻り、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-150">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="63ba0-151">次のコマンドを実行して、`HelloPlugin` という名前の新しいクラス ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-151">Run the following command to create a new class library project named `HelloPlugin`:</span></span>

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="63ba0-152">次のコマンドを実行して、そのプロジェクトを `AppWithPlugin` ソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-152">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="63ba0-153">*HelloPlugin/Class1.cs* ファイルを、次のコンテンツを持つ *HelloCommand.cs* という名前のファイルに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-153">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="63ba0-154">次に、*HelloPlugin.csproj* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-154">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="63ba0-155">次のようになっているはずです。</span><span class="sxs-lookup"><span data-stu-id="63ba0-155">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net5</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="63ba0-156">`<Project>` タグの間に、次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-156">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

<span data-ttu-id="63ba0-157">`<Private>false</Private>` 要素は重要です。</span><span class="sxs-lookup"><span data-stu-id="63ba0-157">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="63ba0-158">これは MSBuild に *PluginBase.dll* を HelloPlugin の出力ディレクトリにコピーしないように指示します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-158">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="63ba0-159">*PluginBase.dll* アセンブリが出力ディレクトリに存在すると、`PluginLoadContext` はそこでアセンブリを検索し、*HelloPlugin.dll* アセンブリを読み込むときにそのアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-159">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="63ba0-160">この時点で、`HelloPlugin.HelloCommand` 型は、既定の読み込みコンテキストに読み込まれる `ICommand` インターフェイスではなく、`HelloPlugin` プロジェクトの出力ディレクトリ内の *PluginBase.dll* から `ICommand` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-160">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="63ba0-161">ランタイムでは、これらの 2 つの型は別のアセンブリからの異なる型として認識されるため、`AppWithPlugin.Program.CreateCommands` メソッドではコマンドが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="63ba0-161">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="63ba0-162">結果として、プラグイン インターフェイスを含むアセンブリへの参照に `<Private>false</Private>`メタデータが必要になります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-162">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="63ba0-163">同様に、`PluginBase` が他のパッケージを参照している場合は、`<ExcludeAssets>runtime</ExcludeAssets>` 要素も重要になります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-163">Similarly, the `<ExcludeAssets>runtime</ExcludeAssets>` element is also important if the `PluginBase` references other packages.</span></span> <span data-ttu-id="63ba0-164">この設定は `<Private>false</Private>` と同じ効果を持ちますが、`PluginBase` プロジェクトまたはその依存関係のいずれかに含まれている場合があるパッケージ参照に対して機能します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-164">This setting has the same effect as `<Private>false</Private>` but works on package references that the `PluginBase` project or one of its dependencies may include.</span></span>

<span data-ttu-id="63ba0-165">これで `HelloPlugin` プロジェクトが完了したので、`AppWithPlugin` プロジェクトを更新して、`HelloPlugin` プラグインが配置されている場所を認識できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-165">Now that the `HelloPlugin` project is complete, you should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="63ba0-166">`// Paths to plugins to load` コメントの後に、`@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` (このパスは使用する .NET Core のバージョンによって異なる可能性があります) を `pluginPaths` 配列の要素として追加します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-166">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` (this path could be different based on the .NET Core version you use) as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="63ba0-167">ライブラリ依存関係を持つプラグイン</span><span class="sxs-lookup"><span data-stu-id="63ba0-167">Plugin with library dependencies</span></span>

<span data-ttu-id="63ba0-168">ほぼすべてのプラグインは単純な "Hello World" よりも複雑で、多くのプラグインには他のライブラリへの依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-168">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="63ba0-169">サンプルの `JsonPlugin` および `OldJson` のプラグイン プロジェクトでは、`Newtonsoft.Json` への NuGet パッケージの依存関係を持つプラグインの 2 つの例が示されています。</span><span class="sxs-lookup"><span data-stu-id="63ba0-169">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="63ba0-170">プロジェクト ファイル自体には、プロジェクト参照のための特別な情報は含まれていません。また、(`pluginPaths` 配列へのプラグインのパスを追加した後) プラグインは AppWithPlugin アプリの同じ実行で実行する場合でも、完璧に実行されます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-170">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="63ba0-171">ただし、これらのプロジェクトでは参照されるアセンブリが出力ディレクトリにコピーされないため、プラグインが機能するためには、アセンブリがユーザーのコンピューター上に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-171">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="63ba0-172">この問題を回避する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-172">There are two ways to work around this problem.</span></span> <span data-ttu-id="63ba0-173">1 つ目の方法は、`dotnet publish` コマンドを使用してクラス ライブラリを発行することです。</span><span class="sxs-lookup"><span data-stu-id="63ba0-173">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="63ba0-174">または、プラグインに `dotnet build` の出力を使用できるようにしたい場合は、プラグインのプロジェクト ファイルで `<PropertyGroup>` タグの間に `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>`プロパティを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-174">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="63ba0-175">例については、`XcopyablePlugin` プラグイン プロジェクトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="63ba0-175">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="63ba0-176">サンプル内のその他の例</span><span class="sxs-lookup"><span data-stu-id="63ba0-176">Other examples in the sample</span></span>

<span data-ttu-id="63ba0-177">このチュートリアルの完全なソース コードは [dotnet/samples リポジトリ](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-177">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="63ba0-178">完全なサンプルには、他のいくつかの `AssemblyDependencyResolver` の動作例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="63ba0-178">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="63ba0-179">たとえば、`AssemblyDependencyResolver` オブジェクトも、NuGet パッケージに含まれているローカライズされたサテライト アセンブリと同じようにネイティブ ライブラリを解決できます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-179">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="63ba0-180">サンプル リポジトリの `UVPlugin` と `FrenchPlugin` で、これらのシナリオが示されています。</span><span class="sxs-lookup"><span data-stu-id="63ba0-180">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a><span data-ttu-id="63ba0-181">NuGet パッケージからプラグイン インターフェイスを参照する</span><span class="sxs-lookup"><span data-stu-id="63ba0-181">Reference a plugin interface from a NuGet package</span></span>

<span data-ttu-id="63ba0-182">`A.PluginBase` という名前の NuGet パッケージで定義されているプラグイン インターフェイスを持つアプリ A があるとします。</span><span class="sxs-lookup"><span data-stu-id="63ba0-182">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="63ba0-183">プラグイン プロジェクト内のパッケージを正しく参照するにはどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="63ba0-183">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="63ba0-184">プロジェクト参照の場合、dll が出力にコピーされるのを防止する `<Private>false</Private>` メタデータをプロジェクト ファイル内の `ProjectReference` 要素で使用します。</span><span class="sxs-lookup"><span data-stu-id="63ba0-184">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="63ba0-185">`A.PluginBase` パッケージを正しく参照するために、プロジェクト ファイル内の `<PackageReference>` 要素を次に変更できます。</span><span class="sxs-lookup"><span data-stu-id="63ba0-185">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="63ba0-186">これにより、`A.PluginBase` アセンブリがプラグインの出力ディレクトリにコピーされるのを防ぎ、プラグインで `A.PluginBase` の A のバージョンが確実に使用されるようになります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-186">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="63ba0-187">プラグインのターゲット フレームワークの推奨事項</span><span class="sxs-lookup"><span data-stu-id="63ba0-187">Plugin target framework recommendations</span></span>

<span data-ttu-id="63ba0-188">プラグインの依存関係の読み込みでは *.deps.json* ファイルが使用されるため、プラグインのターゲット フレームワークに関連する課題があります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-188">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="63ba0-189">具体的には、プラグインでは .NET Standard のバージョンではなく、.NET 5 などのランタイムをターゲットとする必要があります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-189">Specifically, your plugins should target a runtime, such as .NET 5, instead of a version of .NET Standard.</span></span> <span data-ttu-id="63ba0-190">プロジェクトがターゲットとするフレームワークに基づいて *.deps.json* ファイルが生成されます。また、多くの .NET Standard と互換性のあるパッケージでは .NET Standard に対してビルドするための参照アセンブリと、特定のランタイムのための実装アセンブリが同梱されているため、 *.deps.json* が実装アセンブリを正しく認識できない場合や、想定していた .NET Core バージョンではなく、アセンブリの .NET Standard バージョンが取得される場合があります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-190">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>

## <a name="plugin-framework-references"></a><span data-ttu-id="63ba0-191">プラグイン フレームワークの参照</span><span class="sxs-lookup"><span data-stu-id="63ba0-191">Plugin framework references</span></span>

<span data-ttu-id="63ba0-192">現時点では、プラグインで新しいフレームワークをプロセスに導入することはできません。</span><span class="sxs-lookup"><span data-stu-id="63ba0-192">Currently, plugins can't introduce new frameworks into the process.</span></span> <span data-ttu-id="63ba0-193">たとえば、ルート `Microsoft.NETCore.App` フレームワークのみを使用するアプリケーションに、`Microsoft.AspNetCore.App` フレームワークを使用するプラグインを読み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="63ba0-193">For example, you can't load a plugin that uses the `Microsoft.AspNetCore.App` framework into an application that only uses the root `Microsoft.NETCore.App` framework.</span></span> <span data-ttu-id="63ba0-194">ホスト アプリケーションは、プラグインで必要なすべてのフレームワークへの参照を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63ba0-194">The host application must declare references to all frameworks needed by plugins.</span></span>
