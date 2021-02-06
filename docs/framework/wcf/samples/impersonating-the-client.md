---
description: 詳細については、「クライアントの偽装」を参照してください。
title: クライアントの偽装
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: cab6f342a572d357f6987f60218ef2682bedd447
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631763"
---
# <a name="impersonating-the-client"></a><span data-ttu-id="7baba-103">クライアントの偽装</span><span class="sxs-lookup"><span data-stu-id="7baba-103">Impersonating the Client</span></span>

<span data-ttu-id="7baba-104">偽装のサンプルでは、サービスで呼び出し元のアプリケーションを偽装し、サービスが呼び出し元の代わりにシステム リソースにアクセスできるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7baba-104">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="7baba-105">このサンプルは、 [自己ホスト](self-host.md) のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="7baba-105">This sample is based on the [Self-Host](self-host.md) sample.</span></span> <span data-ttu-id="7baba-106">サービスとクライアントの構成ファイルは、 [自己ホスト](self-host.md) のサンプルと同じです。</span><span class="sxs-lookup"><span data-stu-id="7baba-106">The service and client configuration files are the same as that of the [Self-Host](self-host.md) sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7baba-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7baba-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7baba-108">サービス コードは、サービスの `Add` メソッドが <xref:System.ServiceModel.OperationBehaviorAttribute> を使用して呼び出し元を偽装するように変更されています。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7baba-108">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="7baba-109">この結果、実行中のスレッドのセキュリティ コンテキストは呼び出し元を偽装するように切り替えられ、その後 `Add` メソッドが入力されて、このメソッドが終了すると元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="7baba-109">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="7baba-110">次のサンプル コードに示す `DisplayIdentityInformation` メソッドは、呼び出し元の ID を表示するユーティリティ関数です。</span><span class="sxs-lookup"><span data-stu-id="7baba-110">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```csharp
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 <span data-ttu-id="7baba-111">サービスの `Subtract` メソッドは、強制呼び出しを使用して呼び出し元を偽装します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7baba-111">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```csharp
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    Console.WriteLine("Before impersonating");  
    DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs
            // on the system resource are enforced in the caller's context.
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
    Console.WriteLine("After reverting");  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="7baba-112">この場合、呼び出し元は呼び出し全体に対して偽装されるのではなく、呼び出しの一部に対してのみ偽装されます。</span><span class="sxs-lookup"><span data-stu-id="7baba-112">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="7baba-113">通常、操作全体の偽装を行うよりも、最小限の範囲での偽装をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7baba-113">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="7baba-114">他のメソッドは呼び出し元を偽装しません。</span><span class="sxs-lookup"><span data-stu-id="7baba-114">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="7baba-115">クライアント コードは、偽装レベルを <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> に設定するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="7baba-115">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="7baba-116">クライアントは <xref:System.Security.Principal.TokenImpersonationLevel> 列挙体を使用して、サービスで使用される偽装レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7baba-116">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="7baba-117">この列挙体は、<xref:System.Security.Principal.TokenImpersonationLevel.None>、<xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>、<xref:System.Security.Principal.TokenImpersonationLevel.Identification>、<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>、および <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> の値をサポートします。</span><span class="sxs-lookup"><span data-stu-id="7baba-117">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="7baba-118">Windows ACL を使用して保護されているローカル コンピューターのシステム リソースにアクセスする場合、アクセス チェックを実行するには、偽装レベルを <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> に設定する必要があります。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7baba-118">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="7baba-119">このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7baba-119">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="7baba-120">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="7baba-120">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7baba-121">サービスは、管理者アカウントで実行するか、または実行するアカウントに HTTP レイヤーを使用して URI を登録する権限が付与されている必要があり `http://localhost:8000/ServiceModelSamples` ます。</span><span class="sxs-lookup"><span data-stu-id="7baba-121">The service must either run under an administrative account or the account it runs under must be granted rights to register the `http://localhost:8000/ServiceModelSamples` URI with the HTTP layer.</span></span> <span data-ttu-id="7baba-122">このような権限は、 [Httpcfg.exe ツール](/windows/win32/http/httpcfg-exe)を使用して[名前空間の予約](/windows/win32/http/namespace-reservations-registrations-and-routing)を設定することによって付与できます。</span><span class="sxs-lookup"><span data-stu-id="7baba-122">Such rights can be granted by setting up a [Namespace Reservation](/windows/win32/http/namespace-reservations-registrations-and-routing) using the [Httpcfg.exe tool](/windows/win32/http/httpcfg-exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7baba-123">Windows Server 2003 を実行しているコンピューターでは、Host.exe アプリケーションに偽装特権がある場合にのみ、偽装がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7baba-123">On computers running Windows Server 2003, impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="7baba-124">(既定では、管理者のみがこのアクセス許可を持っています)。この特権をサービスが実行されているアカウントに追加するには、[ **管理ツール**]、[ **ローカルセキュリティポリシー**]、[ **ローカルポリシー**]、[ **ユーザー権利の割り当て**] の順に選択し、[ **認証後にクライアントを偽装** ] をクリックし、[ **プロパティ** ] をダブルクリックしてユーザーまたはグループを追加します。</span><span class="sxs-lookup"><span data-stu-id="7baba-124">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7baba-125">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="7baba-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7baba-126">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="7baba-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7baba-127">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7baba-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7baba-128">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7baba-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="7baba-129">サービスが呼び出し元を偽装していることを示すため、サービスが実行されているアカウントとは異なるアカウントでクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="7baba-129">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="7baba-130">これを行うには、コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="7baba-130">To do so, at the command prompt, type:</span></span>  
  
    ```console  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="7baba-131">次に、パスワードの入力が求められます。</span><span class="sxs-lookup"><span data-stu-id="7baba-131">You are then prompted for a password.</span></span> <span data-ttu-id="7baba-132">先ほど指定したアカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="7baba-132">Enter the password for the account you previously specified.</span></span>  
  
5. <span data-ttu-id="7baba-133">クライアントを実行する際、クライアントを実行する前と後で ID の資格情報が異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7baba-133">When you run the client, note the identity before and after running it with different credentials.</span></span>  
