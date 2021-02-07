---
description: '詳細については、「方法: Svcutil.exe を使用してコンパイル済みのサービスコードからメタデータをエクスポートする」を参照してください。'
title: '方法: Svcutil.exe を使用してコンパイル済みのサービス コードからメタデータをエクスポートする'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 509d987ff27f9a05ca59d6065d76f27006f3cb25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734205"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="c7801-103">方法: Svcutil.exe を使用してコンパイル済みのサービス コードからメタデータをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="c7801-103">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>

<span data-ttu-id="c7801-104">Svcutil.exe は、次のように、コンパイル済みアセンブリのサービス、コントラクト、およびデータ型のメタデータをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="c7801-104">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
- <span data-ttu-id="c7801-105">Svcutil.exe を使用して、アセンブリのセットに対するすべてのコンパイル済みサービス コントラクトのメタデータをエクスポートするには、入力パラメーターとして各アセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7801-105">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="c7801-106">これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="c7801-106">This is the default behavior.</span></span>  
  
- <span data-ttu-id="c7801-107">Svcutil.exe を使用して、コンパイル済みサービスのメタデータをエクスポートするには、入力パラメーターとしてサービス アセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7801-107">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="c7801-108">`/serviceName` オプションを使用して、エクスポートするサービスの構成名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7801-108">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="c7801-109">Svcutil.exe を実行すると、指定した実行可能アセンブリの構成ファイルが自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="c7801-109">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
- <span data-ttu-id="c7801-110">アセンブリ セットのすべてのデータ コントラクト型をエクスポートするには、`/dataContractOnly` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="c7801-110">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7801-111">`/reference` オプションを使用して、任意の依存アセンブリへのファイル パスを指定してください。</span><span class="sxs-lookup"><span data-stu-id="c7801-111">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="c7801-112">コンパイル済みサービス コントラクトのメタデータをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="c7801-112">To export metadata for compiled service contracts</span></span>  
  
1. <span data-ttu-id="c7801-113">サービス コントラクトの実装を 1 つ以上のクラス ライブラリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c7801-113">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2. <span data-ttu-id="c7801-114">コンパイルされたアセンブリに対して Svcutil.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="c7801-114">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c7801-115">依存アセンブリへのファイル パスを指定するには、`/reference` スイッチを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7801-115">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="c7801-116">コンパイル済みサービスのメタデータをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="c7801-116">To export metadata for a compiled service</span></span>  
  
1. <span data-ttu-id="c7801-117">サービスの実装を実行可能アセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c7801-117">Compile your service implementation into an executable assembly.</span></span>  
  
2. <span data-ttu-id="c7801-118">サービス実行可能ファイルの構成ファイルを作成し、サービス構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="c7801-118">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3. <span data-ttu-id="c7801-119">コンパイルされたサービス実行可能ファイルに対して Svcutil.exe を実行します。その際、`/serviceName` スイッチを使用してサービスの構成名を指定してください。</span><span class="sxs-lookup"><span data-stu-id="c7801-119">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c7801-120">依存アセンブリへのファイル パスを指定するには、`/reference` スイッチを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7801-120">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="c7801-121">コンパイル済みデータ コントラクトのメタデータをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="c7801-121">To export metadata for compiled data contracts</span></span>  
  
1. <span data-ttu-id="c7801-122">データ コントラクトの実装を 1 つ以上のクラス ライブラリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c7801-122">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2. <span data-ttu-id="c7801-123">コンパイルされたアセンブリに対して Svcutil.exe を実行します。その際、`/dataContract` スイッチを使用して、データ コントラクトのメタデータだけが生成されるように指定してください。</span><span class="sxs-lookup"><span data-stu-id="c7801-123">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c7801-124">依存アセンブリへのファイル パスを指定するには、`/reference` スイッチを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7801-124">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```console  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="c7801-125">例</span><span class="sxs-lookup"><span data-stu-id="c7801-125">Example</span></span>  

 <span data-ttu-id="c7801-126">単純なサービス実装および構成のメタデータを生成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="c7801-126">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="c7801-127">サービス コントラクトのメタデータをエクスポートするには、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="c7801-127">To export metadata for the service contract.</span></span>  
  
```console  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="c7801-128">データ コントラクトのメタデータをエクスポートするには、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="c7801-128">To export metadata for the data contracts.</span></span>  
  
```console  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="c7801-129">サービス実装のメタデータをエクスポートするには、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="c7801-129">To export metadata for the service implementation.</span></span>  
  
```console  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="c7801-130">`<path>` は Contracts.dll へのパスです。</span><span class="sxs-lookup"><span data-stu-id="c7801-130">The `<path>` is the path to Contracts.dll.</span></span>  
  
```csharp
// The following service contract and data contracts are compiled into
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
```

```csharp
// The following service implementation is compiled into Service.exe.
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
```

```xml  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7801-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7801-131">See also</span></span>

- [<span data-ttu-id="c7801-132">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="c7801-132">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="c7801-133">メタデータのエクスポートとインポート</span><span class="sxs-lookup"><span data-stu-id="c7801-133">Exporting and Importing Metadata</span></span>](exporting-and-importing-metadata.md)
