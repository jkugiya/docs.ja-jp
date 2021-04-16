---
description: '詳細情報: 方法: GenericPrincipal および GenericIdentity オブジェクトを作成する'
title: '方法: GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する'
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
ms.openlocfilehash: 8c77a9afec7bd166a71abb6af19d8766b02d0523
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685219"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>方法: GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する

> [!NOTE]
> この記事は Windows に適用されます。
>
> ASP.NET Core の詳細については、「[ASP.NET Core セキュリティの概要](/aspnet/core/security/)」を参照してください。

Windows ドメインから独立して存在する認可スキームを作成するには、<xref:System.Security.Principal.GenericIdentity> クラスと <xref:System.Security.Principal.GenericPrincipal> クラスを組み合わせて使用できます。

### <a name="to-create-a-genericprincipal-object"></a>GenericPrincipal オブジェクトを作成するには

1. ID クラスの新しいインスタンスを作成し、インスタンスに付ける名前で初期化します。 新しい **GenericIdentity** オブジェクトを作成し、名前 `MyUser` で初期化するコードを次に示します。

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. **GenericPrincipal** クラスの新しいインスタンスを作成し、前に作成した **GenericIdentity** オブジェクトと、プリンシパルに関連付けるロールを表す文字列の配列で、このインスタンスを初期化します。 管理者のロールとユーザーのロールを表す文字列の配列を指定するコード例を次に示します。 **GenericPrincipal** は、前の **GenericIdentity** と文字列配列で初期化されます。

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. 次のコードを使用して、プリンシパルを現在のスレッドに結合します。 この方法が便利なのは、プリンシパルが 2 回以上検証される必要がある場合、アプリケーション内で実行されている他のコードによって検証される必要がある場合、または <xref:System.Security.Permissions.PrincipalPermission> オブジェクトによって検証される必要がある場合です。 このような場合でも、プリンシパル オブジェクトをスレッドに結合せずにロール ベースの検証を行うことができます。 詳細については、「[プリンシパル オブジェクトの置き換え](replacing-a-principal-object.md)」を参照してください。

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a>例

次のコード例では、**GenericPrincipal** と **GenericIdentity** のインスタンスを作成する方法を示します。 このコードは、各オブジェクトの値をコンソールに表示します。

```vb
Imports System.Security.Principal
Imports System.Threading

Public Class Class1

    Public Shared Sub Main()
        ' Create generic identity.
        Dim myIdentity As New GenericIdentity("MyIdentity")

        ' Create generic principal.
        Dim myStringArray As String() =  {"Manager", "Teller"}
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)

        ' Attach the principal to the current thread.
        ' This is not required unless repeated validation must occur,
        ' other code in your application must validate, or the
        ' PrincipalPermission object is used.
        Thread.CurrentPrincipal = myPrincipal

        ' Print values to the console.
        Dim name As String = myPrincipal.Identity.Name
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")

        Console.WriteLine("The name is: {0}", name)
        Console.WriteLine("The isAuthenticated is: {0}", auth)
        Console.WriteLine("Is this a Manager? {0}", isInRole)

    End Sub

End Class
```

```csharp
using System;
using System.Security.Principal;
using System.Threading;

public class Class1
{
    public static int Main(string[] args)
    {
    // Create generic identity.
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");

    // Create generic principal.
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal =
        new GenericPrincipal(myIdentity, myStringArray);

    // Attach the principal to the current thread.
    // This is not required unless repeated validation must occur,
    // other code in your application must validate, or the
    // PrincipalPermission object is used.
    Thread.CurrentPrincipal = myPrincipal;

    // Print values to the console.
    String name =  myPrincipal.Identity.Name;
    bool auth =  myPrincipal.Identity.IsAuthenticated;
    bool isInRole =  myPrincipal.IsInRole("Manager");

    Console.WriteLine("The name is: {0}", name);
    Console.WriteLine("The isAuthenticated is: {0}", auth);
    Console.WriteLine("Is this a Manager? {0}", isInRole);

    return 0;
    }
}
```

実行されると、アプリケーションの出力は次のようになります。

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a>関連項目

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [プリンシパル オブジェクトの置き換え](replacing-a-principal-object.md)
- [プリンシパル オブジェクトと ID オブジェクト](principal-and-identity-objects.md)
