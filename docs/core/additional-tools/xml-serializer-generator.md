---
title: Microsoft XML Serializer Generator
description: Microsoft XML Serializer Generator の概要。 XML Serializer Generator を使用して、プロジェクトに格納される型のために XML シリアル化アセンブリを生成します。
author: honggit
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4b408326bb9f1bc3b82acb92e8daabfd90be43f6
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957898"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="a8d70-104">.NET Core で Microsoft XML Serializer Generator を使用する</span><span class="sxs-lookup"><span data-stu-id="a8d70-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="a8d70-105">このチュートリアルでは、C# .NET Core アプリケーションで Microsoft XML Serializer Generator を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="a8d70-106">このチュートリアルを通して、以下のことを学びます。</span><span class="sxs-lookup"><span data-stu-id="a8d70-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="a8d70-107">.NET Core アプリの作成方法</span><span class="sxs-lookup"><span data-stu-id="a8d70-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="a8d70-108">Microsoft.XmlSerializer.Generator パッケージへの参照を追加する方法</span><span class="sxs-lookup"><span data-stu-id="a8d70-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="a8d70-109">MyApp.csproj を編集して依存関係を追加する方法</span><span class="sxs-lookup"><span data-stu-id="a8d70-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="a8d70-110">クラスと XmlSerializer を追加する方法</span><span class="sxs-lookup"><span data-stu-id="a8d70-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="a8d70-111">アプリケーションをビルドして実行する方法</span><span class="sxs-lookup"><span data-stu-id="a8d70-111">How to build and run the application</span></span>

<span data-ttu-id="a8d70-112">.NET Framework の [Xml シリアライザー ジェネレーター (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) と同様に、[Microsoft.XmlSerializer.Generator NuGet パッケージ](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)は .NET Core および .NET Standard プロジェクト用の同等のものです。</span><span class="sxs-lookup"><span data-stu-id="a8d70-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="a8d70-113">アセンブリに含まれる型の XML シリアル化アセンブリを作成することで、<xref:System.Xml.Serialization.XmlSerializer> を使用してその型のオブジェクトをシリアル化または逆シリアル化するときの XML シリアル化の起動パフォーマンスを改善します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8d70-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a8d70-114">Prerequisites</span></span>

<span data-ttu-id="a8d70-115">このチュートリアルを完了するには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="a8d70-115">To complete this tutorial:</span></span>

- <span data-ttu-id="a8d70-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) 以降。</span><span class="sxs-lookup"><span data-stu-id="a8d70-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="a8d70-117">任意のコード エディター。</span><span class="sxs-lookup"><span data-stu-id="a8d70-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="a8d70-118">コード エディターをインストールする必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="a8d70-118">Need to install a code editor?</span></span> <span data-ttu-id="a8d70-119">[Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) をお試しください。</span><span class="sxs-lookup"><span data-stu-id="a8d70-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="a8d70-120">.NET Core コンソール アプリケーションで Microsoft XML Serializer Generator を使用する</span><span class="sxs-lookup"><span data-stu-id="a8d70-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="a8d70-121">次の手順では、.NET Core コンソール アプリケーションで XML Serializer Generator を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="a8d70-122">.NET Core コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="a8d70-122">Create a .NET Core console application</span></span>

<span data-ttu-id="a8d70-123">コマンド プロンプトを開き、*MyApp* というフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="a8d70-124">作成したフォルダーに移動し、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="a8d70-125">MyApp プロジェクトで Microsoft.XmlSerializer.Generator パッケージへの参照を追加する</span><span class="sxs-lookup"><span data-stu-id="a8d70-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="a8d70-126">[`dotnet add package`](../tools/dotnet-add-package.md) コマンドを使用して、プロジェクトで参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-126">Use the [`dotnet add package`](../tools/dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="a8d70-127">型:</span><span class="sxs-lookup"><span data-stu-id="a8d70-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="a8d70-128">パッケージを追加した後に MyApp.csproj の変更を確認する</span><span class="sxs-lookup"><span data-stu-id="a8d70-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="a8d70-129">コード エディターを開き、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="a8d70-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="a8d70-130">引き続き、アプリをビルドした *MyApp* ディレクトリから作業します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="a8d70-131">テキスト エディターで *MyApp.csproj* を開きます。</span><span class="sxs-lookup"><span data-stu-id="a8d70-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="a8d70-132">[`dotnet add package`](../tools/dotnet-add-package.md) コマンドを実行すると、以下の行が *MyApp.csproj* プロジェクト ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a8d70-132">After running the [`dotnet add package`](../tools/dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="a8d70-133">.NET Core CLI Tool のサポートのために別の ItemGroup セクションを追加する</span><span class="sxs-lookup"><span data-stu-id="a8d70-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="a8d70-134">検査した `ItemGroup` セクションの後に以下の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="a8d70-135">アプリケーションにクラスを追加する</span><span class="sxs-lookup"><span data-stu-id="a8d70-135">Add a class in the application</span></span>

<span data-ttu-id="a8d70-136">テキスト エディターで *Program.cs* を開きます。</span><span class="sxs-lookup"><span data-stu-id="a8d70-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="a8d70-137">*MyClass* というクラスを *Program.cs* に追加します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="a8d70-138">MyClass 用の `XmlSerializer` を作成する</span><span class="sxs-lookup"><span data-stu-id="a8d70-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="a8d70-139">*Main* 内に次の行を追加して MyClass 用の `XmlSerializer` を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="a8d70-140">アプリケーションのビルドと実行</span><span class="sxs-lookup"><span data-stu-id="a8d70-140">Build and run the application</span></span>

<span data-ttu-id="a8d70-141">*MyApp* フォルダー内のままで、[`dotnet run`](../tools/dotnet-run.md) を介してアプリケーションを実行すると、事前生成されたシリアライザーが実行時に自動的に読み込まれ、使用されます。</span><span class="sxs-lookup"><span data-stu-id="a8d70-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at run time.</span></span>

<span data-ttu-id="a8d70-142">コンソール ウィンドウに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="a8d70-143">[`dotnet run`](../tools/dotnet-run.md) は、[`dotnet build`](../tools/dotnet-build.md) を呼び出してビルド ターゲットがビルドされていることを確認した後、`dotnet <assembly.dll>` を呼び出してターゲット アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8d70-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8d70-144">このチュートリアルで紹介した、アプリケーションを実行するコマンドと手順は、開発時にのみ利用されます。</span><span class="sxs-lookup"><span data-stu-id="a8d70-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="a8d70-145">アプリの展開に進むときは、.NET Core アプリの別の[展開方法](../deploying/index.md)や [`dotnet publish`](../tools/dotnet-publish.md) コマンドを利用した方が効果的な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a8d70-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="a8d70-146">すべて正常に終了すると、*MyApp.XmlSerializers.dll* というアセンブリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a8d70-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="a8d70-147">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="a8d70-147">Congratulations!</span></span> <span data-ttu-id="a8d70-148">今回の成果:</span><span class="sxs-lookup"><span data-stu-id="a8d70-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a8d70-149">.NET Core アプリを作成しました。</span><span class="sxs-lookup"><span data-stu-id="a8d70-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="a8d70-150">Microsoft.XmlSerializer.Generator パッケージへの参照を追加しました。</span><span class="sxs-lookup"><span data-stu-id="a8d70-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="a8d70-151">MyApp.csproj を編集して依存関係を追加しました。</span><span class="sxs-lookup"><span data-stu-id="a8d70-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="a8d70-152">クラスと XmlSerializer を追加しました。</span><span class="sxs-lookup"><span data-stu-id="a8d70-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="a8d70-153">アプリケーションをビルドして実行しました。</span><span class="sxs-lookup"><span data-stu-id="a8d70-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="a8d70-154">関連資料</span><span class="sxs-lookup"><span data-stu-id="a8d70-154">Related resources</span></span>

- [<span data-ttu-id="a8d70-155">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="a8d70-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="a8d70-156">XmlSerializer を使用してシリアル化する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="a8d70-156">How to serialize using XmlSerializer (C#)</span></span>](../../standard/linq/serialize-xmlserializer.md)
- [<span data-ttu-id="a8d70-157">方法: XmlSerializer を使用してシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8d70-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../standard/linq/serialize-xmlserializer.md)
