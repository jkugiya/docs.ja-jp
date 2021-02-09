---
description: '詳細情報: 方法:グループの接続にユーザー情報を割り当てる'
title: '方法: グループの接続にユーザー情報を割り当てる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
ms.openlocfilehash: 2af901b91c561f5f46c63ed627cbd0053d30e624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729264"
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="1971a-103">方法: グループの接続にユーザー情報を割り当てる</span><span class="sxs-lookup"><span data-stu-id="1971a-103">How to: Assign User Information to Group Connections</span></span>

 <span data-ttu-id="1971a-104">次の例では、グループの接続にユーザー情報を割り当てる方法を示します。このセクションのコードが呼び出される前に、アプリケーションで変数の *UserName*、*SecurelyStoredPassword*、および *Domain* が設定されており、*UserName* が一意であると想定します。</span><span class="sxs-lookup"><span data-stu-id="1971a-104">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="1971a-105">グループの接続にユーザー情報を割り当てるには</span><span class="sxs-lookup"><span data-stu-id="1971a-105">To assign user information to a group connection</span></span>  
  
1. <span data-ttu-id="1971a-106">接続グループ名を作成します。</span><span class="sxs-lookup"><span data-stu-id="1971a-106">Create a connection group name.</span></span>  
  
    ```csharp  
    SHA1Managed Sha1 = new SHA1Managed();  
    Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
    String secureGroupName = Encoding.Default.GetString(updHash);  
    ```  
  
    ```vb  
    Dim Sha1 As New SHA1Managed()  
    Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
    Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
    ```  
  
2. <span data-ttu-id="1971a-107">特定の URL の要求を作成します。</span><span class="sxs-lookup"><span data-stu-id="1971a-107">Create a request for a specific URL.</span></span> <span data-ttu-id="1971a-108">たとえば、次のコードでは URL `http://www.contoso.com.` の要求が作成されます。</span><span class="sxs-lookup"><span data-stu-id="1971a-108">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3. <span data-ttu-id="1971a-109">Web 要求の資格情報と ConnectionGroupName を設定し、**GetResponse** を呼び出して **WebResponse** オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="1971a-109">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
    ```csharp  
    myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);
    myWebRequest.ConnectionGroupName = secureGroupName;  
  
    WebResponse myWebResponse=myWebRequest.GetResponse();  
    ```  
  
    ```vb  
    myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
    myWebRequest.ConnectionGroupName = secureGroupName  
  
    Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
    ```  
  
4. <span data-ttu-id="1971a-110">WebRespose オブジェクトを使用した後、応答ストリームを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1971a-110">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="1971a-111">例</span><span class="sxs-lookup"><span data-stu-id="1971a-111">Example</span></span>  
  
```csharp  
// Create a connection group name.  
SHA1Managed Sha1 = new SHA1Managed();  
Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
String secureGroupName = Encoding.Default.GetString(updHash);  
  
// Create a request for a specific URL.  
WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
  
myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);
myWebRequest.ConnectionGroupName = secureGroupName;  
  
WebResponse myWebResponse=myWebRequest.GetResponse();  
  
// Insert the code that uses myWebResponse.  
  
MyWebResponse.Close();  
```  
  
```vb  
' Create a secure group name.  
Dim Sha1 As New SHA1Managed()  
Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
  
' Create a request for a specific URL.  
Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
  
myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
myWebRequest.ConnectionGroupName = secureGroupName  
  
Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
  
' Insert the code that uses myWebResponse.  
MyWebResponse.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="1971a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1971a-112">See also</span></span>

- [<span data-ttu-id="1971a-113">接続の管理</span><span class="sxs-lookup"><span data-stu-id="1971a-113">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="1971a-114">接続のグループ化</span><span class="sxs-lookup"><span data-stu-id="1971a-114">Connection Grouping</span></span>](connection-grouping.md)
