---
description: '詳細情報: ConfigurationCodeGenerator'
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: f65a32b6e9eadfed8dc8d1066086908c4b9a3396
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778361"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="16cef-103">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="16cef-103">ConfigurationCodeGenerator</span></span>

<span data-ttu-id="16cef-104">ConfigurationCodeGenerator は、カスタム チャネルの実装を構成システムに公開する際に使用できるツールです。</span><span class="sxs-lookup"><span data-stu-id="16cef-104">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="16cef-105">カスタム チャネルのユーザーは、このツールを使用することによって、`NetTcpBinding` などのシステム指定のバインディングやカスタム バインドを `TcpTransportBindingElement` で構成するのと同じように、.config ファイルを使用してカスタム チャネルを構成できます。</span><span class="sxs-lookup"><span data-stu-id="16cef-105">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="16cef-106">新しい `BindingElement` または `Binding` を使用してカスタム チャネルを記述し、プログラミング モデルに公開する場合は、.config ファイルを使用して、`BindingElement` または `Binding` を構成可能にするためのクラスのセットを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16cef-106">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="16cef-107">ConfigurationCodeGenerator ツールを使用すると、こうしたクラスを生成してユーザーの操作性を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="16cef-107">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="16cef-108">ツールをビルドするには</span><span class="sxs-lookup"><span data-stu-id="16cef-108">To build the tool</span></span>  
  
1. <span data-ttu-id="16cef-109">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="16cef-109">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="16cef-110">ソリューションをビルドすると、ConfigurationCodeGenerator.exe ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="16cef-110">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="16cef-111">Samplerun.cmd ファイルには、このツールを使用して [Transport: UDP](transport-udp.md) サンプルのクラスを生成する方法を示すサンプルコマンドラインがあります。</span><span class="sxs-lookup"><span data-stu-id="16cef-111">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="16cef-112">ツールを実行するには</span><span class="sxs-lookup"><span data-stu-id="16cef-112">To run the tool</span></span>  
  
1. <span data-ttu-id="16cef-113">`BindingElement` のカスタム型と `Binding` のカスタム型の両方がある場合は、コマンド プロンプトで次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="16cef-113">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="16cef-114">`BindingElement` のカスタム型のみがある場合は、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="16cef-114">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="16cef-115">`Binding` のカスタム型のみがある場合は、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="16cef-115">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="16cef-116">このコマンドにより、`BindingElement` 用の 3 つの .cs ファイル (/be: オプションを指定した場合)、標準の `Binding` 用の 5 つの .cs ファイル (/sb: オプションを指定した場合)、および 1 つの .xml ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="16cef-116">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="16cef-117">/be オプションを使用した場合、いずれかの .cs ファイルに、バインディング要素用の `BindingElementExtensionSection` が実装されます。</span><span class="sxs-lookup"><span data-stu-id="16cef-117">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="16cef-118">このコードにより、`BindingElement` が構成システムに公開されます。したがって他のカスタム バインディングも、このバインディング要素を使用できます。</span><span class="sxs-lookup"><span data-stu-id="16cef-118">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="16cef-119">他のファイルには、既定値と定数を示すクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="16cef-119">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="16cef-120">ファイルでは、既定値を更新する必要があることが `//TODO` コメントで示されています。</span><span class="sxs-lookup"><span data-stu-id="16cef-120">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="16cef-121">/sb オプションを指定した場合、2 つの .cs ファイルにそれぞれ `StandardBindingElement` と `StandardBindingCollectionElement` が実装されます。これによって、標準バインディングが構成システムに公開されます。</span><span class="sxs-lookup"><span data-stu-id="16cef-121">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="16cef-122">他のファイルには、既定値と定数を示すクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="16cef-122">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="16cef-123">ファイルでは、既定値を更新する必要があることが `//TODO` コメントで示されています。</span><span class="sxs-lookup"><span data-stu-id="16cef-123">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="16cef-124">/Sb: オプションを指定した場合、CodeToAddTo \<*YourStdBinding*> .cs には、標準バインディングを実装するクラスに手動で追加する必要があるコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="16cef-124">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="16cef-125">SampleConfig.xml ファイルには、構成コードが含まれます。このコードは、前の手順 1. または 2. で定義されたハンドラーを登録する構成ファイルに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16cef-125">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
