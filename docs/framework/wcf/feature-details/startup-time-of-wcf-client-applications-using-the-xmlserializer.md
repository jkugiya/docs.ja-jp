---
description: '詳細については、「方法: XmlSerializer を使用して WCF クライアントアプリケーションの起動時間を向上させる」を参照してください。'
title: '方法: XmlSerializer を使用する WCF クライアント アプリケーションの起動時間を短縮する'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 8cf46cc35753934e8f4cb3abadc20c912e9efca9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793403"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="54a0b-103">方法: XmlSerializer を使用する WCF クライアント アプリケーションの起動時間を短縮する</span><span class="sxs-lookup"><span data-stu-id="54a0b-103">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>

<span data-ttu-id="54a0b-104"><xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるデータ型を使用するサービスおよびクライアント アプリケーションは、実行時にこのようなデータ型のシリアル化コードを生成およびコンパイルします。このため、起動時のパフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="54a0b-104">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54a0b-105">事前生成済みシリアル化コードはクライアント アプリケーションでのみ使用できます。サービスでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="54a0b-105">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="54a0b-106">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用すると、アプリケーションのコンパイル済みアセンブリから必要なシリアル化コードを生成することで、これらのアプリケーションの起動時のパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="54a0b-106">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="54a0b-107">Svcutil.exe は、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるコンパイル済みアプリケーション アセンブリに格納されたサービス コントラクトで使用されるすべてのデータ型に対して、シリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-107">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="54a0b-108"><xref:System.Xml.Serialization.XmlSerializer> を使用するサービスおよび操作コントラクトは、<xref:System.ServiceModel.XmlSerializerFormatAttribute> でマークされます。</span><span class="sxs-lookup"><span data-stu-id="54a0b-108">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="54a0b-109">XmlSerializer シリアル化コードを生成するには</span><span class="sxs-lookup"><span data-stu-id="54a0b-109">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="54a0b-110">サービスまたはクライアント コードを 1 つ以上のアセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="54a0b-110">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="54a0b-111">SDK コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="54a0b-111">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="54a0b-112">コマンド プロンプトで、次の形式を使用して Svcutil.exe ツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-112">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="54a0b-113">`assemblyPath` 引数には、サービス コントラクト型を格納するアセンブリへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-113">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="54a0b-114">Svcutil.exe は、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるコンパイル済みアプリケーション アセンブリに格納されたサービス コントラクトで使用されるすべてのデータ型に対して、シリアル化コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-114">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="54a0b-115">Svcutil.exe は、C# のシリアル化コードのみを生成できます。</span><span class="sxs-lookup"><span data-stu-id="54a0b-115">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="54a0b-116">入力アセンブリごとに、1 つのソース コード ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="54a0b-116">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="54a0b-117">**/言語** スイッチを使用して、生成されたコードの言語を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="54a0b-117">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="54a0b-118">依存アセンブリへのパスを指定するには、 **/reference** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-118">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="54a0b-119">次のオプションのいずれかを使用して、生成したシリアル化コードをアプリケーションから利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="54a0b-119">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1. <span data-ttu-id="54a0b-120">生成されたシリアル化コードを、[*元のアセンブリ*] .XmlSerializers.dll という名前の別のアセンブリにコンパイルします (たとえば、MyApp.XmlSerializers.dll)。</span><span class="sxs-lookup"><span data-stu-id="54a0b-120">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="54a0b-121">アプリケーションがアセンブリを読み込むことができ、アセンブリが元のアセンブリと同じキーで署名されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="54a0b-121">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="54a0b-122">元のアセンブリを再コンパイルする場合は、シリアル化アセンブリも再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54a0b-122">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2. <span data-ttu-id="54a0b-123">生成されたシリアル化コードを別個のアセンブリにコンパイルし、<xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> を使用するサービス コントラクトで <xref:System.ServiceModel.XmlSerializerFormatAttribute> を使用します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-123">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="54a0b-124"><xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> プロパティまたは <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> プロパティが、コンパイル済みのシリアル化アセンブリを指すように設定します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-124">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3. <span data-ttu-id="54a0b-125">生成されたシリアル化コードをアプリケーション アセンブリにコンパイルし、<xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> を使用するサービス コントラクトに <xref:System.ServiceModel.XmlSerializerFormatAttribute> を追加します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-125">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="54a0b-126"><xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> プロパティおよび <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> プロパティは設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="54a0b-126">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="54a0b-127">既定のシリアル化アセンブリが現在のアセンブリであると見なされます。</span><span class="sxs-lookup"><span data-stu-id="54a0b-127">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="54a0b-128">Visual Studio で XmlSerializer シリアル化コードを生成するには</span><span class="sxs-lookup"><span data-stu-id="54a0b-128">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="54a0b-129">Visual Studio で WCF サービスとクライアントプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-129">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="54a0b-130">次に、クライアントプロジェクトにサービス参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-130">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="54a0b-131"><xref:System.ServiceModel.XmlSerializerFormatAttribute>クライアントアプリプロジェクトの *reference.cs* ファイルの **serviceReference** の下に、サービスコントラクトにを追加  ->  します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-131">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="54a0b-132">これらのファイルを表示するには、 **ソリューションエクスプローラー** 内のすべてのファイルを表示する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="54a0b-132">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="54a0b-133">クライアントアプリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="54a0b-133">Build the client app.</span></span>  
  
4. <span data-ttu-id="54a0b-134">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、次のコマンドを使用して、事前に生成さ *れ* たシリアライザーファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-134">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="54a0b-135">AssemblyPath 引数は、WCF クライアントアセンブリへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-135">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="54a0b-136">例:</span><span class="sxs-lookup"><span data-stu-id="54a0b-136">Such as:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="54a0b-137">*WCFClient.XmlSerializers.dll の .cs* ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="54a0b-137">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="54a0b-138">事前に生成されたシリアル化アセンブリをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="54a0b-138">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="54a0b-139">前の手順の例に基づいて、compile コマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="54a0b-139">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="54a0b-140">生成された *WCFClient.XmlSerializers.dll* がクライアントアプリと同じディレクトリにあることを確認します。これは、この場合 *WCFClient.exe* ます。</span><span class="sxs-lookup"><span data-stu-id="54a0b-140">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="54a0b-141">通常どおりにクライアントアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-141">Run the client app as usual.</span></span> <span data-ttu-id="54a0b-142">事前に生成されたシリアル化アセンブリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="54a0b-142">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54a0b-143">例</span><span class="sxs-lookup"><span data-stu-id="54a0b-143">Example</span></span>  

 <span data-ttu-id="54a0b-144">次のコマンドにより、アセンブリに含まれているサービス コントラクトが使用する `XmlSerializer` 型用のシリアル化型を生成します。</span><span class="sxs-lookup"><span data-stu-id="54a0b-144">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="54a0b-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="54a0b-145">See also</span></span>

- [<span data-ttu-id="54a0b-146">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="54a0b-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
