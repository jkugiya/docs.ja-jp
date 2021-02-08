---
description: 詳細については、「サービスコントラクトでのデータ転送の指定」を参照してください。
title: サービス コントラクトでのデータ転送の指定
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 672d2127af95847c0a085a8ca1c358f2a8440dee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793429"
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="e8f2c-103">サービス コントラクトでのデータ転送の指定</span><span class="sxs-lookup"><span data-stu-id="e8f2c-103">Specifying Data Transfer in Service Contracts</span></span>

<span data-ttu-id="e8f2c-104">Windows Communication Foundation (WCF) は、メッセージングインフラストラクチャと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-104">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="e8f2c-105">サービス操作では、メッセージを受信し、それらのメッセージを処理し、送信することができます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-105">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="e8f2c-106">メッセージは、操作コントラクトを使用して記述されます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-106">Messages are described using operation contracts.</span></span> <span data-ttu-id="e8f2c-107">たとえば、次のようなコントラクトがあるとします。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-107">For example, consider the following contract.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 <span data-ttu-id="e8f2c-108">この場合、`GetAirfare` 操作では、`fromCity` と `toCity` に関する情報を含むメッセージを受け入れ、数値を含むメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-108">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="e8f2c-109">ここでは、操作コントラクトでメッセージを記述するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-109">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="e8f2c-110">パラメーターを使用したメッセージの記述</span><span class="sxs-lookup"><span data-stu-id="e8f2c-110">Describing Messages by Using Parameters</span></span>  

 <span data-ttu-id="e8f2c-111">メッセージを記述する最も簡単な方法は、パラメーター リストと戻り値を使用することです。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-111">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="e8f2c-112">前の例では、`fromCity` と `toCity` の 2 つの文字列パラメーターを使用して要求メッセージを記述し、float 型の戻り値を使用して応答メッセージを記述しました。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-112">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="e8f2c-113">戻り値だけでは応答メッセージを記述できない場合は、out パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-113">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="e8f2c-114">たとえば、次の操作は、`fromCity` と `toCity` を要求メッセージに含め、数値と通貨を応答メッセージに含めます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-114">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="e8f2c-115">また、参照パラメーターを使用すると、要求メッセージと応答メッセージの両方のパラメーター部分を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-115">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="e8f2c-116">パラメーターは、シリアル化 (XML への変換) が可能な型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-116">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="e8f2c-117">既定では、WCF はクラスと呼ばれるコンポーネントを使用して、 <xref:System.Runtime.Serialization.DataContractSerializer> この変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-117">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="e8f2c-118">ほとんどのプリミティブ型 (`int`、`string`、`float`、`DateTime` など) がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-118">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="e8f2c-119">ユーザー定義型には、通常、データ コントラクトが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-119">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="e8f2c-120">詳細については、「 [データコントラクトの使用](using-data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-120">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 <span data-ttu-id="e8f2c-121">場合によっては、使用する型のシリアル化に `DataContractSerializer` が適さないことがあります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-121">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="e8f2c-122">WCF では、別のシリアル化エンジンであるをサポートしてい <xref:System.Xml.Serialization.XmlSerializer> ます。これは、パラメーターをシリアル化するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-122">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="e8f2c-123"><xref:System.Xml.Serialization.XmlSerializer> では、`XmlAttributeAttribute` などの属性を使用することによって、結果の XML をより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-123">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="e8f2c-124">特定の操作やサービス全体で <xref:System.Xml.Serialization.XmlSerializer> を使用するように切り替えるには、<xref:System.ServiceModel.XmlSerializerFormatAttribute> 属性を操作またはサービスに適用します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-124">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="e8f2c-125">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-125">For example:</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 <span data-ttu-id="e8f2c-126">詳細については、「 [XmlSerializer クラスの使用](using-the-xmlserializer-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-126">For more information, see [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="e8f2c-127">「XmlSerializer の使用」で説明するような明確な理由がある場合を除き、ここで示す <xref:System.Xml.Serialization.XmlSerializer> への手動での切り替えはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-127">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="e8f2c-128">.NET パラメーター名をコントラクト名から分離するには、<xref:System.ServiceModel.MessageParameterAttribute> 属性を使用し、`Name` プロパティを使用してコントラクト名を設定します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-128">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="e8f2c-129">たとえば、次の操作コントラクトは、このトピックの最初の例に相当します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-129">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a><span data-ttu-id="e8f2c-130">空のメッセージの記述</span><span class="sxs-lookup"><span data-stu-id="e8f2c-130">Describing Empty Messages</span></span>  

 <span data-ttu-id="e8f2c-131">空の要求メッセージを記述するには、入力パラメーターや参照パラメーターを一切指定しません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-131">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="e8f2c-132">たとえば、C# では、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-132">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="e8f2c-133">たとえば、Visual Basic の場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-133">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="e8f2c-134">空の応答メッセージを記述するには、戻り値の型として `void` を指定し、出力パラメーターや参照パラメーターを一切指定しません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-134">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="e8f2c-135">次の場合:</span><span class="sxs-lookup"><span data-stu-id="e8f2c-135">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="e8f2c-136">これは、次のような一方向操作コントラクトと異なります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-136">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="e8f2c-137">`SetTemperatureStatus` 操作は空のメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-137">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="e8f2c-138">入力メッセージの処理中にエラーが発生した場合は、代わりにエラーを返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-138">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="e8f2c-139">`SetLightbulbStatus` 操作は何も返しません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-139">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="e8f2c-140">この操作からエラー状態を伝達することはできません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-140">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="e8f2c-141">メッセージ コントラクトを使用したメッセージの記述</span><span class="sxs-lookup"><span data-stu-id="e8f2c-141">Describing Messages by Using Message Contracts</span></span>  

 <span data-ttu-id="e8f2c-142">1 つの型を使用してメッセージ全体を表現する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-142">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="e8f2c-143">この場合、データ コントラクトを使用することもできますが、メッセージ コントラクトを使用する方法をお勧めします。この方法を使用すると、結果の XML での不要なレベルのラップを回避できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-143">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="e8f2c-144">さらに、メッセージ コントラクトを使用すると、結果のメッセージをより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-144">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="e8f2c-145">たとえば、メッセージの本文とヘッダーに含める情報をそれぞれ決めることができます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-145">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="e8f2c-146">次に、メッセージ コントラクトの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-146">The following example shows the use of message contracts.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 <span data-ttu-id="e8f2c-147">詳細については、「 [メッセージコントラクトの使用](using-message-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-147">For more information, see [Using Message Contracts](using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="e8f2c-148">前の例でも <xref:System.Runtime.Serialization.DataContractSerializer> クラスが既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-148">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="e8f2c-149">メッセージ コントラクトで、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-149">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="e8f2c-150">これを行うには、操作またはコントラクトに <xref:System.ServiceModel.XmlSerializerFormatAttribute> 属性を適用し、メッセージ ヘッダーと本文メンバーで <xref:System.Xml.Serialization.XmlSerializer> クラスと互換性のある型を使用します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-150">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="e8f2c-151">ストリームを使用したメッセージの記述</span><span class="sxs-lookup"><span data-stu-id="e8f2c-151">Describing Messages by Using Streams</span></span>  

 <span data-ttu-id="e8f2c-152">操作でメッセージを記述する場合は、<xref:System.IO.Stream> クラスまたはその派生クラスを操作コントラクトで使用したり、メッセージ コントラクト本文メンバー (この場合、唯一のメンバーである必要があります) として使用したりする方法もあります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-152">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="e8f2c-153">受信メッセージの場合、型は `Stream` である必要があり、派生クラスを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-153">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="e8f2c-154">WCF は、シリアライザーを呼び出す代わりに、ストリームからデータを取得し、送信メッセージに直接格納するか、受信メッセージからデータを取得してストリームに直接格納します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-154">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="e8f2c-155">次に、ストリームの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-155">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="e8f2c-156">1 つのメッセージ本文で `Stream` と非ストリーム データを組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-156">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="e8f2c-157">追加データをメッセージ ヘッダーに配置するには、メッセージ コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-157">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="e8f2c-158">操作コントラクトを定義するときのストリームの不適切な使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-158">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 <span data-ttu-id="e8f2c-159">操作コントラクトを定義するときのストリームの正しい使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-159">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 <span data-ttu-id="e8f2c-160">詳細については、「 [Large Data And Streaming](large-data-and-streaming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-160">For more information, see [Large Data and Streaming](large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="e8f2c-161">メッセージ クラスの使用</span><span class="sxs-lookup"><span data-stu-id="e8f2c-161">Using the Message Class</span></span>  

 <span data-ttu-id="e8f2c-162">送受信されるメッセージをプログラムによって完全に制御するには、次のコード例に示すように <xref:System.ServiceModel.Channels.Message> クラスを直接使用します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-162">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="e8f2c-163">これは高度なシナリオです。詳細については、「 [Message クラスの使用](using-the-message-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-163">This is an advanced scenario, which is described in detail in [Using the Message Class](using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="e8f2c-164">エラー メッセージの記述</span><span class="sxs-lookup"><span data-stu-id="e8f2c-164">Describing Fault Messages</span></span>  

 <span data-ttu-id="e8f2c-165">一方向ではない操作では、戻り値と出力パラメーターまたは参照パラメーターによって記述されるメッセージに加え、通常の応答メッセージとエラー メッセージの少なくとも 2 つのメッセージを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-165">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="e8f2c-166">たとえば、次の操作コントラクトがあるとします。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-166">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="e8f2c-167">この操作は、`float` 型の数値を含む通常のメッセージか、エラー コードと説明を含むエラー メッセージのいずれかを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-167">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="e8f2c-168">これは、サービス実装で <xref:System.ServiceModel.FaultException> をスローすることによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-168">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="e8f2c-169"><xref:System.ServiceModel.FaultContractAttribute> 属性を使用すると、追加のエラー メッセージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-169">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="e8f2c-170">追加のエラーは、次のコード例に示すように、<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-170">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 <span data-ttu-id="e8f2c-171">これらの追加エラーは、適切なデータ コントラクト型の <xref:System.ServiceModel.FaultException%601> をスローすることによって生成できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-171">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="e8f2c-172">詳細については、「 [例外とエラーの処理](../extending/handling-exceptions-and-faults.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-172">For more information, see [Handling Exceptions and Faults](../extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="e8f2c-173"><xref:System.Xml.Serialization.XmlSerializer> クラスを使用してエラーを記述することはできません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-173">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="e8f2c-174"><xref:System.ServiceModel.XmlSerializerFormatAttribute> は、エラー コントラクトに影響を及ぼしません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-174">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="e8f2c-175">派生型の使用</span><span class="sxs-lookup"><span data-stu-id="e8f2c-175">Using Derived Types</span></span>  

 <span data-ttu-id="e8f2c-176">操作コントラクトやメッセージ コントラクトで基本型を使用し、その後、実際に操作を呼び出すときに派生型を使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-176">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="e8f2c-177">この場合、<xref:System.ServiceModel.ServiceKnownTypeAttribute> 属性または何らかの代替機構を使用して、派生型を使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-177">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="e8f2c-178">次の操作があるとします。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-178">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="e8f2c-179">`Book` から派生する `Magazine` と `LibraryItem` の 2 つの型があると想定します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-179">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="e8f2c-180">`IsLibraryItemAvailable` 操作でこれらの型を使用するには、操作を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-180">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="e8f2c-181">既定の <xref:System.Runtime.Serialization.KnownTypeAttribute> を使用している場合は、次のコード例に示すように <xref:System.Runtime.Serialization.DataContractSerializer> 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-181">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 <span data-ttu-id="e8f2c-182"><xref:System.Xml.Serialization.XmlIncludeAttribute> を使用する場合は、<xref:System.Xml.Serialization.XmlSerializer> 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-182">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="e8f2c-183"><xref:System.ServiceModel.ServiceKnownTypeAttribute> 属性は、操作に適用することもサービス全体に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-183">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="e8f2c-184">この属性は、<xref:System.Runtime.Serialization.KnownTypeAttribute> 属性と同様に、型を受け取るか、既知の型の一覧を取得するために呼び出すメソッドの名前を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-184">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="e8f2c-185">詳細については、「 [データコントラクトの既知の型](data-contract-known-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-185">For more information, see [Data Contract Known Types](data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="e8f2c-186">Use と Style の指定</span><span class="sxs-lookup"><span data-stu-id="e8f2c-186">Specifying the Use and Style</span></span>  

 <span data-ttu-id="e8f2c-187">Web サービス記述言語 (WSDL: Web Services Description Language) を使用してサービスを記述するときは、一般にドキュメントとリモート プロシージャ コール (RPC: Remote Procedure Call) の 2 つのスタイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-187">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="e8f2c-188">ドキュメント スタイルでは、スキーマを使用してメッセージ本文全体が記述されます。WSDL では、該当するスキーマの中の要素を参照して、メッセージ本文のさまざまな部分を記述します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-188">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="e8f2c-189">RPC スタイルでは、WSDL は、要素ではなく、メッセージの各部を表すスキーマ型を参照します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-189">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="e8f2c-190">場合によっては、これらのスタイルのいずれかを手動で選択することが必要になります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-190">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="e8f2c-191">これを行うには、<xref:System.ServiceModel.DataContractFormatAttribute> 属性を適用し、`Style` プロパティを設定するか (<xref:System.Runtime.Serialization.DataContractSerializer> を使用している場合)、`Style` 属性の <xref:System.ServiceModel.XmlSerializerFormatAttribute> を設定します (<xref:System.Xml.Serialization.XmlSerializer> を使用している場合)。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-191">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="e8f2c-192">また、<xref:System.Xml.Serialization.XmlSerializer> はシリアル化された XML の形式を 2 とおり (`Literal` および `Encoded`) サポートしています。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-192">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="e8f2c-193">`Literal` は最も一般に受け入れられたフォームであり、<xref:System.Runtime.Serialization.DataContractSerializer> がサポートする唯一のフォームです。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-193">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="e8f2c-194">`Encoded` は SOAP 仕様のセクション 5 に記載されたレガシ フォームであり、新しいサービスにはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-194">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="e8f2c-195">`Encoded` モードに切り替えるには、`Use` 属性の <xref:System.ServiceModel.XmlSerializerFormatAttribute> プロパティを `Encoded` に設定します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-195">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="e8f2c-196">ほとんどの場合、`Style` プロパティと `Use` プロパティの既定の設定は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-196">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="e8f2c-197">シリアル化プロセスの制御</span><span class="sxs-lookup"><span data-stu-id="e8f2c-197">Controlling the Serialization Process</span></span>  

 <span data-ttu-id="e8f2c-198">データをシリアル化する方法をカスタマイズする場合、さまざまな設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-198">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="e8f2c-199">サーバーのシリアル化設定の変更</span><span class="sxs-lookup"><span data-stu-id="e8f2c-199">Changing Server Serialization Settings</span></span>  

 <span data-ttu-id="e8f2c-200">既定の <xref:System.Runtime.Serialization.DataContractSerializer> を使用している場合は、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性をサービスに適用することで、サービスでのシリアル化プロセスの一部の側面を制御できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-200">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="e8f2c-201">具体的には、`MaxItemsInObjectGraph` プロパティを使用して、<xref:System.Runtime.Serialization.DataContractSerializer> が逆シリアル化するオブジェクトの最大数を制限するクォータを設定できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-201">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="e8f2c-202">また、`IgnoreExtensionDataObject` プロパティを使用すると、ラウンド トリップ バージョン管理機能を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-202">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="e8f2c-203">クォータの詳細については、「[セキュリティに関するデータの考慮事項](security-considerations-for-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-203">For more information about quotas, see [Security Considerations for Data](security-considerations-for-data.md).</span></span> <span data-ttu-id="e8f2c-204">ラウンドトリップの詳細については、「 [上位互換性のあるデータコントラクト](forward-compatible-data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-204">For more information about round-tripping, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a><span data-ttu-id="e8f2c-205">シリアル化の動作</span><span class="sxs-lookup"><span data-stu-id="e8f2c-205">Serialization Behaviors</span></span>  

 <span data-ttu-id="e8f2c-206">WCF では、 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> 特定の操作に使用されているシリアライザーに応じて自動的に接続されるとの2つの動作が使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-206">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="e8f2c-207">これらの動作は自動的に適用されるため、通常、これらの動作を意識する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-207">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="e8f2c-208">ただし、`DataContractSerializerOperationBehavior` には、`MaxItemsInObjectGraph`、`IgnoreExtensionDataObject`、および `DataContractSurrogate` の 3 つのプロパティがあり、これらを使用してシリアル化プロセスをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-208">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="e8f2c-209">最初の 2 つのプロパティの意味は、前のセクションの説明と同じです。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-209">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="e8f2c-210">`DataContractSurrogate` プロパティを使用すると、シリアル化プロセスをカスタマイズおよび拡張するための強力な機構であるデータ コントラクト サロゲートを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-210">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="e8f2c-211">詳細については、「 [データコントラクトサロゲート](../extending/data-contract-surrogates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-211">For more information, see [Data Contract Surrogates](../extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="e8f2c-212">`DataContractSerializerOperationBehavior` を使用すると、クライアントとサーバーの両方のシリアル化をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-212">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="e8f2c-213">クライアントで `MaxItemsInObjectGraph` クォータを増やす方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-213">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
<span data-ttu-id="e8f2c-214">次に示すのは、自己ホスト型の場合のサービスの同等のコードです。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-214">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 <span data-ttu-id="e8f2c-215">Web ホスト型の場合は、新しい `ServiceHost` 派生クラスを作成し、サービス ホスト ファクトリを使用してプラグインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-215">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="e8f2c-216">構成でのシリアル化設定の制御</span><span class="sxs-lookup"><span data-stu-id="e8f2c-216">Controlling Serialization Settings in Configuration</span></span>  

 <span data-ttu-id="e8f2c-217">次の例に示すように、`MaxItemsInObjectGraph` と `IgnoreExtensionDataObject` は、`dataContractSerializer` エンドポイントまたはサービスの動作を使用して構成によって制御できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-217">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address="http://example.com/myservice"  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="e8f2c-218">共有する型のシリアル化、オブジェクト グラフの保存、およびカスタム シリアライザー</span><span class="sxs-lookup"><span data-stu-id="e8f2c-218">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  

 <span data-ttu-id="e8f2c-219"><xref:System.Runtime.Serialization.DataContractSerializer> は、.NET 型名ではなく、データ コントラクト名を使用してシリアル化を実行します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-219">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="e8f2c-220">これは、サービス指向アーキテクチャの基本思想と一致しており、高度な柔軟性の実現を可能にします。つまり、ネットワーク コントラクトに影響を及ぼさずに .NET 型を変更できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-220">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="e8f2c-221">まれなケースとして、実際の .NET 型名をシリアル化することにより、.NET Framework リモート処理テクノロジと同様のクライアントとサーバー間の密結合を導入することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-221">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="e8f2c-222">これは、.NET Framework リモート処理から WCF に移行するときに通常発生するまれなケースを除き、推奨される方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-222">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="e8f2c-223">この場合、<xref:System.Runtime.Serialization.NetDataContractSerializer> クラスではなく、<xref:System.Runtime.Serialization.DataContractSerializer> クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-223">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="e8f2c-224"><xref:System.Runtime.Serialization.DataContractSerializer> は、通常、オブジェクト グラフをオブジェクト ツリーとしてシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-224">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="e8f2c-225">つまり、同じオブジェクトが複数回にわたって参照される場合、そのオブジェクトは複数回にわたってシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-225">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="e8f2c-226">たとえば、`PurchaseOrder` および `billTo` という、Address 型の 2 つのフィールドを持つ `shipTo` インスタンスがあるとします。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-226">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="e8f2c-227">この両方のフィールドに同じ Address インスタンスを設定すると、シリアル化および逆シリアル化の後に 2 つの同一の Address インスタンスが生じます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-227">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="e8f2c-228">これは、オブジェクト グラフを XML で表現する相互運用可能な標準の方法がないためです (ただし、<xref:System.Xml.Serialization.XmlSerializer> と `Style` に関する前のセクションで説明した `Use` で使用できる従来の SOAP エンコード標準を除きます)。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-228">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="e8f2c-229">オブジェクト グラフをツリーとしてシリアル化する場合、循環参照が含まれたグラフをシリアル化できないなどの欠点があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-229">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="e8f2c-230">場合によっては、相互運用が可能ではありませんが、真のオブジェクト グラフ シリアル化に切り替えることが必要になります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-230">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="e8f2c-231">これを行うには、<xref:System.Runtime.Serialization.DataContractSerializer> パラメーターを `preserveObjectReferences` に設定して構築した `true` を使用します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-231">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="e8f2c-232">シナリオによっては、組み込みのシリアライザーでは不十分な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-232">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="e8f2c-233">ただし、ほとんどの場合、<xref:System.Runtime.Serialization.XmlObjectSerializer> と <xref:System.Runtime.Serialization.DataContractSerializer> の派生元である <xref:System.Runtime.Serialization.NetDataContractSerializer> 抽象クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-233">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="e8f2c-234">前の 3 つのケース (.NET 型の保存、オブジェクト グラフの保存、および `XmlObjectSerializer` ベースの完全なカスタム シリアル化) では、必ずカスタム シリアライザーをプラグインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-234">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="e8f2c-235">この操作を行うには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-235">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="e8f2c-236"><xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> から派生する独自の動作を記述します。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-236">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="e8f2c-237">独自のシリアライザー (`CreateSerializer`、<xref:System.Runtime.Serialization.NetDataContractSerializer> が <xref:System.Runtime.Serialization.DataContractSerializer> に設定された `preserveObjectReferences`、独自のカスタム `true` のいずれか) を返すように 2 つの <xref:System.Runtime.Serialization.XmlObjectSerializer> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-237">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="e8f2c-238">サービス ホストを開いたり、クライアント チャネルを作成したりする前に、既存の <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 動作を削除し、前の手順で作成したカスタム派生クラスをプラグインします。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-238">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="e8f2c-239">高度なシリアル化の概念の詳細については、「 [シリアル化と逆シリアル](serialization-and-deserialization.md)化」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8f2c-239">For more information about advanced serialization concepts, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f2c-240">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8f2c-240">See also</span></span>

- [<span data-ttu-id="e8f2c-241">XmlSerializer クラスの使用</span><span class="sxs-lookup"><span data-stu-id="e8f2c-241">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)
- [<span data-ttu-id="e8f2c-242">方法: ストリーミングを有効にする</span><span class="sxs-lookup"><span data-stu-id="e8f2c-242">How to: Enable Streaming</span></span>](how-to-enable-streaming.md)
- [<span data-ttu-id="e8f2c-243">方法: クラスまたは構造体に基本的なデータ コントラクトを作成する</span><span class="sxs-lookup"><span data-stu-id="e8f2c-243">How to: Create a Basic Data Contract for a Class or Structure</span></span>](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
