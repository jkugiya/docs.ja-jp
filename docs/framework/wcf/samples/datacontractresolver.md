---
description: '詳細情報: DataContractResolver'
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 629316e45a125eaedad46c57dc22844a24d5e79f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778257"
---
# <a name="datacontractresolver"></a><span data-ttu-id="0cf9e-103">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="0cf9e-103">DataContractResolver</span></span>

<span data-ttu-id="0cf9e-104">このサンプルでは、<xref:System.Runtime.Serialization.DataContractResolver> クラスを使用して、シリアル化プロセスおよび逆シリアル化プロセスをカスタマイズする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-104">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="0cf9e-105">このサンプルでは、シリアル化および逆シリアル化の際に CLR 型と xsi:type 表現との間にマッピングを行うために DataContractResolver を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-105">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="0cf9e-106">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="0cf9e-106">Sample Details</span></span>

 <span data-ttu-id="0cf9e-107">サンプルでは、次の CLR 型を定義します。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-107">The sample defines the following CLR types.</span></span>

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 <span data-ttu-id="0cf9e-108">サンプルでは、このアセンブリを読み込み、これらの各型を抽出して、型をシリアル化および逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-108">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="0cf9e-109">次の例で示すように、<xref:System.Runtime.Serialization.DataContractResolver> は <xref:System.Runtime.Serialization.DataContractResolver> 派生クラスのインスタンスを <xref:System.Runtime.Serialization.DataContractSerializer> コンストラクターに渡すことによってシリアル化プロセスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-109">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="0cf9e-110">次のコード例に示すように、サンプルでは CLR 型をシリアル化しています。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-110">The sample then serializes the CLR types as shown in the following code example.</span></span>

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 <span data-ttu-id="0cf9e-111">次のコード例に示すように、サンプルでは xsi:types を逆シリアル化しています。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-111">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 <span data-ttu-id="0cf9e-112">カスタム <xref:System.Runtime.Serialization.DataContractResolver> は <xref:System.Runtime.Serialization.DataContractSerializer> コンストラクターに渡されるため、CLR 型を同等の <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> にマッピングするためのシリアル化時に `xsi:type` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-112">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="0cf9e-113">同様に、<xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> を同等の CLR 型にマッピングするための逆シリアル化時に `xsi:type` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-113">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="0cf9e-114">このサンプルでは、<xref:System.Runtime.Serialization.DataContractResolver> は、次の例のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-114">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="0cf9e-115"><xref:System.Runtime.Serialization.DataContractResolver> から派生するクラスのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-115">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 <span data-ttu-id="0cf9e-116">サンプルの一部として、Types プロジェクトでは、このサンプルで使用するすべての型を含むアセンブリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-116">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="0cf9e-117">このプロジェクトは、シリアル化される型を追加、削除、または変更するために使用します。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-117">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="0cf9e-118">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="0cf9e-118">To use this sample</span></span>

1. <span data-ttu-id="0cf9e-119">Visual Studio 2012 を使用して、DCRSample .sln ソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-119">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="0cf9e-120">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-120">To run the solution, press F5</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0cf9e-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0cf9e-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0cf9e-123">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0cf9e-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0cf9e-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="0cf9e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cf9e-125">See also</span></span>

- [<span data-ttu-id="0cf9e-126">データ コントラクト リゾルバーの使用</span><span class="sxs-lookup"><span data-stu-id="0cf9e-126">Using a Data Contract Resolver</span></span>](../feature-details/using-a-data-contract-resolver.md)
