---
description: '詳細については、「方法: サービスモニカーを登録および構成する」を参照してください。'
title: '方法: サービス モニカーを登録および構成する'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 9c6867941a5b96c6ced0f8e371e10697144bd121
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643463"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="9c881-103">方法: サービス モニカーを登録および構成する</span><span class="sxs-lookup"><span data-stu-id="9c881-103">How to: Register and Configure a Service Moniker</span></span>

<span data-ttu-id="9c881-104">型指定されたコントラクトを持つ COM アプリケーション内で Windows Communication Foundation (WCF) サービスモニカーを使用する前に、必要な属性型を COM に登録し、必要なバインド構成を使用して COM アプリケーションとモニカーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c881-104">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>

## <a name="register-the-required-attributed-types-with-com"></a><span data-ttu-id="9c881-105">必要な属性型を COM に登録する</span><span class="sxs-lookup"><span data-stu-id="9c881-105">Register the required attributed types with COM</span></span>

1. <span data-ttu-id="9c881-106">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)ツールを使用して、WCF サービスからメタデータコントラクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="9c881-106">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="9c881-107">これにより、WCF クライアントアセンブリとクライアントアプリケーション構成ファイルのソースコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c881-107">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>

2. <span data-ttu-id="9c881-108">アセンブリ内で定義されている型に `ComVisible` という設定をします。</span><span class="sxs-lookup"><span data-stu-id="9c881-108">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="9c881-109">これを行うには、Visual Studio プロジェクトの *AssemblyInfo.cs* ファイルに次の属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="9c881-109">To do so, add the following attribute to the *AssemblyInfo.cs* file in your Visual Studio project.</span></span>

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. <span data-ttu-id="9c881-110">マネージ WCF クライアントを厳密な名前付きアセンブリとしてコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="9c881-110">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="9c881-111">そのためには暗号キー ペアで署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c881-111">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="9c881-112">詳しくは、「[厳密な名前でのアセンブリへの署名](../../../standard/assembly/sign-strong-name.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9c881-112">For more information, see [Signing an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

4. <span data-ttu-id="9c881-113">アセンブリ登録 (Regasm.exe) ツールに `-tlb` オプションを指定して、アセンブリで定義されている型を COM に登録します。</span><span class="sxs-lookup"><span data-stu-id="9c881-113">Use the Assembly Registration (Regasm.exe) tool with the `-tlb` option to register the types in the assembly with COM.</span></span>

5. <span data-ttu-id="9c881-114">グローバル アセンブリ キャッシュ ツール (Gacutil.exe) で、グローバル アセンブリ キャッシュにアセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="9c881-114">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9c881-115">アセンブリへの署名とグローバル アセンブリ キャッシュへの追加は、必須ではありません。しかしこれを済ませておくと、実行時には、適切な場所からアセンブリを読み込むための手順が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="9c881-115">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="9c881-116">必要なバインド構成を使用して COM アプリケーションとモニカーを構成する</span><span class="sxs-lookup"><span data-stu-id="9c881-116">Configure the COM application and the moniker with the required binding configuration</span></span>

- <span data-ttu-id="9c881-117">クライアントアプリケーションの構成ファイルに、生成されたクライアントアプリケーション構成ファイルの [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) によって生成されたバインディング定義を配置します。</span><span class="sxs-lookup"><span data-stu-id="9c881-117">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="9c881-118">たとえば、Visual Basic 6.0 で開発した実行可能ファイルの名前が CallCenterClient.exe の場合、これと同じディレクトリに、CallCenterConfig.exe.config という名前で構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c881-118">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="9c881-119">するとクライアント アプリケーションはモニカーを使えるようになります。</span><span class="sxs-lookup"><span data-stu-id="9c881-119">The client application can now use the moniker.</span></span> <span data-ttu-id="9c881-120">WCF に用意されている標準のバインディングの型のいずれかを使用する場合は、バインディングの構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9c881-120">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>

     <span data-ttu-id="9c881-121">次の型が登録されています。</span><span class="sxs-lookup"><span data-stu-id="9c881-121">The following type is registered.</span></span>

    ```csharp
    using System.ServiceModel;

    [ServiceContract]
    public interface IMathService
    {
        [OperationContract]
        public int Add(int x, int y);
        [OperationContract]
        public int Subtract(int x, int y);
    }
    ```

     <span data-ttu-id="9c881-122">このアプリケーションは、`wsHttpBinding` バインディングを使用して公開されています。</span><span class="sxs-lookup"><span data-stu-id="9c881-122">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="9c881-123">このような型とアプリケーション設定であれば、次のようなモニカー文字列が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c881-123">For the given type and application configuration, the following example moniker strings are used.</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     <span data-ttu-id="9c881-124">または</span><span class="sxs-lookup"><span data-stu-id="9c881-124">or</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     <span data-ttu-id="9c881-125">`IMathService` 型を定義するアセンブリへの参照を追加すれば、次のコード例のように、Visual Basic 6.0 アプリケーションに上記のモニカー文字列 (どちらの形式でも可) を記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9c881-125">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     <span data-ttu-id="9c881-126">この例では、バインド構成の定義は、 `Binding1` *vb6appname.exe.config* など、クライアントアプリケーション用に適切な名前が付けられた構成ファイルに格納されています。</span><span class="sxs-lookup"><span data-stu-id="9c881-126">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as *vb6appname.exe.config*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9c881-127">同様のコードを C#、C++、およびその他の .NET 言語アプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c881-127">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9c881-128">モニカーの形式が正しくない場合、またはサービスが使用できない場合、を呼び出すと、 `GetObject` "構文が無効です" というエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="9c881-128">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="9c881-129">このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9c881-129">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>

     <span data-ttu-id="9c881-130">このトピックでは、Visual Basic 6.0 コードのサービスモニカーを使用することに焦点を当てていますが、他の言語のサービスモニカーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9c881-130">Although this topic focuses on using the service moniker from Visual Basic 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="9c881-131">C++ コードからモニカーを使用している場合、次のコードに示すように、Svcutil.exe によって生成されたアセンブリを、"no_namespace named_guids raw_interfaces_only" と共にインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c881-131">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     <span data-ttu-id="9c881-132">これにより、インポートされたインターフェイス定義は、すべてのメソッドが `HResult` を返すように変更されます。</span><span class="sxs-lookup"><span data-stu-id="9c881-132">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="9c881-133">他の戻り値は、出力パラメーターに変換されます。</span><span class="sxs-lookup"><span data-stu-id="9c881-133">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="9c881-134">メソッドの実行全体は、同じままです。</span><span class="sxs-lookup"><span data-stu-id="9c881-134">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="9c881-135">このために、プロキシでメソッドを呼び出したときの例外の原因を特定できます。</span><span class="sxs-lookup"><span data-stu-id="9c881-135">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="9c881-136">この機能は C++ コードからのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c881-136">This functionality is only available from C++ code.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c881-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c881-137">See also</span></span>

- [<span data-ttu-id="9c881-138">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="9c881-138">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
