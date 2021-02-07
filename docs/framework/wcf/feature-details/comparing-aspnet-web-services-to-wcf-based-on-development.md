---
description: '詳細: 開発に基づく WCF と ASP.NET ウェブサービスの比較'
title: 開発者の視点から見た ASP.NET Web サービスと WCF との比較
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: fa9db35070bdde32d509f0e9c25dbf179d64da32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743461"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="d1e18-103">開発者の視点から見た ASP.NET Web サービスと WCF との比較</span><span class="sxs-lookup"><span data-stu-id="d1e18-103">Comparing ASP.NET Web Services to WCF Based on Development</span></span>

<span data-ttu-id="d1e18-104">Windows Communication Foundation (WCF) には ASP.NET 互換モードオプションがあります。このオプションを使用すると、WCF アプリケーションを ASP.NET Web サービスのようにプログラミングおよび構成し、その動作を模倣できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-104">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="d1e18-105">次のセクションでは、両方のテクノロジを使用してアプリケーションを開発するために必要なものに基づいて、ASP.NET ウェブサービスと WCF を比較します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-105">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>

## <a name="data-representation"></a><span data-ttu-id="d1e18-106">データ表現</span><span class="sxs-lookup"><span data-stu-id="d1e18-106">Data Representation</span></span>

<span data-ttu-id="d1e18-107">ASP.NET で Web サービスを開発する場合、通常はまず、このサービスが使う複合データ型の定義から始めます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-107">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="d1e18-108">ASP.NET は <xref:System.Xml.Serialization.XmlSerializer> を利用して、.NET Framework 型で表されたデータを XML 形式に変換してサービスとの間でやり取りしたり、XML 形式で受け取ったデータを .NET Framework オブジェクトに変換したりします。</span><span class="sxs-lookup"><span data-stu-id="d1e18-108">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="d1e18-109">ASP.NET サービスで使用する複合データ型を定義するには、<xref:System.Xml.Serialization.XmlSerializer> で XML 形式にシリアル化したり、XML 形式から逆シリアル化したりできる .NET Framework クラスの定義が必要です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-109">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="d1e18-110">クラス定義は手で記述するほか、XML スキーマの型定義から生成することも可能です。それにはコマンド ライン上で実行する XML スキーマ/データ型サポート ユーティリティである xsd.exe を使います。</span><span class="sxs-lookup"><span data-stu-id="d1e18-110">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>

<span data-ttu-id="d1e18-111"><xref:System.Xml.Serialization.XmlSerializer> で XML 形式にシリアル化したり、XML 形式から逆シリアル化したりできる .NET Framework クラスを定義する場合に知っておくべき主な事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-111">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>

- <span data-ttu-id="d1e18-112">XML に変換されるのは、.NET Framework オブジェクトのパブリック フィールドおよびパブリック プロパティに限ります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-112">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>

- <span data-ttu-id="d1e18-113">コレクション クラスのインスタンスを XML 形式にシリアル化できるのは、そのクラスが <xref:System.Collections.IEnumerable> または <xref:System.Collections.ICollection> インターフェイスを実装している場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-113">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>

- <span data-ttu-id="d1e18-114"><xref:System.Collections.IDictionary> インターフェイスを実装した、<xref:System.Collections.Hashtable> などのクラスを、XML 形式にシリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-114">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>

- <span data-ttu-id="d1e18-115"><xref:System.Xml.Serialization> 名前空間の属性型は、大部分が .NET Framework クラスやそのメンバーに追加可能であり、これにより、XML での当該クラスのインスタンスの表現方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-115">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>

<span data-ttu-id="d1e18-116">また、WCF アプリケーション開発は、通常、複合型の定義から開始されます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-116">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="d1e18-117">WCF では、ASP.NET Web サービスと同じ .NET Framework 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-117">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>

<span data-ttu-id="d1e18-118">次の <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> サンプルコードに示すように、WCF とを .NET Framework 型に追加して、型のインスタンスを XML にシリアル化し、その型の特定のフィールドまたはプロパティをシリアル化することを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-118">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

<span data-ttu-id="d1e18-119"><xref:System.Runtime.Serialization.DataContractAttribute> は、当該型の中にシリアル化可能なフィールドやプロパティがあることを示し、具体的にどのフィールドやプロパティをシリアル化できるかを <xref:System.Runtime.Serialization.DataMemberAttribute> で示します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-119">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="d1e18-120"><xref:System.Runtime.Serialization.DataContractAttribute> はクラスにも構造体にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-120">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="d1e18-121"><xref:System.Runtime.Serialization.DataMemberAttribute> はフィールドやプロパティに適用します。これはパブリックでもプライベートでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-121">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="d1e18-122">が適用されている型のインスタンス <xref:System.Runtime.Serialization.DataContractAttribute> は、WCF ではデータコントラクトと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-122">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="d1e18-123">これを XML 形式にシリアル化するには <xref:System.Runtime.Serialization.DataContractSerializer> を使います。</span><span class="sxs-lookup"><span data-stu-id="d1e18-123">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

<span data-ttu-id="d1e18-124"><xref:System.Runtime.Serialization.DataContractSerializer> を使う場合と、<xref:System.Xml.Serialization.XmlSerializer> および <xref:System.Xml.Serialization> 名前空間に定義された属性を使う場合の、主な違いを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-124">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>

- <span data-ttu-id="d1e18-125"><xref:System.Xml.Serialization.XmlSerializer> や <xref:System.Xml.Serialization> 名前空間の属性は、XML スキーマで定義された有効な型であればどれにでも .NET Framework 型をマップできるようにするためのものです。これらを使うと、XML での型の表現方法を細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-125">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="d1e18-126">これに対し、<xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.DataContractAttribute>、および <xref:System.Runtime.Serialization.DataMemberAttribute> の場合、XML での型の表現方法にはほとんど自由度がありません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-126">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="d1e18-127">指定できるのは、名前空間と、型やフィールド、プロパティを XML で表す名前、フィールドやプロパティの XML における並び順だけです。</span><span class="sxs-lookup"><span data-stu-id="d1e18-127">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>

  ```csharp
  [DataContract(
  Namespace="urn:Contoso:2006:January:29",
  Name="LineItem")]
  public class LineItem
  {
        [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
        public string itemNumber;
        [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
        public decimal quantity;
        [DataMember(Name="Price",IsRequired=false,Order = 2)]
        public decimal unitPrice;
  }
  ```

  <span data-ttu-id="d1e18-128">上記以外の事項は、<xref:System.Runtime.Serialization.DataContractSerializer> に固定で組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-128">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

- <span data-ttu-id="d1e18-129"><xref:System.Runtime.Serialization.DataContractSerializer> の場合、型の XML での表現方法に自由度が小さく、したがってシリアル化のプロセスがあらかじめ大部分予測できるので、最適化が容易です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-129">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="d1e18-130"><xref:System.Runtime.Serialization.DataContractSerializer> を使えば、性能が約 10% 向上するという現実的な利点があります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-130">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>

- <span data-ttu-id="d1e18-131"><xref:System.Xml.Serialization.XmlSerializer> を使用する方法では、どのフィールドやプロパティを XML にシリアル化するかを属性で指定することはできませんが、<xref:System.Runtime.Serialization.DataMemberAttribute> の場合は <xref:System.Runtime.Serialization.DataContractSerializer> 属性で明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-131">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="d1e18-132">このように、データ コントラクトとは、アプリケーションとの間でやり取りするデータ構造を明示した契約であると言うことができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-132">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>

- <span data-ttu-id="d1e18-133"><xref:System.Xml.Serialization.XmlSerializer> で XML 形式に変換できるのは、.NET オブジェクトのパブリック メンバーに限ります。一方 <xref:System.Runtime.Serialization.DataContractSerializer> は、アクセス修飾子にかかわらず、どのメンバーでも変換可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-133">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>

- <span data-ttu-id="d1e18-134"><xref:System.Runtime.Serialization.DataContractSerializer> の場合、パブリックでないメンバーも XML に変換できるため、シリアル化できる .NET 型についての制約が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-134">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="d1e18-135">特に、<xref:System.Collections.Hashtable> など、<xref:System.Collections.IDictionary> インターフェイスを実装した型が変換可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-135">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="d1e18-136"><xref:System.Runtime.Serialization.DataContractSerializer> はさらに、既存の .NET 型のインスタンスを XML にシリアル化する場合でも、型定義を変更したり、ラッパーを定義したりする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-136">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>

- <span data-ttu-id="d1e18-137"><xref:System.Runtime.Serialization.DataContractSerializer> はパブリックでないメンバーも変換できるため、完全に信頼できるコードからしか実行できないようになっています。<xref:System.Xml.Serialization.XmlSerializer> にはそのような制約がありません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-137">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="d1e18-138">完全信頼コードアクセス許可は、コードを実行している資格情報を使用してアクセスできる、コンピューター上のすべてのリソースへの完全なアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-138">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="d1e18-139">このオプションは、完全に信頼されたコードがコンピューター上のすべてのリソースにアクセスするため、注意して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-139">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>

- <span data-ttu-id="d1e18-140"><xref:System.Runtime.Serialization.DataContractSerializer> にはバージョン管理の機能がいくつか組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-140">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>

  - <span data-ttu-id="d1e18-141"><xref:System.Runtime.Serialization.DataMemberAttribute> には <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> プロパティがあります。旧バージョンにはなかったメンバーを追加した場合に、そのプロパティを false とすれば、当該データ コントラクトの新バージョンを扱うアプリケーションが、旧バージョンのデータも扱えるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-141">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>

  - <span data-ttu-id="d1e18-142">データ コントラクトに <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装すると、<xref:System.Runtime.Serialization.DataContractSerializer> は、新バージョンのデータ コントラクトで定義されたメンバーを、旧バージョンのコントラクトを扱うアプリケーション経由で受け渡しできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-142">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>

<span data-ttu-id="d1e18-143">以上のようにさまざまな違いがありますが、<xref:System.Xml.Serialization.XmlSerializer> で既定の設定を使用して型をシリアル化したものは、XML の名前空間を明示的に定義してあれば、<xref:System.Runtime.Serialization.DataContractSerializer> で型をシリアル化したものと意味的に同等です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-143">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="d1e18-144">次のクラスは、両方のシリアライザーで使用する属性を持っており、とによって意味的に同一の XML に変換され <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-144">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

<span data-ttu-id="d1e18-145">Windows ソフトウェア開発キット (SDK) には、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)と呼ばれるコマンドラインツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-145">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="d1e18-146">ASP.NET ウェブサービスで使用される xsd.exe ツールと同様に、Svcutil.exe は XML スキーマから .NET データ型の定義を生成できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-146">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="d1e18-147"><xref:System.Runtime.Serialization.DataContractSerializer> が XML スキーマで定義された形式の XML を出力できる場合、型はデータ コントラクトの形に変換されます。そうでなければ、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-147">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d1e18-148">また Svcutil.exe は、スイッチを使用してデータコントラクトから XML スキーマを生成することもでき `dataContractOnly` ます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-148">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>

> [!NOTE]
> <span data-ttu-id="d1e18-149">ASP.NET ウェブサービスではを使用しますが、 <xref:System.Xml.Serialization.XmlSerializer> wcf ASP.NET 互換モードでは wcf サービスが ASP.NET Web サービスの動作を模倣しますが、ASP.NET compatibility オプションでは、を使用するように制限されていません <xref:System.Xml.Serialization.XmlSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="d1e18-149">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d1e18-150">必要であれば ASP.NET 互換モードでも <xref:System.Runtime.Serialization.DataContractSerializer> も使えるようになっています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-150">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>

## <a name="service-development"></a><span data-ttu-id="d1e18-151">サービスの開発</span><span class="sxs-lookup"><span data-stu-id="d1e18-151">Service Development</span></span>

<span data-ttu-id="d1e18-152">ASP.NET を使用してサービスを開発する場合、通常は <xref:System.Web.Services.WebService> 属性をクラスに追加し、<xref:System.Web.Services.WebMethodAttribute> を当該クラスのサービスに対する操作メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-152">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="d1e18-153">ASP.NET 2.0 では、<xref:System.Web.Services.WebService> 属性や <xref:System.Web.Services.WebMethodAttribute> 属性をクラスではなくインターフェイスに追加し、そのインターフェイスを実装するクラスを記述する、という方法も使えるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d1e18-153">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

<span data-ttu-id="d1e18-154"><xref:System.Web.Services.WebService> 属性を持つインターフェイスは、サービスによって実行される操作のコントラクトを構成し、またそれをさまざまなクラスで再利用することによって、同じコントラクトをさまざまな方法で実装できるので、このオプションの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d1e18-154">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>

<span data-ttu-id="d1e18-155">WCF サービスは、1つまたは複数の WCF エンドポイントを定義することによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-155">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="d1e18-156">エンドポイントは、アドレス、バインディング、サービス コントラクトで定義します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-156">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="d1e18-157">アドレスとは、サービスが配備された場所のことです。</span><span class="sxs-lookup"><span data-stu-id="d1e18-157">The address defines where the service is located.</span></span> <span data-ttu-id="d1e18-158">バインディングはサービスとの通信方法を表します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-158">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="d1e18-159">サービス コントラクトとは、サービスが実行できる操作の定義のことです。</span><span class="sxs-lookup"><span data-stu-id="d1e18-159">The service contract defines the operations that the service can perform.</span></span>

<span data-ttu-id="d1e18-160">サービス コントラクトは通常、インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> および <xref:System.ServiceModel.OperationContractAttribute> を追加して定義します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-160">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<span data-ttu-id="d1e18-161">は、 <xref:System.ServiceModel.ServiceContractAttribute> インターフェイスが WCF サービスコントラクトを定義することを指定します。また、は、 <xref:System.ServiceModel.OperationContractAttribute> インターフェイスのメソッドがサービスコントラクトの操作を定義しているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-161">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>

<span data-ttu-id="d1e18-162">このようにして定義されたサービス コントラクトをクラスとして実装します。サービス コントラクトを定義するインターフェイスを実装するクラスという形で記述します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-162">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="d1e18-163">サービスコントラクトを実装するクラスは、WCF ではサービス型と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-163">A class that implements a service contract is referred to as a service type in WCF.</span></span>

<span data-ttu-id="d1e18-164">次に、アドレスとバインディングを、サービス型と関連付けます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-164">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="d1e18-165">通常は、ファイルを直接編集するか、WCF に用意されている構成エディターを使用して、構成ファイルで行います。</span><span class="sxs-lookup"><span data-stu-id="d1e18-165">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="d1e18-166">構成ファイルの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-166">Here is an example of a configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

<span data-ttu-id="d1e18-167">バインディングは、アプリケーションとの通信に使う一連のプロトコルを表します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-167">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="d1e18-168">一般的なシステム指定のバインディングを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-168">The following table lists the system-provided bindings that represent common options.</span></span>

|<span data-ttu-id="d1e18-169">名前</span><span class="sxs-lookup"><span data-stu-id="d1e18-169">Name</span></span>|<span data-ttu-id="d1e18-170">目的</span><span class="sxs-lookup"><span data-stu-id="d1e18-170">Purpose</span></span>|
|----------|-------------|
|<span data-ttu-id="d1e18-171">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d1e18-171">BasicHttpBinding</span></span>|<span data-ttu-id="d1e18-172">WS-BasicProfile 1.1 および Basic Security Profile 1.0 に対応した Web サービスやクライアントとの相互運用性。</span><span class="sxs-lookup"><span data-stu-id="d1e18-172">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|
|<span data-ttu-id="d1e18-173">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d1e18-173">WSHttpBinding</span></span>|<span data-ttu-id="d1e18-174">HTTP 上の WS-\* プロトコルに対応した Web サービスやクライアントとの相互運用性。</span><span class="sxs-lookup"><span data-stu-id="d1e18-174">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|
|<span data-ttu-id="d1e18-175">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d1e18-175">WSDualHttpBinding</span></span>|<span data-ttu-id="d1e18-176">双方向 HTTP 通信。最初のメッセージの受信者は送信元に直接は応答せず、代わりに、WS-\* プロトコルに準拠した HTTP で、ある期間にわたって任意の数の応答を送信することができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-176">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|
|<span data-ttu-id="d1e18-177">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="d1e18-177">WSFederationBinding</span></span>|<span data-ttu-id="d1e18-178">HTTP 通信。サービスのリソースに対するアクセスを、明示的に指定された資格情報プロバイダーによって発行された証明書に基づいて制御することができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-178">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|
|<span data-ttu-id="d1e18-179">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="d1e18-179">NetTcpBinding</span></span>|<span data-ttu-id="d1e18-180">ネットワーク経由での WCF ソフトウェアエンティティ間の安全で信頼性の高い高パフォーマンスな通信。</span><span class="sxs-lookup"><span data-stu-id="d1e18-180">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|
|<span data-ttu-id="d1e18-181">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="d1e18-181">NetNamedPipeBinding</span></span>|<span data-ttu-id="d1e18-182">同じコンピューター上の WCF ソフトウェアエンティティ間で、セキュリティで保護された信頼性の高い高パフォーマンスの通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-182">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|
|<span data-ttu-id="d1e18-183">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="d1e18-183">NetMsmqBinding</span></span>|<span data-ttu-id="d1e18-184">MSMQ を使用した WCF ソフトウェアエンティティ間の通信。</span><span class="sxs-lookup"><span data-stu-id="d1e18-184">Communication between WCF software entities by using MSMQ.</span></span>|
|<span data-ttu-id="d1e18-185">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="d1e18-185">MsmqIntegrationBinding</span></span>|<span data-ttu-id="d1e18-186">MSMQ を使用した WCF ソフトウェアエンティティと別のソフトウェアエンティティ間の通信。</span><span class="sxs-lookup"><span data-stu-id="d1e18-186">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|
|<span data-ttu-id="d1e18-187">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="d1e18-187">NetPeerTcpBinding</span></span>|<span data-ttu-id="d1e18-188">Windows ピアツーピアネットワークを使用した WCF ソフトウェアエンティティ間の通信。</span><span class="sxs-lookup"><span data-stu-id="d1e18-188">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|

<span data-ttu-id="d1e18-189">システム指定のバインディングである <xref:System.ServiceModel.BasicHttpBinding> には、ASP.NET Web サービスが対応している一連のプロトコルが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-189">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>

<span data-ttu-id="d1e18-190">WCF アプリケーションのカスタムバインドは、WCF が個々のプロトコルを実装するために使用するバインド要素クラスのコレクションとして簡単に定義できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-190">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="d1e18-191">追加のプロトコルを表す、新しいバインド要素を記述することも可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-191">New binding elements can be written to represent additional protocols.</span></span>

<span data-ttu-id="d1e18-192">サービス型の内部的な動作は、動作を表すクラス群のプロパティで調整できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-192">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="d1e18-193">次の例で、<xref:System.ServiceModel.ServiceBehaviorAttribute> クラスは、サービス型がマルチスレッド処理されることを指定しています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-193">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple)]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<span data-ttu-id="d1e18-194"><xref:System.ServiceModel.ServiceBehaviorAttribute> など、属性として定義された動作もあります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-194">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="d1e18-195">これに対し、管理者がプロパティを設定できる動作は、アプリケーションの構成ファイルで変更することができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-195">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>

<span data-ttu-id="d1e18-196">サービス型のプログラムの記述には、多くの場合 <xref:System.ServiceModel.OperationContext> クラスを使います。</span><span class="sxs-lookup"><span data-stu-id="d1e18-196">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="d1e18-197">静的プロパティである <xref:System.ServiceModel.OperationContext.Current%2A> を介して、実行コンテキストに関する情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-197">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="d1e18-198"><xref:System.ServiceModel.OperationContext> の使い方は、<xref:System.Web.HttpContext> クラスや <xref:System.EnterpriseServices.ContextUtil> クラスと同様です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-198"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>

## <a name="hosting"></a><span data-ttu-id="d1e18-199">Hosting</span><span class="sxs-lookup"><span data-stu-id="d1e18-199">Hosting</span></span>

<span data-ttu-id="d1e18-200">ASP.NET Web サービスは、コンパイルしてクラス ライブラリ アセンブリの形になっています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-200">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="d1e18-201">サービス ファイルという、拡張子が .asmx のファイルの `@ WebService` ディレクティブに、サービスの実行コードが組み込まれたクラスと、これを収容するアセンブリが定義されています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-201">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

<span data-ttu-id="d1e18-202">サービス ファイルをインターネット インフォメーション サービス (IIS) の ASP.NET アプリケーション ルート、アセンブリをアプリケーション ルートのサブディレクトリ \bin 以下にコピーすると、</span><span class="sxs-lookup"><span data-stu-id="d1e18-202">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="d1e18-203">このサービス ファイルの URL (Uniform Resource Locator) でアプリケーションにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-203">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>

<span data-ttu-id="d1e18-204">WCF サービスは、iis 5.1 または6.0 内、IIS 7.0 の一部として提供される Windows プロセスアクティブ化サービス (WAS)、および .NET アプリケーション内で簡単にホストできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-204">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="d1e18-205">ただし IIS 5.1/6.0 の場合、通信トランスポート プロトコルは HTTP に限ります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-205">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>

<span data-ttu-id="d1e18-206">IIS 5.1/6.0 または WAS 上でサービスをホストする手順を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-206">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>

1. <span data-ttu-id="d1e18-207">サービス型をコンパイルしてクラス ライブラリ アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-207">Compile the service type into a class library assembly.</span></span>

2. <span data-ttu-id="d1e18-208">拡張子を .svc としたサービス ファイルを作り、サービス型を `@ ServiceHost` ディレクティブで次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-208">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. <span data-ttu-id="d1e18-209">サービス ファイルを仮想ディレクトリにコピーし、アセンブリをその仮想ディレクトリの \bin サブディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d1e18-209">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>

4. <span data-ttu-id="d1e18-210">構成ファイルを仮想ディレクトリに、Web.config という名前でコピーします。</span><span class="sxs-lookup"><span data-stu-id="d1e18-210">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>

<span data-ttu-id="d1e18-211">するとアプリケーションには、アプリケーション ルートに置いたサービス ファイルの URL でアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-211">The application is then accessible by using the URL of the service file in the application root.</span></span>

<span data-ttu-id="d1e18-212">.NET アプリケーション内で WCF サービスをホストするには、アプリケーションによって参照されるクラスライブラリアセンブリにサービスの種類をコンパイルし、クラスを使用してサービスをホストするようにアプリケーションをプログラミングし <xref:System.ServiceModel.ServiceHost> ます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-212">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="d1e18-213">サービスを管理する基本的なプログラムの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-213">The following is an example of the basic programming required:</span></span>

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

<span data-ttu-id="d1e18-214">この例では <xref:System.ServiceModel.ServiceHost> の構築時にトランスポート プロトコルに対してアドレスを指定しています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-214">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d1e18-215">このアドレスをベース アドレスと呼びます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-215">These addresses are referred to as base addresses.</span></span>

<span data-ttu-id="d1e18-216">WCF サービスのエンドポイントに対して指定されるアドレスは、エンドポイントのホストのベースアドレスを基準とするアドレスです。</span><span class="sxs-lookup"><span data-stu-id="d1e18-216">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="d1e18-217">ホストではトランスポート プロトコルごとに 1 つベース アドレスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-217">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="d1e18-218">上記の構成ファイルの構成例では、エンドポイントに対して選択された <xref:System.ServiceModel.BasicHttpBinding> はトランスポート プロトコルとして HTTP を使用しているので、エンドポイント `EchoService` のアドレスは、HTTP に対して設定されたベース アドレスを基準としたものになります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-218">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="d1e18-219">前の例のホストの場合、HTTP ベースアドレスはに `http://www.contoso.com:8000/` なります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-219">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="d1e18-220">なお、IIS や WAS 上でホストされているサービスの場合、ベース アドレスはサービス ファイルの URL になります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-220">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>

<span data-ttu-id="d1e18-221">WCF ASP.NET 互換モードオプションを使用するには、IIS または WAS でホストされていて、トランスポートプロトコルとしてのみ HTTP で構成されているサービスのみを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-221">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="d1e18-222">ASP.NET 互換モードは、次の 2 つの手順で切り替えます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-222">Turning that option on requires the following steps.</span></span>

1. <span data-ttu-id="d1e18-223">プログラムの開発者は、サービス型に <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 属性を追加し、ASP.NET 互換モードに切り替えることができる、または切り替えることが必須である旨の指定をしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-223">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. <span data-ttu-id="d1e18-224">管理者は、アプリケーションが ASP.NET 互換モードで動作するよう、次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-224">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="d1e18-225">また、.svc ではなくサービスファイルの拡張子として .asmx を使用するように、WCF アプリケーションを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-225">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    <span data-ttu-id="d1e18-226">このオプションを使用すると、WCF を使用するようにサービスを変更するときに、.asmx サービスファイルの Url を使用するように構成されているクライアントを変更する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-226">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>

## <a name="client-development"></a><span data-ttu-id="d1e18-227">クライアント開発</span><span class="sxs-lookup"><span data-stu-id="d1e18-227">Client Development</span></span>

<span data-ttu-id="d1e18-228">ASP.NET Web サービスのクライアントの開発にはコマンド ライン ツール WSDL.exe を使用します。.asmx ファイルの URL を入力として指定します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-228">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="d1e18-229">WCF によって提供される対応ツールは、 [ServiceModel Metadata Utility tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-229">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="d1e18-230">これにより、サービスコントラクトの定義と WCF クライアントクラスの定義を含むコードモジュールが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-230">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="d1e18-231">また、サービスのアドレスとバインディングを指定して、構成ファイルを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-231">It also generates a configuration file with the address and binding of the service.</span></span>

<span data-ttu-id="d1e18-232">リモート サービスのクライアントを開発する場合、通常は、非同期パターンに従ってプログラムを記述するようお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d1e18-232">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="d1e18-233">WSDL.exe ツールは、特段の指定をしなくても、同期パターンと非同期パターンを使ったコードをそれぞれ生成します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-233">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="d1e18-234">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)によって生成されるコードは、どちらのパターンでも提供できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-234">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="d1e18-235">特に指定しなければ同期パターン用です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-235">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="d1e18-236">`/async` スイッチを指定して実行すれば、生成されるコードは非同期パターン用になります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-236">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>

<span data-ttu-id="d1e18-237">ASP によって生成される WCF クライアントクラスに名前があることは保証されません。既定では、NET の WSDL.exe ツールは、Svcutil.exe ツールによって生成される WCF クライアントクラスの名前と一致します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-237">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="d1e18-238">特に、<xref:System.Xml.Serialization.XmlSerializer> でシリアル化したクラスのプロパティ名は、Svcutil.exe で生成した場合 "Property" という接頭辞が付きますが、WSDL.exe の場合はそうなりません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-238">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>

## <a name="message-representation"></a><span data-ttu-id="d1e18-239">メッセージ表現</span><span class="sxs-lookup"><span data-stu-id="d1e18-239">Message Representation</span></span>

<span data-ttu-id="d1e18-240">ASP.NET Web サービスとやり取りする SOAP メッセージのヘッダーはカスタマイズ可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-240">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="d1e18-241"><xref:System.Web.Services.Protocols.SoapHeader> の派生クラスでヘッダーの構造を定義し、<xref:System.Web.Services.Protocols.SoapHeaderAttribute> でヘッダーが存在することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-241">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

<span data-ttu-id="d1e18-242">WCF には、 <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> サービスによって送受信される SOAP メッセージの構造を記述するための、、、およびの属性が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-242">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

<span data-ttu-id="d1e18-243">この構文でメッセージ構造を明示的に記述できますが、ASP.NET Web サービスのコードからメッセージ構造を導くことも可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-243">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="d1e18-244">また、ASP.NET 構文では、メッセージヘッダーは、前の例のプロパティのように、サービスのプロパティとして表され `ProtocolHeader` ます。一方、WCF 構文では、メッセージのプロパティとしてより正確に表されます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-244">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="d1e18-245">また、WCF では、メッセージヘッダーをエンドポイントの構成に追加できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-245">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

<span data-ttu-id="d1e18-246">この方法では、クライアントやサービスのコード内で、基盤となるプロトコル ヘッダーを参照しなくても済みます。エンドポイントが適切に構成されているので、ヘッダーがメッセージ中に取り込まれるからです。</span><span class="sxs-lookup"><span data-stu-id="d1e18-246">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>

## <a name="service-description"></a><span data-ttu-id="d1e18-247">サービスの説明</span><span class="sxs-lookup"><span data-stu-id="d1e18-247">Service Description</span></span>

<span data-ttu-id="d1e18-248">WSDL で記述したクエリを HTTP GET 要求として発行して、ASP.NET Web サービスの .asmx ファイルを取得しようとすると、ASP.NET は WSDL によるサービス記述を生成し、</span><span class="sxs-lookup"><span data-stu-id="d1e18-248">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="d1e18-249">要求に対する応答として返します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-249">It returns that WSDL as the response to the request.</span></span>

<span data-ttu-id="d1e18-250">ASP.NET 2.0 では、サービスが Web Services-Interoperability Organization (WS-I) の Basic Profile 1.1 に準拠していることを検証し、その旨を WSDL による記述に追加できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d1e18-250">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="d1e18-251">この処理には、`ConformsTo` 属性の `EmitConformanceClaims` および <xref:System.Web.Services.WebServiceBindingAttribute> パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-251">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

<span data-ttu-id="d1e18-252">ASP.NET が WSDL で生成したサービス記述はカスタマイズ可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-252">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="d1e18-253"><xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> の派生クラスを作成し、WSDL による記述に項目を追加する、という形でカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="d1e18-253">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>

<span data-ttu-id="d1e18-254">IIS 51、6.0、または WAS でホストされている HTTP エンドポイントを使用して、WCF サービスの .svc ファイルのクエリ WSDL を使用して HTTP GET 要求を発行すると、WCF は WSDL と応答してサービスを記述します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-254">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="d1e18-255">httpGetEnabled が true に設定されている場合は、WSDL で記述したクエリを HTTP GET 要求として、.NET アプリケーション上でホストされているサービスの HTTP ベース アドレスに発行しても同じ効力があります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-255">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>

<span data-ttu-id="d1e18-256">ただし、WCF では、サービスを記述するために生成される WSDL を使用した WS-MetadataExchange 要求にも応答します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-256">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="d1e18-257">ASP.NET Web サービスには、WS-MetadataExchange 要求に応答する機能がありません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-257">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>

<span data-ttu-id="d1e18-258">WCF によって生成される WSDL は、広範囲にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-258">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="d1e18-259"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスには、WSDL による記述をカスタマイズするための機能がいくつか組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-259">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="d1e18-260">WCF は、WSDL を生成しないように構成することもできますが、特定の URL で静的 WSDL ファイルを使用するように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-260">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a><span data-ttu-id="d1e18-261">例外処理</span><span class="sxs-lookup"><span data-stu-id="d1e18-261">Exception Handling</span></span>

<span data-ttu-id="d1e18-262">ASP.NET Web サービスでは、処理できない例外が発生すると、SOAP エラーとしてクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-262">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="d1e18-263">また、<xref:System.Web.Services.Protocols.SoapException> クラスのインスタンスを明示的にスローして、クライアント側に SOAP エラーの詳しい状況を通知し、より適切に管理させることも可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-263">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>

<span data-ttu-id="d1e18-264">WCF サービスでは、ハンドルされない例外が SOAP エラーとしてクライアントに返されないため、例外によって機密情報が誤って公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-264">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="d1e18-265">ただしデバッグ目的で、このような例外をクライアントに返すように設定することは可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-265">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>

<span data-ttu-id="d1e18-266">SOAP エラーをクライアントに返す場合、データ コントラクト型を汎用型 <xref:System.ServiceModel.FaultException%601> のインスタンスとしてキャストし、これをスローする方法が使えます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-266">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="d1e18-267">また、操作に <xref:System.ServiceModel.FaultContractAttribute> 属性を追加して、操作で生じうるエラーを指定する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-267">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

<span data-ttu-id="d1e18-268">これにより、サービスで発生する可能性のあるエラーが WSDL の形で公開されます。クライアント側の開発者は、当該操作によりどのようなエラーが生じうるかをあらかじめ予測し、catch ブロック内に適切な処理を組み込んでおくことができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-268">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a><span data-ttu-id="d1e18-269">状態管理</span><span class="sxs-lookup"><span data-stu-id="d1e18-269">State Management</span></span>

<span data-ttu-id="d1e18-270">ASP.NET Web サービスの実装には <xref:System.Web.Services.WebService> の派生クラスを使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-270">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

<span data-ttu-id="d1e18-271">この場合、基本クラス <xref:System.Web.Services.WebService> に定義された Context プロパティを使って、<xref:System.Web.HttpContext> オブジェクトにアクセスすることになります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-271">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="d1e18-272"><xref:System.Web.HttpContext> オブジェクトには、アプリケーションやセッションの状態情報をそれぞれ更新、取得する、Application プロパティ、Session プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-272">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>

<span data-ttu-id="d1e18-273">ASP.NET では、<xref:System.Web.HttpContext> の Session プロパティでアクセスするセッション状態情報の、実際の格納場所を細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-273">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="d1e18-274">格納場所としては、クッキー内、データベース内、稼動中のサーバーのメモリ上、状態管理用の特別なサーバーのメモリ上があり、</span><span class="sxs-lookup"><span data-stu-id="d1e18-274">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="d1e18-275">サービスの構成ファイルで指定します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-275">The choice is made in the service’s configuration file.</span></span>

<span data-ttu-id="d1e18-276">WCF には、状態管理のための拡張可能なオブジェクトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-276">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="d1e18-277">いずれも <xref:System.ServiceModel.IExtensibleObject%601> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-277">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="d1e18-278">中でも重要な拡張可能オブジェクトは、<xref:System.ServiceModel.ServiceHostBase> および <xref:System.ServiceModel.InstanceContext> です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-278">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="d1e18-279">`ServiceHostBase` を使用すると、同一ホスト上の全サービス型のあらゆるインスタンスからアクセスできる状態を管理できます。一方、`InstanceContext` を使用すると、同じサービス型のインスタンス内で実行されるコードからアクセスできる状態を管理できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-279">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>

<span data-ttu-id="d1e18-280">ここで、サービス型には、 `TradingSystem` <xref:System.ServiceModel.ServiceBehaviorAttribute> 同じ WCF クライアントインスタンスからのすべての呼び出しがサービス型の同じインスタンスにルーティングされることを指定するがあります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-280">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

<span data-ttu-id="d1e18-281">次のクラス `DealData` に定義されている状態には、同じサービス型のインスタンス内で実行されるどのコードからでもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-281">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

<span data-ttu-id="d1e18-282">サービス コントラクトの操作のいずれかを実装するサービス型のコードでは、状態オブジェクト `DealData` を、当該サービス型の現在のインスタンスに関する状態として追加することができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-282">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

<span data-ttu-id="d1e18-283">この状態オブジェクトは、サービス コントラクトの他の操作を実装するコードから取得、更新できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-283">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

<span data-ttu-id="d1e18-284">ASP.NET では、クラス内の状態情報を実際に格納する場所を制御でき <xref:System.Web.HttpContext> ますが、WCF は少なくとも最初のバージョンでは、拡張可能なオブジェクトが格納される場所を制御できません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-284">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="d1e18-285">これは、WCF サービスの ASP.NET 互換モードを選択するための非常に最良の理由です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-285">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="d1e18-286">このような制御が不可欠な応用の場合、ASP.NET 互換モードにすれば、ASP.NET と同様に <xref:System.Web.HttpContext> クラスの機能を活用できるばかりでなく、<xref:System.Web.HttpContext> クラスで管理する状態情報の実際の格納場所も制御できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-286">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>

## <a name="security"></a><span data-ttu-id="d1e18-287">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d1e18-287">Security</span></span>

<span data-ttu-id="d1e18-288">ASP.NET Web サービスのセキュリティ保全の手順は、IIS アプリケーションのセキュリティ保全の手順と同じです。</span><span class="sxs-lookup"><span data-stu-id="d1e18-288">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="d1e18-289">WCF アプリケーションは IIS 内だけでなく、.NET 実行可能ファイル内でもホストできるため、WCF アプリケーションをセキュリティで保護するためのオプションは、IIS の機能とは独立したものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-289">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="d1e18-290">ただし、ASP.NET Web サービスに提供されている機能は、ASP.NET 互換モードで実行されている WCF サービスでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-290">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>

### <a name="security-authentication"></a><span data-ttu-id="d1e18-291">セキュリティ : 認証</span><span class="sxs-lookup"><span data-stu-id="d1e18-291">Security: Authentication</span></span>

<span data-ttu-id="d1e18-292">IIS にはアプリケーションへのアクセス制御機能が組み込まれており、匿名アクセスの他、Windows 認証、ダイジェスト認証、基本認証、.NET パスポート認証など、さまざまな認証モードを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-292">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="d1e18-293">Windows 認証は、ASP.NET Web サービスへのアクセス制御に使えます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-293">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="d1e18-294">ただし、WCF アプリケーションが IIS 内でホストされている場合、アプリケーションへの匿名アクセスを許可するように IIS を構成する必要があります。これにより、他のさまざまなオプション間で Windows 認証をサポートする WCF 自体で認証を管理できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-294">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="d1e18-295">他の認証方法としては、ユーザー名トークン、X.509 証明書、SAML トークン、CardSpace カードなどが組み込まれていますが、独自の認証機構を定義することも可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-295">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>

### <a name="security-impersonation"></a><span data-ttu-id="d1e18-296">セキュリティ : 偽装</span><span class="sxs-lookup"><span data-stu-id="d1e18-296">Security: Impersonation</span></span>

<span data-ttu-id="d1e18-297">ASP.NET Web サービスは ASP.NET の ID 要素を使用して、あるユーザーに偽装することができます。あらかじめ設定した特定のユーザーでなくても、要求に資格情報が添えられていれば、その要求元ユーザーに偽装できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-297">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="d1e18-298">この要素を使用して、ASP.NET 互換モードで実行されている WCF アプリケーションで偽装を構成できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-298">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>

<span data-ttu-id="d1e18-299">WCF 構成システムには、偽装する特定のユーザーを指定するための独自の id 要素が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-299">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="d1e18-300">また、WCF クライアントとサービスは、権限借用のために個別に構成できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-300">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="d1e18-301">クライアント側では、要求を送信する現在のユーザーに偽装する構成が可能です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-301">Clients can be configured to impersonate the current user when they transmit requests.</span></span>

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

<span data-ttu-id="d1e18-302">サービス側では、現在の要求と共に提供された資格情報のユーザーに偽装するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-302">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="d1e18-303">セキュリティ : アクセス制御リストによる承認</span><span class="sxs-lookup"><span data-stu-id="d1e18-303">Security: Authorization using Access Control Lists</span></span>

<span data-ttu-id="d1e18-304">アクセス制御リスト (ACL) を使って .asmx ファイルへのアクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-304">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="d1e18-305">ただし、ASP.NET 互換モードの場合を除き、WCF .svc ファイルの Acl は無視されます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-305">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>

### <a name="security-role-based-authorization"></a><span data-ttu-id="d1e18-306">セキュリティ : ロール ベースの承認</span><span class="sxs-lookup"><span data-stu-id="d1e18-306">Security: Role-based Authorization</span></span>

<span data-ttu-id="d1e18-307">IIS の Windows 認証オプションを、ASP.NET 構成言語の承認要素と組み合わせて使用すると、ASP.NET Web サービスに対し、各ユーザーが属する Windows グループに基づくロール ベースの承認機構を提供できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-307">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="d1e18-308">ASP.NET 2.0 には、より汎用的なロール ベースの承認機構である、ロール プロバイダーが導入されました。</span><span class="sxs-lookup"><span data-stu-id="d1e18-308">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>

<span data-ttu-id="d1e18-309">ロール プロバイダーとは、ユーザーが割り当てられたロールに関する問い合わせを行う、基本インターフェイスを実装したクラス群です。各ロール プロバイダーには、さまざまな情報源から必要な情報を取得する手段が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-309">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="d1e18-310">ASP.NET 2.0 には、Microsoft SQL Server データベースからロールの割り当てを検索できるロール プロバイダーと、Windows Server 2003 承認マネージャーから検索できるロール プロバイダーがあります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-310">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>

<span data-ttu-id="d1e18-311">ロールプロバイダーのメカニズムは、WCF アプリケーションを含む任意の .NET アプリケーションの ASP.NET とは無関係に使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-311">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="d1e18-312">次の WCF アプリケーションのサンプル構成では、ASP.NET ロールプロバイダーの使用方法が、で選択されたオプションであることを示し <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-312">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a><span data-ttu-id="d1e18-313">セキュリティ : クレーム ベースの承認</span><span class="sxs-lookup"><span data-stu-id="d1e18-313">Security: Claims-based Authorization</span></span>

<span data-ttu-id="d1e18-314">WCF の最も重要なイノベーションの1つは、要求に基づいて保護されたリソースへのアクセスの承認を完全にサポートすることです。</span><span class="sxs-lookup"><span data-stu-id="d1e18-314">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="d1e18-315">クレームは、型、権限、および値で構成されます。たとえば、運転免許証を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="d1e18-315">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="d1e18-316">ここには所持者に関する誕生日などの情報 (ここでいう「クレーム」) が記載されています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-316">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="d1e18-317">つまり、クレームの型は「誕生日」、値は運転者の実際の誕生日です。</span><span class="sxs-lookup"><span data-stu-id="d1e18-317">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="d1e18-318">また、クレームの権限は、所持者がこの値に対してできることを表します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-318">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="d1e18-319">誕生日について言えば、所持者はこの情報を「見る」ことはできますが、「書き換える」ことはできません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-319">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="d1e18-320">クレーム ベースの承認は、ロール ベースの承認を包含する概念です。というのも、ロールはクレームの 1 つの型であると考えることができるからです。</span><span class="sxs-lookup"><span data-stu-id="d1e18-320">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>

<span data-ttu-id="d1e18-321">クレーム ベースの承認では、一連のクレームを操作のアクセス要求と比較し、その結果に応じてアクセスを許可または拒否します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-321">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="d1e18-322">WCF では、のプロパティに値を割り当てることによって、要求ベースの承認を再実行するために使用するクラスを指定でき `ServiceAuthorizationManager` <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-322">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

<span data-ttu-id="d1e18-323">クレーム ベースの承認を行うクラスは、<xref:System.ServiceModel.ServiceAuthorizationManager> を継承し、`AccessCheck()` メソッドだけをオーバーライドして定義します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-323">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="d1e18-324">WCF は、サービスの操作が呼び出されるたびに、そのメソッドを呼び出し、その <xref:System.ServiceModel.OperationContext> プロパティでユーザーのクレームを持つオブジェクトを提供し `ServiceSecurityContext.AuthorizationContext` ます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-324">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="d1e18-325">WCF では、ユーザーに関する認証用に提供されたセキュリティトークンからユーザーに関するクレームをアセンブルする処理を行います。これにより、該当する操作に対して十分な要求があるかどうかを評価するタスクが残ります。</span><span class="sxs-lookup"><span data-stu-id="d1e18-325">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>

<span data-ttu-id="d1e18-326">WCF では、任意の種類のセキュリティトークンからのクレームを自動的にアセンブルすることが非常に重要なイノベーションです。これは、認証メカニズムに関係なく、信頼性の高い要求に基づいてコードを承認するためです。</span><span class="sxs-lookup"><span data-stu-id="d1e18-326">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="d1e18-327">これに対し、ACL やロール ベースの承認は、Windows 認証と密に関連し合っています。</span><span class="sxs-lookup"><span data-stu-id="d1e18-327">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>

### <a name="security-confidentiality"></a><span data-ttu-id="d1e18-328">セキュリティ : 機密性</span><span class="sxs-lookup"><span data-stu-id="d1e18-328">Security: Confidentiality</span></span>

<span data-ttu-id="d1e18-329">ASP.NET Web サービスとの間でやり取りするメッセージの機密性は、トランスポート層で、IIS 上のアプリケーションが Secure Hypertext Transfer Protocol (HTTPS) を使うように構成することによって確保します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-329">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="d1e18-330">IIS 内でホストされている WCF アプリケーションに対しても同じことができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-330">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="d1e18-331">ただし、IIS の外部でホストされている WCF アプリケーションは、セキュリティで保護されたトランスポートプロトコルを使用するように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-331">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="d1e18-332">さらに重要な点として、WS-Security プロトコルを使用して、メッセージを転送する前にセキュリティで保護するように WCF アプリケーションを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-332">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="d1e18-333">メッセージの本体を WS-Security で保護することにより、最終送信先に到達するまでの中継ノードで機密が洩れないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-333">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>

## <a name="globalization"></a><span data-ttu-id="d1e18-334">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="d1e18-334">Globalization</span></span>

<span data-ttu-id="d1e18-335">ASP.NET 構成言語では、個々のサービスごとにカルチャを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d1e18-335">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="d1e18-336">WCF では、ASP.NET 互換モードを除き、この構成設定はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d1e18-336">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="d1e18-337">ASP.NET 互換モードを使用しない WCF サービスをローカライズするには、サービスの種類をカルチャ固有のアセンブリにコンパイルし、カルチャ固有のアセンブリごとにカルチャ固有のエンドポイントを個別に用意します。</span><span class="sxs-lookup"><span data-stu-id="d1e18-337">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1e18-338">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1e18-338">See also</span></span>

- [<span data-ttu-id="d1e18-339">使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較</span><span class="sxs-lookup"><span data-stu-id="d1e18-339">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
