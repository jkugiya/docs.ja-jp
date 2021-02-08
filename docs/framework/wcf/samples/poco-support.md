---
description: 詳細については、「POCO Support」を参照してください。
title: POCO サポート
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 8d44e7a3ebffc6c460a735587ca56990953b2d9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793182"
---
# <a name="poco-support"></a><span data-ttu-id="dad74-103">POCO サポート</span><span class="sxs-lookup"><span data-stu-id="dad74-103">POCO Support</span></span>

<span data-ttu-id="dad74-104">このサンプルでは、マークされていない型 (シリアル化属性が適用されていない型で、POCO (Plain Old CLR Object) 型と呼ばれる場合もあります) のシリアル化のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dad74-104">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="dad74-105">は、 <xref:System.Runtime.Serialization.DataContractSerializer> パラメーターなしのコンストラクターを持つ、すべてのパブリックのマークされていない型のデータコントラクトを推論します。</span><span class="sxs-lookup"><span data-stu-id="dad74-105">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="dad74-106">データ コントラクトを使用すると、サービスと構造化データをやり取りできます。</span><span class="sxs-lookup"><span data-stu-id="dad74-106">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="dad74-107">マークが付いていない型の詳細については、「 [Serializable 型](../feature-details/serializable-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dad74-107">For more information about unmarked types, see [Serializable Types](../feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="dad74-108">このサンプルは [はじめに](getting-started-sample.md)に基づいていますが、プリミティブな数値型ではなく複素数を使用します。</span><span class="sxs-lookup"><span data-stu-id="dad74-108">This sample is based on the [Getting Started](getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="dad74-109">また、属性と属性が使用されない点を除いて、 [基本的なデータコントラクト](basic-data-contract.md) サンプルに似てい <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="dad74-109">It is also similar to the [Basic Data Contract](basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="dad74-110">サービスはインターネット インフォメーション サービス (IIS) によってホストされています。クライアントはコンソール アプリケーション (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="dad74-110">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dad74-111">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dad74-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="dad74-112">`ComplexNumber` クラスは、`ServiceContract` で使用されます。</span><span class="sxs-lookup"><span data-stu-id="dad74-112">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="dad74-113">次のサンプル コードに示すように、`ComplexNumber` 型には、<xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性がありません。</span><span class="sxs-lookup"><span data-stu-id="dad74-113">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="dad74-114">既定では、パブリック プロパティとパブリック フィールドはすべてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="dad74-114">By default, all public properties and fields are serialized.</span></span>  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dad74-115">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="dad74-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dad74-116">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="dad74-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="dad74-117">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="dad74-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="dad74-118">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="dad74-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dad74-119">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="dad74-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dad74-120">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="dad74-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dad74-121">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="dad74-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dad74-122">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="dad74-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="dad74-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="dad74-123">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="dad74-124">シリアル化可能な型</span><span class="sxs-lookup"><span data-stu-id="dad74-124">Serializable Types</span></span>](../feature-details/serializable-types.md)
