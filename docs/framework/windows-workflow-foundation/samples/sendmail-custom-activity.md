---
description: '詳細情報: SendMail カスタムアクティビティ'
title: SendMail カスタム アクティビティ
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 853e28d26c41338670d377593d5a3536b011d112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741758"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="3c10b-103">SendMail カスタム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="3c10b-103">SendMail Custom Activity</span></span>

<span data-ttu-id="3c10b-104">このサンプルでは、<xref:System.Activities.AsyncCodeActivity> から派生するカスタム アクティビティを作成して、SMTP を使用して電子メールを送信し、ワークフロー アプリケーション内で使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-104">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="3c10b-105">カスタムアクティビティでは、の機能を使用して、 <xref:System.Net.Mail.SmtpClient> 電子メールを非同期的に送信し、認証を使用してメールを送信します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-105">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="3c10b-106">また、テスト モード、トークン置換、ファイル テンプレート、テスト ドロップ パスなどのエンドユーザーの機能も提供しています。</span><span class="sxs-lookup"><span data-stu-id="3c10b-106">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="3c10b-107">次の表で、`SendMail` アクティビティの引数の詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-107">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="3c10b-108">名前</span><span class="sxs-lookup"><span data-stu-id="3c10b-108">Name</span></span>|<span data-ttu-id="3c10b-109">Type</span><span class="sxs-lookup"><span data-stu-id="3c10b-109">Type</span></span>|<span data-ttu-id="3c10b-110">説明</span><span class="sxs-lookup"><span data-stu-id="3c10b-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3c10b-111">Host</span><span class="sxs-lookup"><span data-stu-id="3c10b-111">Host</span></span>|<span data-ttu-id="3c10b-112">String</span><span class="sxs-lookup"><span data-stu-id="3c10b-112">String</span></span>|<span data-ttu-id="3c10b-113">SMTP サーバー ホストのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3c10b-113">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="3c10b-114">ポート</span><span class="sxs-lookup"><span data-stu-id="3c10b-114">Port</span></span>|<span data-ttu-id="3c10b-115">String</span><span class="sxs-lookup"><span data-stu-id="3c10b-115">String</span></span>|<span data-ttu-id="3c10b-116">ホストの SMTP サービスのポート。</span><span class="sxs-lookup"><span data-stu-id="3c10b-116">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="3c10b-117">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="3c10b-117">EnableSsl</span></span>|<span data-ttu-id="3c10b-118">[bool]</span><span class="sxs-lookup"><span data-stu-id="3c10b-118">bool</span></span>|<span data-ttu-id="3c10b-119"><xref:System.Net.Mail.SmtpClient> が、接続を暗号化するために SSL (Secure Sockets Layer) を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-119">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="3c10b-120">UserName</span><span class="sxs-lookup"><span data-stu-id="3c10b-120">UserName</span></span>|<span data-ttu-id="3c10b-121">文字列型</span><span class="sxs-lookup"><span data-stu-id="3c10b-121">String</span></span>|<span data-ttu-id="3c10b-122">差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するユーザー名。</span><span class="sxs-lookup"><span data-stu-id="3c10b-122">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="3c10b-123">Password</span><span class="sxs-lookup"><span data-stu-id="3c10b-123">Password</span></span>|<span data-ttu-id="3c10b-124">String</span><span class="sxs-lookup"><span data-stu-id="3c10b-124">String</span></span>|<span data-ttu-id="3c10b-125">差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するパスワード。</span><span class="sxs-lookup"><span data-stu-id="3c10b-125">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="3c10b-126">サブジェクト</span><span class="sxs-lookup"><span data-stu-id="3c10b-126">Subject</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="3c10b-127">メッセージの件名。</span><span class="sxs-lookup"><span data-stu-id="3c10b-127">Subject of the message.</span></span>|  
|<span data-ttu-id="3c10b-128">本文</span><span class="sxs-lookup"><span data-stu-id="3c10b-128">Body</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="3c10b-129">メッセージの本文。</span><span class="sxs-lookup"><span data-stu-id="3c10b-129">Body of the message.</span></span>|  
|<span data-ttu-id="3c10b-130">[Attachments]</span><span class="sxs-lookup"><span data-stu-id="3c10b-130">Attachments</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="3c10b-131">この電子メールメッセージに添付されたデータを格納するために使用される添付ファイルのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="3c10b-131">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="3c10b-132">差出人</span><span class="sxs-lookup"><span data-stu-id="3c10b-132">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="3c10b-133">この電子メールメッセージの差出人アドレス。</span><span class="sxs-lookup"><span data-stu-id="3c10b-133">From address for this email message.</span></span>|  
|<span data-ttu-id="3c10b-134">終了</span><span class="sxs-lookup"><span data-stu-id="3c10b-134">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="3c10b-135">この電子メールメッセージの受信者を含むアドレスコレクション。</span><span class="sxs-lookup"><span data-stu-id="3c10b-135">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="3c10b-136">CC</span><span class="sxs-lookup"><span data-stu-id="3c10b-136">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="3c10b-137">この電子メールメッセージのカーボンコピー (CC) 受信者を格納するアドレスのコレクション。</span><span class="sxs-lookup"><span data-stu-id="3c10b-137">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="3c10b-138">BCC</span><span class="sxs-lookup"><span data-stu-id="3c10b-138">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="3c10b-139">この電子メールメッセージの BCC (ブラインドカーボンコピー) 受信者を含むアドレスコレクション。</span><span class="sxs-lookup"><span data-stu-id="3c10b-139">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="3c10b-140">トークン</span><span class="sxs-lookup"><span data-stu-id="3c10b-140">Tokens</span></span>|<span data-ttu-id="3c10b-141"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span><span class="sxs-lookup"><span data-stu-id="3c10b-141"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="3c10b-142">本文で置換するトークン。</span><span class="sxs-lookup"><span data-stu-id="3c10b-142">Tokens to replace in the body.</span></span> <span data-ttu-id="3c10b-143">この機能を使用すると、本文にいくつかの値を指定した後、このプロパティを使用して提供されるトークンで置換できます。</span><span class="sxs-lookup"><span data-stu-id="3c10b-143">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="3c10b-144">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="3c10b-144">BodyTemplateFilePath</span></span>|<span data-ttu-id="3c10b-145">String</span><span class="sxs-lookup"><span data-stu-id="3c10b-145">String</span></span>|<span data-ttu-id="3c10b-146">本文のテンプレートのパス。</span><span class="sxs-lookup"><span data-stu-id="3c10b-146">Path of a template for the body.</span></span> <span data-ttu-id="3c10b-147">`SendMail` アクティビティは、このファイルの内容をその body プロパティにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3c10b-147">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="3c10b-148">テンプレートは、tokens プロパティの内容によって置き換えられるトークンを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3c10b-148">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="3c10b-149">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="3c10b-149">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="3c10b-150">このプロパティを設定すると、すべての電子メールが、その中に指定されたアドレスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="3c10b-150">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="3c10b-151">このプロパティは、ワークフローをテストするときに使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="3c10b-151">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="3c10b-152">たとえば、すべての電子メールが実際の受信者に送信されることなく送信されるようにする場合です。</span><span class="sxs-lookup"><span data-stu-id="3c10b-152">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="3c10b-153">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="3c10b-153">TestDropPath</span></span>|<span data-ttu-id="3c10b-154">String</span><span class="sxs-lookup"><span data-stu-id="3c10b-154">String</span></span>|<span data-ttu-id="3c10b-155">このプロパティが設定されている場合、すべての電子メールも指定したファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="3c10b-155">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="3c10b-156">このプロパティは、ワークフローをテストまたはデバッグするときに使用することを目的としており、送信メールの形式と内容が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-156">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="3c10b-157">ソリューションのコンテンツ</span><span class="sxs-lookup"><span data-stu-id="3c10b-157">Solution Contents</span></span>  

 <span data-ttu-id="3c10b-158">ソリューションには、次の 2 つのプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c10b-158">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="3c10b-159">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="3c10b-159">Project</span></span>|<span data-ttu-id="3c10b-160">説明</span><span class="sxs-lookup"><span data-stu-id="3c10b-160">Description</span></span>|<span data-ttu-id="3c10b-161">重要なファイル</span><span class="sxs-lookup"><span data-stu-id="3c10b-161">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="3c10b-162">SendMail</span><span class="sxs-lookup"><span data-stu-id="3c10b-162">SendMail</span></span>|<span data-ttu-id="3c10b-163">SendMail アクティビティ</span><span class="sxs-lookup"><span data-stu-id="3c10b-163">The SendMail activity</span></span>|<span data-ttu-id="3c10b-164">1. SendMail.cs: メインアクティビティの実装</span><span class="sxs-lookup"><span data-stu-id="3c10b-164">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="3c10b-165">2. SendMailDesigner .xaml and SendMailDesigner.xaml.cs: SendMail アクティビティのデザイナー</span><span class="sxs-lookup"><span data-stu-id="3c10b-165">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="3c10b-166">3. MailTemplateBody.htm: 送信する電子メールのテンプレート。</span><span class="sxs-lookup"><span data-stu-id="3c10b-166">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="3c10b-167">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="3c10b-167">SendMailTestClient</span></span>|<span data-ttu-id="3c10b-168">SendMail アクティビティをテストするクライアント。</span><span class="sxs-lookup"><span data-stu-id="3c10b-168">Client to test the SendMail activity.</span></span>  <span data-ttu-id="3c10b-169">このプロジェクトでは、SendMail アクティビティを宣言的に起動する方法とプログラムで起動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-169">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="3c10b-170">1. Sequence1: SendMail アクティビティを呼び出すワークフロー。</span><span class="sxs-lookup"><span data-stu-id="3c10b-170">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="3c10b-171">2. Program.cs: Sequence1 を呼び出し、SendMail を使用するプログラムによってワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-171">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="3c10b-172">SendMail アクティビティの追加構成</span><span class="sxs-lookup"><span data-stu-id="3c10b-172">Further configuration of the SendMail activity</span></span>  

 <span data-ttu-id="3c10b-173">サンプルには表示されませんが、SendMail アクティビティの追加構成を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3c10b-173">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="3c10b-174">次の 3 つのセクションは、その方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3c10b-174">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="3c10b-175">本文で指定されたトークンを使用した電子メールの送信</span><span class="sxs-lookup"><span data-stu-id="3c10b-175">Sending an email using tokens specified in the body</span></span>  

 <span data-ttu-id="3c10b-176">次のコード スニペットでは、本文のトークンを使用して電子メールを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-176">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="3c10b-177">トークンが body プロパティに指定されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="3c10b-177">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="3c10b-178">それらのトークンの値は、tokens プロパティに指定されています。</span><span class="sxs-lookup"><span data-stu-id="3c10b-178">Values for those tokens are provided to the tokens property.</span></span>  
  
```csharp  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="3c10b-179">テンプレートを使用した電子メールの送信</span><span class="sxs-lookup"><span data-stu-id="3c10b-179">Sending an email using a template</span></span>  

 <span data-ttu-id="3c10b-180">次のスニペットでは、本文のテンプレート トークンを使用して電子メールを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-180">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="3c10b-181">`BodyTemplateFilePath` プロパティを設定するときに、Body プロパティの値を指定する必要がないことに注目してください (テンプレート ファイルのコンテンツは本文にコピーされます)。</span><span class="sxs-lookup"><span data-stu-id="3c10b-181">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```csharp  
new SendMail  
{
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="3c10b-182">テスト モードでの電子メールの送信</span><span class="sxs-lookup"><span data-stu-id="3c10b-182">Sending Mails in Testing Mode</span></span>  

 <span data-ttu-id="3c10b-183">このコードスニペットは、2つのテストプロパティを設定する方法を示しています。をに設定すると `TestMailTo` 、すべてのメッセージがに送信されます `john.doe@contoso.con` (To、Cc、Bcc の値には関係ありません)。</span><span class="sxs-lookup"><span data-stu-id="3c10b-183">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="3c10b-184">TestDropPath を設定すると、送信するすべての電子メールは、指定したパスにも記録されます。</span><span class="sxs-lookup"><span data-stu-id="3c10b-184">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="3c10b-185">これらのプロパティは、個別に設定できます (関連していません)。</span><span class="sxs-lookup"><span data-stu-id="3c10b-185">These properties can be set independently (they are not related).</span></span>  
  
```csharp  
new SendMail  
{
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="3c10b-186">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="3c10b-186">Set-Up Instructions</span></span>  

 <span data-ttu-id="3c10b-187">このサンプルでは SMTP サーバーにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c10b-187">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="3c10b-188">SMTP サーバーの設定の詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c10b-188">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="3c10b-189">[SMTP サービス (IIS 6.0) の構成](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="3c10b-189">[Configuring the SMTP Service (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="3c10b-190">[IIS 7.0: SMTP 電子メールの構成](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="3c10b-190">[IIS 7.0: Configure SMTP E-Mail](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="3c10b-191">[SMTP サービスをインストールする方法](/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="3c10b-191">[How to Install the SMTP Service](/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="3c10b-192">ダウンロードには、サードパーティで提供されている SMTP エミュレーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c10b-192">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="3c10b-193">このサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="3c10b-193">To run this sample</span></span>  
  
1. <span data-ttu-id="3c10b-194">Visual Studio 2010 を使用して、SendMail のソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="3c10b-194">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="3c10b-195">有効な SMTP サーバーへのアクセス権があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3c10b-195">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="3c10b-196">セットアップ手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c10b-196">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="3c10b-197">サーバーアドレス、差出人、および宛先の電子メールアドレスを使用して、プログラムを構成します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-197">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="3c10b-198">このサンプルを正しく実行するには、From および To 電子メールアドレスの値と Program.cs の SMTP サーバーのアドレスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c10b-198">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="3c10b-199">プログラムでは電子メールが 2 つの方法で送信されるため、両方の場所でアドレスを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c10b-199">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="3c10b-200">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-200">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="3c10b-201">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="3c10b-201">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3c10b-202">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3c10b-202">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3c10b-203">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3c10b-203">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3c10b-204">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="3c10b-204">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3c10b-205">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3c10b-205">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
