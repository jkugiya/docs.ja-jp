---
title: COM への .NET Core コンポーネントの公開
description: このチュートリアルでは、.NET Core から COM にクラスを公開する方法について説明します。 COM サーバーと、レジストリを使用しない COM 用のサイドバイサイド サーバー マニフェストを生成します。
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 13c91e5cb6728c5669642d1b5f7bb461efdd44f8
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065052"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="c3b7a-104">COM への .NET Core コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="c3b7a-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="c3b7a-105">.NET Core では、.NET Framework と比較し、.NET オブジェクトを COM に公開する工程が大幅に簡素化されています。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="c3b7a-106">次の手順では、クラスを COM に公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="c3b7a-107">このチュートリアルでは、次の方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="c3b7a-108">.NET Core から COM にクラスを公開します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="c3b7a-109">使用する .NET Core ライブラリをビルドする一環として、COM サーバーを生成します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="c3b7a-110">レジストリを使用しない COM 用の side-by-side サーバー マニフェストを自動生成します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3b7a-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c3b7a-111">Prerequisites</span></span>

- <span data-ttu-id="c3b7a-112">[NET Core 3.0 SDK](https://dotnet.microsoft.com/download) 以降のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="c3b7a-113">ライブラリを作成する</span><span class="sxs-lookup"><span data-stu-id="c3b7a-113">Create the library</span></span>

<span data-ttu-id="c3b7a-114">最初の手順では、ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="c3b7a-115">新しいフォルダーを作成し、そのフォルダーで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="c3b7a-116">`Class1.cs`を開きます。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="c3b7a-117">ファイルの先頭に、`using System.Runtime.InteropServices;` を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="c3b7a-118">`IServer` という名前のインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="c3b7a-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-119">For example:</span></span>

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. <span data-ttu-id="c3b7a-120">このインターフェイスに、実装する COM インターフェイス用のインターフェイス GUID を使用して、`[Guid("<IID>")]` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="c3b7a-121">たとえば、`[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]` のようにします。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="c3b7a-122">この GUID は、COM 用のこのインターフェイスの唯一の識別子であるため、一意である必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="c3b7a-123">Visual Studio で GUID を作成するには、[ツール] > [GUID の作成] の順に移動して GUI の作成ツールを開きます。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="c3b7a-124">インターフェイスに `[InterfaceType]` 属性を追加し、お使いのインターフェイスで実装すべき基本 COM インターフェイスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="c3b7a-125">`IServer` を実装する、`Server` という名前のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="c3b7a-126">クラスに、実装する COM クラス用のクラス識別子 GUID を使用して、`[Guid("<CLSID>")]` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="c3b7a-127">たとえば、`[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]` のようにします。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="c3b7a-128">インターフェイス GUID でこの GUID は、COM ではこのインターフェイスの唯一の識別子であるため、一意である必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="c3b7a-129">インターフェイスとクラスの両方に `[ComVisible(true)]` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3b7a-130">.NET Framework とは異なり、.NET Core では COM を使用してアクティブ化したいすべてのクラスの CLSID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="c3b7a-131">COM ホストを生成する</span><span class="sxs-lookup"><span data-stu-id="c3b7a-131">Generate the COM host</span></span>

1. <span data-ttu-id="c3b7a-132">`.csproj` プロジェクト ファイルを開き、`<PropertyGroup></PropertyGroup>` タグの内側に `<EnableComHosting>true</EnableComHosting>` を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="c3b7a-133">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-133">Build the project.</span></span>

<span data-ttu-id="c3b7a-134">結果として、`ProjectName.dll`、`ProjectName.runtimeconfig.json`、`ProjectName.deps.json`、および`ProjectName.comhost.dll` ファイルが出力されます。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="c3b7a-135">COM 用の COM ホストを登録する</span><span class="sxs-lookup"><span data-stu-id="c3b7a-135">Register the COM host for COM</span></span>

<span data-ttu-id="c3b7a-136">管理者特権でのコマンド プロンプトを開き、`regsvr32 ProjectName.comhost.dll` を実行します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="c3b7a-137">これにより、公開されているすべての .NET オブジェクトが COM に登録されます。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="c3b7a-138">Regfree COM を有効にする</span><span class="sxs-lookup"><span data-stu-id="c3b7a-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="c3b7a-139">`.csproj` プロジェクト ファイルを開き、`<PropertyGroup></PropertyGroup>` タグの内側に `<EnableRegFreeCom>true</EnableRegFreeCom>` を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="c3b7a-140">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-140">Build the project.</span></span>

<span data-ttu-id="c3b7a-141">これで結果として、`ProjectName.X.manifest` ファイルも出力されます。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="c3b7a-142">このファイルが、Registry-Free COM で使用される side-by-side マニフェストです。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="c3b7a-143">サンプル</span><span class="sxs-lookup"><span data-stu-id="c3b7a-143">Sample</span></span>

<span data-ttu-id="c3b7a-144">GitHub の dotnet/samples リポジトリには、完全に機能する [COM サーバーのサンプル](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo)があります。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="c3b7a-145">補足メモ</span><span class="sxs-lookup"><span data-stu-id="c3b7a-145">Additional notes</span></span>

<span data-ttu-id="c3b7a-146">.NET Core では、.NET Framework とは異なり、.NET Core アセンブリからの COM タイプ ライブラリ (TLB) の生成はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="c3b7a-147">このガイダンスは、COM インターフェイスのネイティブ宣言のために、IDL ファイルまたは C/C++ ヘッダーを手動で記述する方法について説明するものです。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3b7a-148">.NET Framework では、32 ビットと 64 ビットの両方のクライアントで "Any CPU" アセンブリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-148">In .NET Framework, an "Any CPU" assembly can be consumed by both 32-bit and 64-bit clients.</span></span> <span data-ttu-id="c3b7a-149">.NET Core、.NET 5、およびそれ以降のバージョンでは、既定で "Any CPU" アセンブリに 64 ビットの *\*.comhost.dll* が付属しています。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-149">By default, in .NET Core, .NET 5, and later versions, "Any CPU" assemblies are accompanied by a 64-bit *\*.comhost.dll*.</span></span> <span data-ttu-id="c3b7a-150">このため、これらを使用できるのは 64 ビットのクライアントでのみとなります。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-150">Because of this, they can only be consumed by 64-bit clients.</span></span> <span data-ttu-id="c3b7a-151">これは SDK で示されるものであるため、既定値となります。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-151">That is the default because that is what the SDK represents.</span></span> <span data-ttu-id="c3b7a-152">この動作は、"自己完結型" 機能が公開される方法と同じです。既定では、SDK によって提供されるものが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-152">This behavior is identical to how the "self-contained" feature is published: by default it uses what the SDK provides.</span></span> <span data-ttu-id="c3b7a-153">MSBuild の `NETCoreSdkRuntimeIdentifier` プロパティによって、 *\*.comhost.dll* のビットが決まります。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-153">The `NETCoreSdkRuntimeIdentifier` MSBuild property determines the bitness of *\*.comhost.dll*.</span></span> <span data-ttu-id="c3b7a-154">マネージド部分は実際には想定どおりにビットには対応していませんが、付随するネイティブ資産の既定値はターゲットとなる SDK になります。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-154">The managed part is actually bitness agnostic as expected, but the accompanying native asset defaults to the targeted SDK.</span></span>

<span data-ttu-id="c3b7a-155">COM コンポーネントの[自己完結型の配置](../deploying/index.md#publish-self-contained)はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-155">[Self-contained deployments](../deploying/index.md#publish-self-contained) of COM components are not supported.</span></span> <span data-ttu-id="c3b7a-156">COM コンポーネントの[フレームワークに依存する配置](../deploying/index.md#publish-framework-dependent)のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-156">Only [framework-dependent deployments](../deploying/index.md#publish-framework-dependent) of COM components are supported.</span></span>

<span data-ttu-id="c3b7a-157">また、.NET Framework と .NET Core の両方を同じプロセスに読み込むと、診断が制限されます。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-157">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="c3b7a-158">主にマネージド コンポーネントのデバッグが制限されます。これは、.NET Framework と .NET Core の両方を同時にデバッグすることはできないためです。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-158">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="c3b7a-159">また、2 つのランタイム インスタンスはマネージド アセンブリを共有しません。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-159">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="c3b7a-160">つまり、2 つのランタイム間で実際の .NET 型を共有することはできません。代わりに、すべての対話を、公開されている COM インターフェイス コントラクトに制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3b7a-160">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
