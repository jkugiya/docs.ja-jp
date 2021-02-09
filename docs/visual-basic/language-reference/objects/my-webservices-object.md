---
description: '詳細情報: My.WebServices オブジェクト'
title: My.WebServices オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: e8d7ef8b349fef6d69b92d9df4a23222bd3c912e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640538"
---
# <a name="mywebservices-object"></a><span data-ttu-id="b5366-103">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="b5366-103">My.WebServices Object</span></span>

<span data-ttu-id="b5366-104">現在のプロジェクトによって参照される各 XML Web サービスの単一のインスタンスを作成してアクセスするためのプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="b5366-104">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5366-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="b5366-105">Remarks</span></span>  

 <span data-ttu-id="b5366-106">`My.WebServices` オブジェクトは、現在のプロジェクトにより参照されている各 Web サービスのインスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b5366-106">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="b5366-107">各インスタンスは要求に応じてインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="b5366-107">Each instance is instantiated on demand.</span></span> <span data-ttu-id="b5366-108">これらの Web サービスには `My.WebServices` オブジェクトのプロパティを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b5366-108">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="b5366-109">プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになります。</span><span class="sxs-lookup"><span data-stu-id="b5366-109">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="b5366-110"><xref:System.Web.Services.Protocols.SoapHttpClientProtocol> から継承されたクラスはすべて Web サービスです。</span><span class="sxs-lookup"><span data-stu-id="b5366-110">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="b5366-111">プロジェクトへの Web サービスの追加の詳細については、「[アプリケーションの Web サービスへのアクセス](../../developing-apps/programming/accessing-application-web-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5366-111">For information about adding Web services to a project, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="b5366-112">`My.WebServices` オブジェクトでは、現在のプロジェクトに関連付けられている Web サービスのみが公開されます。</span><span class="sxs-lookup"><span data-stu-id="b5366-112">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="b5366-113">参照されている DLL で宣言されている Web サービスへのアクセスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="b5366-113">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="b5366-114">DLL で提供されている Web サービスにアクセスするには、Web サービスの修飾名を *DllName*.*WebServiceName* の形式で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5366-114">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="b5366-115">詳細については、「[アプリケーションの Web サービスへのアクセス](../../developing-apps/programming/accessing-application-web-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5366-115">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="b5366-116">オブジェクトとそのプロパティは、Web アプリケーションで使用できません。</span><span class="sxs-lookup"><span data-stu-id="b5366-116">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b5366-117">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b5366-117">Properties</span></span>  

 <span data-ttu-id="b5366-118">`My.WebServices` オブジェクトの各プロパティにより、現在のプロジェクトで参照されている Web サービスのインスタンスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b5366-118">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="b5366-119">プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになり、プロパティの型は Web サービスの型と同じになります。</span><span class="sxs-lookup"><span data-stu-id="b5366-119">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5366-120">名前の競合がある場合、Web サービスにアクセスするためのプロパティ名は、*RootNamespace* _ *Namespace*\_*ServiceName* になります。</span><span class="sxs-lookup"><span data-stu-id="b5366-120">If there is a name collision, the property name for accessing a Web service is *RootNamespace* _ *Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="b5366-121">たとえば、`Service1` という名前の 2 つの Web サービスがあるとします。</span><span class="sxs-lookup"><span data-stu-id="b5366-121">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="b5366-122">これらのサービスのいずれかがルート名前空間 `WindowsApplication1` および名前空間 `Namespace1` にある場合は、`My.WebServices.WindowsApplication1_Namespace1_Service1` を使用してそのサービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b5366-122">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="b5366-123">`My.WebServices` オブジェクトのいずれかのプロパティに初めてアクセスすると、Web サービスの新しいインスタンスが作成され、保存されます。</span><span class="sxs-lookup"><span data-stu-id="b5366-123">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="b5366-124">そのプロパティのその後のアクセスでは、Web サービスのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="b5366-124">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="b5366-125">Web サービスを破棄するには、Web サービスのプロパティに `Nothing` を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b5366-125">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="b5366-126">プロパティ セッターによって、格納されている値に `Nothing` が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b5366-126">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="b5366-127">プロパティに `Nothing` 以外の値を割り当てた場合、セッターが <xref:System.ArgumentException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b5366-127">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="b5366-128">`My.WebServices` オブジェクトのプロパティに Web サービスのインスタンスが格納されているかどうかをテストするには、`Is` または `IsNot` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5366-128">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="b5366-129">これらの演算子を使用すると、プロパティの値が `Nothing` かどうかをチェックできます。</span><span class="sxs-lookup"><span data-stu-id="b5366-129">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5366-130">通常、`Is` または `IsNot` 演算子では、比較を実行するためにプロパティの値を読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5366-130">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="b5366-131">ただし、プロパティに現在 `Nothing` が格納されている場合は、プロパティによって Web サービスの新しいインスタンスが作成され、そのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="b5366-131">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="b5366-132">ただし、Visual Basic コンパイラでは、`My.WebServices` オブジェクトのプロパティが特別に処理されるため、`Is` または `IsNot` 演算子によって、値を変更せずにプロパティの状態をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="b5366-132">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5366-133">例</span><span class="sxs-lookup"><span data-stu-id="b5366-133">Example</span></span>  

 <span data-ttu-id="b5366-134">この例では、`TemperatureConverter` XML Web サービスの `FahrenheitToCelsius` メソッドを呼び出して、その結果を返しています。</span><span class="sxs-lookup"><span data-stu-id="b5366-134">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 <span data-ttu-id="b5366-135">この例を機能させるには、プロジェクトで `Converter` という名前の Web サービスを参照し、その Web サービスで `ConvertTemperature` メソッドを公開している必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5366-135">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="b5366-136">詳細については、「[アプリケーションの Web サービスへのアクセス](../../developing-apps/programming/accessing-application-web-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5366-136">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="b5366-137">このコードは、Web アプリケーション プロジェクトでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="b5366-137">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5366-138">必要条件</span><span class="sxs-lookup"><span data-stu-id="b5366-138">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="b5366-139">プロジェクトの種類別の可用性</span><span class="sxs-lookup"><span data-stu-id="b5366-139">Availability by Project Type</span></span>  
  
|<span data-ttu-id="b5366-140">プロジェクトの種類</span><span class="sxs-lookup"><span data-stu-id="b5366-140">Project type</span></span>|<span data-ttu-id="b5366-141">使用可能</span><span class="sxs-lookup"><span data-stu-id="b5366-141">Available</span></span>|  
|---|---|  
|<span data-ttu-id="b5366-142">Windows アプリケーション</span><span class="sxs-lookup"><span data-stu-id="b5366-142">Windows Application</span></span>|<span data-ttu-id="b5366-143">**はい**</span><span class="sxs-lookup"><span data-stu-id="b5366-143">**Yes**</span></span>|  
|<span data-ttu-id="b5366-144">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="b5366-144">Class Library</span></span>|<span data-ttu-id="b5366-145">**はい**</span><span class="sxs-lookup"><span data-stu-id="b5366-145">**Yes**</span></span>|  
|<span data-ttu-id="b5366-146">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="b5366-146">Console Application</span></span>|<span data-ttu-id="b5366-147">**はい**</span><span class="sxs-lookup"><span data-stu-id="b5366-147">**Yes**</span></span>|  
|<span data-ttu-id="b5366-148">Windows コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="b5366-148">Windows Control Library</span></span>|<span data-ttu-id="b5366-149">**はい**</span><span class="sxs-lookup"><span data-stu-id="b5366-149">**Yes**</span></span>|  
|<span data-ttu-id="b5366-150">Web コントロール ライブラリ</span><span class="sxs-lookup"><span data-stu-id="b5366-150">Web Control Library</span></span>|<span data-ttu-id="b5366-151">**はい**</span><span class="sxs-lookup"><span data-stu-id="b5366-151">**Yes**</span></span>|  
|<span data-ttu-id="b5366-152">Windows サービス</span><span class="sxs-lookup"><span data-stu-id="b5366-152">Windows Service</span></span>|<span data-ttu-id="b5366-153">**はい**</span><span class="sxs-lookup"><span data-stu-id="b5366-153">**Yes**</span></span>|  
|<span data-ttu-id="b5366-154">Web サイト</span><span class="sxs-lookup"><span data-stu-id="b5366-154">Web Site</span></span>|<span data-ttu-id="b5366-155">いいえ</span><span class="sxs-lookup"><span data-stu-id="b5366-155">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5366-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5366-156">See also</span></span>

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [<span data-ttu-id="b5366-157">アプリケーションの Web サービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="b5366-157">Accessing Application Web Services</span></span>](../../developing-apps/programming/accessing-application-web-services.md)
