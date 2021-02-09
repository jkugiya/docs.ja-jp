---
description: '詳細情報: 安全なクライアント アプリケーション'
title: 安全なクライアント アプリケーション
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: a40a6444c2e317b03f03688ca46de157ded6f0ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718955"
---
# <a name="secure-client-applications"></a><span data-ttu-id="ae69f-103">安全なクライアント アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ae69f-103">Secure Client Applications</span></span>

<span data-ttu-id="ae69f-104">通常、アプリケーションは多数の要素で構成されており、それぞれをデータの損失やシステムのセキュリティ侵害を招く脆弱性から確実に保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae69f-104">Applications typically consist of many parts that must all be protected from vulnerabilities that could result in data loss or otherwise compromise the system.</span></span> <span data-ttu-id="ae69f-105">安全なユーザー インターフェイスを作成し、攻撃者によるデータやシステム リソースへのアクセスを未然に阻止することで、多くの問題を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="ae69f-105">Creating secure user interfaces can prevent many problems by blocking attackers before they can access data or system resources.</span></span>  
  
## <a name="validate-user-input"></a><span data-ttu-id="ae69f-106">ユーザー入力の検証</span><span class="sxs-lookup"><span data-stu-id="ae69f-106">Validate User Input</span></span>  

 <span data-ttu-id="ae69f-107">データにアクセスするアプリケーションを構築する場合、ユーザーの入力はすべて悪意のあるものと想定しない限り、</span><span class="sxs-lookup"><span data-stu-id="ae69f-107">When constructing an application that accesses data, you should assume that all user input is malicious until proven otherwise.</span></span> <span data-ttu-id="ae69f-108">攻撃に対する脆弱性をアプリケーションから取り除くことはできません。</span><span class="sxs-lookup"><span data-stu-id="ae69f-108">Failure to do so can leave your application vulnerable to attack.</span></span> <span data-ttu-id="ae69f-109">.NET Framework には、入力できる文字数の制限など、入力コントロールの値の範囲を設定するクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ae69f-109">The .NET Framework contains classes to help you enforce a domain of values for input controls, such as limiting the number of characters that can be entered.</span></span> <span data-ttu-id="ae69f-110">イベントを捕捉することによって、値の有効性を確認するプロシージャを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ae69f-110">Event hooks allow you to write procedures to check the validity of values.</span></span> <span data-ttu-id="ae69f-111">ユーザーによって入力されるデータを検証し、厳密に型指定することで、アプリケーションをスクリプト インジェクションや SQL インジェクションなどの攻撃にさらす機会を制限できます。</span><span class="sxs-lookup"><span data-stu-id="ae69f-111">User input data can be validated and strongly typed, limiting an application's exposure to script and SQL injection exploits.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ae69f-112">クライアント アプリケーションだけでなく、データ ソース側でもユーザー入力を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae69f-112">You must also validate user input at the data source as well as in the client application.</span></span> <span data-ttu-id="ae69f-113">攻撃者がアプリケーションを迂回し、データ ソースを直接攻撃してくる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="ae69f-113">An attacker may choose to circumvent your application and attack the data source directly.</span></span>  
  
 [<span data-ttu-id="ae69f-114">セキュリティとユーザー入力</span><span class="sxs-lookup"><span data-stu-id="ae69f-114">Security and User Input</span></span>](../../../standard/security/security-and-user-input.md)  
 <span data-ttu-id="ae69f-115">発見が難しく大きな危険を招く可能性のあるユーザー入力に関連したバグへの対処方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-115">Describes how to handle subtle and potentially dangerous bugs involving user input.</span></span>  
  
 <span data-ttu-id="ae69f-116">[ASP.NET Web ページにおけるユーザー入力の検証](/previous-versions/aspnet/7kh55542(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ae69f-116">[Validating User Input in ASP.NET Web Pages](/previous-versions/aspnet/7kh55542(v=vs.100))</span></span>  
 <span data-ttu-id="ae69f-117">ASP.NET の検証コントロールを使ったユーザー入力の検証について概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-117">Overview of validating user input using ASP.NET validation controls.</span></span>  
  
 [<span data-ttu-id="ae69f-118">Windows フォームでのユーザー入力</span><span class="sxs-lookup"><span data-stu-id="ae69f-118">User Input in Windows Forms</span></span>](/dotnet/desktop/winforms/user-input-in-windows-forms)  
 <span data-ttu-id="ae69f-119">Windows フォーム アプリケーションにおけるマウス入力およびキーボード入力の検証に関連したリンクや情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-119">Provides links and information for validating mouse and keyboard input in a Windows Forms application.</span></span>  
  
 [<span data-ttu-id="ae69f-120">.NET Framework 正規表現</span><span class="sxs-lookup"><span data-stu-id="ae69f-120">.NET Framework Regular Expressions</span></span>](../../../standard/base-types/regular-expressions.md)  
 <span data-ttu-id="ae69f-121"><xref:System.Text.RegularExpressions.Regex> クラスを使用してユーザー入力の有効性を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-121">Describes how to use the <xref:System.Text.RegularExpressions.Regex> class to check the validity of user input.</span></span>  
  
## <a name="windows-applications"></a><span data-ttu-id="ae69f-122">Windows アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ae69f-122">Windows Applications</span></span>  

 <span data-ttu-id="ae69f-123">これまで、Windows アプリケーションは、アクセスがすべて許可された状態で実行されていました。</span><span class="sxs-lookup"><span data-stu-id="ae69f-123">In the past, Windows applications generally ran with full permissions.</span></span> <span data-ttu-id="ae69f-124">.NET Framework は、コード アクセス セキュリティ (CAS) を使用して Windows アプリケーションで実行されるコードを制限するインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-124">The .NET Framework provides the infrastructure to restrict code executing in a Windows application by using code access security (CAS).</span></span> <span data-ttu-id="ae69f-125">ただし、CAS だけでは、アプリケーションを保護するには不十分です。</span><span class="sxs-lookup"><span data-stu-id="ae69f-125">However, CAS alone is not enough to protect your application.</span></span>  
  
 [<span data-ttu-id="ae69f-126">Windows フォームのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="ae69f-126">Windows Forms Security</span></span>](/dotnet/desktop/winforms/windows-forms-security)  
 <span data-ttu-id="ae69f-127">Windows フォーム アプリケーションをセキュリティで保護する方法について説明します。また、関連項目へのリンクがあります。</span><span class="sxs-lookup"><span data-stu-id="ae69f-127">Discusses how to secure Windows Forms applications and provides links to related topics.</span></span>  
  
 [<span data-ttu-id="ae69f-128">Windows Forms and Unmanaged Applications</span><span class="sxs-lookup"><span data-stu-id="ae69f-128">Windows Forms and Unmanaged Applications</span></span>](/dotnet/desktop/winforms/advanced/windows-forms-and-unmanaged-applications)  
 <span data-ttu-id="ae69f-129">Windows フォーム アプリケーションでアンマネージ アプリケーションと対話する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-129">Describes how to interact with unmanaged applications in a Windows Forms application.</span></span>  
  
 [<span data-ttu-id="ae69f-130">Windows フォームの ClickOnce 配置</span><span class="sxs-lookup"><span data-stu-id="ae69f-130">ClickOnce Deployment for Windows Forms</span></span>](/dotnet/desktop/winforms/clickonce-deployment-for-windows-forms)  
 <span data-ttu-id="ae69f-131">Windows フォーム アプリケーションでの `ClickOnce` 配置の使用方法およびセキュリティへの影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-131">Describes how to use `ClickOnce` deployment in a Windows Forms application and discusses the security implications.</span></span>  
  
## <a name="aspnet-and-xml-web-services"></a><span data-ttu-id="ae69f-132">ASP.NET と XML Web サービス</span><span class="sxs-lookup"><span data-stu-id="ae69f-132">ASP.NET and XML Web Services</span></span>  

 <span data-ttu-id="ae69f-133">通常、ASP.NET アプリケーションは、アクセスを Web サイトの一部に制限し、データ保護およびサイト セキュリティのための他のメカニズムを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae69f-133">ASP.NET applications generally need to restrict access to some portions of the Web site and provide other mechanisms for data protection and site security.</span></span> <span data-ttu-id="ae69f-134">以下のリンクにアクセスすると、ASP.NET アプリケーションをセキュリティで保護するための有益な情報を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="ae69f-134">These links provide useful information for securing your ASP.NET application.</span></span>  
  
 <span data-ttu-id="ae69f-135">XML Web サービスは、ASP.NET アプリケーション、Windows フォーム アプリケーション、またはその他の Web サービスが使用できるデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-135">An XML Web service provides data that can be consumed by an ASP.NET application, a Windows Forms application, or another Web service.</span></span> <span data-ttu-id="ae69f-136">クライアント アプリケーションのセキュリティだけでなく、Web サービスそのもののセキュリティを管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae69f-136">You need to manage security for the Web service itself as well as security for the client application.</span></span>  
  
 <span data-ttu-id="ae69f-137">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae69f-137">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="ae69f-138">リソース</span><span class="sxs-lookup"><span data-stu-id="ae69f-138">Resource</span></span>|<span data-ttu-id="ae69f-139">説明</span><span class="sxs-lookup"><span data-stu-id="ae69f-139">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ae69f-140">[ASP.NET Web サイトのセキュリティ保護](/previous-versions/aspnet/91f66yxt(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ae69f-140">[Securing ASP.NET Web Sites](/previous-versions/aspnet/91f66yxt(v=vs.100))</span></span>|<span data-ttu-id="ae69f-141">ASP.NET アプリケーションをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-141">Discusses how to secure ASP.NET applications.</span></span>|  
|<span data-ttu-id="ae69f-142">[ASP.NET を使用して作成した XML Web サービスのセキュリティ](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ae69f-142">[Securing XML Web Services Created Using ASP.NET](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))</span></span>|<span data-ttu-id="ae69f-143">ASP.NET Web サービスへのセキュリティの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-143">Discusses how to implement security for an ASP.NET Web Service.</span></span>|  
|<span data-ttu-id="ae69f-144">[スクリプト攻略の概要](/previous-versions/aspnet/w1sw53ds(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ae69f-144">[Script Exploits Overview](/previous-versions/aspnet/w1sw53ds(v=vs.100))</span></span>|<span data-ttu-id="ae69f-145">Web ページに悪意のある文字の挿入を試みるスクリプト攻略攻撃を阻止する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-145">Discusses how to guard against a script exploit attack, which attempts to insert malicious characters into a Web page.</span></span>|  
|<span data-ttu-id="ae69f-146">[Web アプリケーションのセキュリティに関する基本的な対策](/previous-versions/aspnet/zdh19h94(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ae69f-146">[Basic Security Practices for Web Applications](/previous-versions/aspnet/zdh19h94(v=vs.100))</span></span>|<span data-ttu-id="ae69f-147">一般的なセキュリティ情報のほか、より詳細なページへのリンクも掲載されています。</span><span class="sxs-lookup"><span data-stu-id="ae69f-147">General security information and links to further discussion,</span></span>|  
  
## <a name="remoting"></a><span data-ttu-id="ae69f-148">リモート処理</span><span class="sxs-lookup"><span data-stu-id="ae69f-148">Remoting</span></span>  

 <span data-ttu-id="ae69f-149">.NET リモート処理を使用すると、広範囲の分散アプリケーションを簡単に構築できます。その場合、アプリケーションのコンポーネントを、すべて 1 台のコンピューターに置くことも、遠隔地のコンピューターに分散させることもできます。</span><span class="sxs-lookup"><span data-stu-id="ae69f-149">.NET remoting enables you to build widely distributed applications easily, whether the application components are all on one computer or spread out across the entire world.</span></span> <span data-ttu-id="ae69f-150">同じコンピューター上、またはネットワークを経由してアクセスできる他の任意のコンピューター上にある他のプロセスのオブジェクトを使用するクライアント アプリケーションを構築できます。</span><span class="sxs-lookup"><span data-stu-id="ae69f-150">You can build client applications that use objects in other processes on the same computer or on any other computer that is reachable over its network.</span></span> <span data-ttu-id="ae69f-151">また、.NET リモート処理を使用すると、同じプロセスの他のアプリケーション ドメインと通信できます。</span><span class="sxs-lookup"><span data-stu-id="ae69f-151">You can also use .NET remoting to communicate with other application domains in the same process.</span></span>  
  
|<span data-ttu-id="ae69f-152">リソース</span><span class="sxs-lookup"><span data-stu-id="ae69f-152">Resource</span></span>|<span data-ttu-id="ae69f-153">説明</span><span class="sxs-lookup"><span data-stu-id="ae69f-153">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ae69f-154">[リモート アプリケーションの構成](/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ae69f-154">[Configuration of Remote Applications](/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))</span></span>|<span data-ttu-id="ae69f-155">一般的な問題を回避するためのリモート処理アプリケーションの構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-155">Discusses how to configure remoting applications in order to avoid common problems.</span></span>|  
|<span data-ttu-id="ae69f-156">[リモート処理でのセキュリティ](/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ae69f-156">[Security in Remoting](/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))</span></span>|<span data-ttu-id="ae69f-157">認証と暗号化のほか、リモート処理に関連したその他のセキュリティ トピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-157">Describes authentication and encryption as well as additional security topics relevant to remoting.</span></span>|  
|[<span data-ttu-id="ae69f-158">セキュリティとリモート処理の考慮事項</span><span class="sxs-lookup"><span data-stu-id="ae69f-158">Security and Remoting Considerations</span></span>](../../misc/security-and-remoting-considerations.md)|<span data-ttu-id="ae69f-159">保護されたオブジェクトやアプリケーション ドメインの境界越えに伴うセキュリティの問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae69f-159">Describes security issues with protected objects and application domain crossing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae69f-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae69f-160">See also</span></span>

- [<span data-ttu-id="ae69f-161">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="ae69f-161">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- <span data-ttu-id="ae69f-162">[データ アクセス戦略に関する推奨事項](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ae69f-162">[Recommendations for Data Access Strategies](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))</span></span>
- [<span data-ttu-id="ae69f-163">アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="ae69f-163">Securing Applications</span></span>](/visualstudio/ide/securing-applications)
- [<span data-ttu-id="ae69f-164">接続情報の保護</span><span class="sxs-lookup"><span data-stu-id="ae69f-164">Protecting Connection Information</span></span>](protecting-connection-information.md)
- [<span data-ttu-id="ae69f-165">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="ae69f-165">ADO.NET Overview</span></span>](ado-net-overview.md)
