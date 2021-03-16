---
title: '破壊的変更: ほとんどのコード アクセス セキュリティ API は旧型式'
description: Core .NET ライブラリでの .NET 5 に関する破壊的変更について学習します。この変更により、.NET でのほとんどのコード アクセス セキュリティ (CAS) 関連の型は古いものとなり、警告が示されるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: cc4be58622e81022e74476cf824a19689ba23ea4
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257636"
---
# <a name="most-code-access-security-apis-are-obsolete"></a><span data-ttu-id="2c059-103">ほとんどのコード アクセス セキュリティ API は旧型式</span><span class="sxs-lookup"><span data-stu-id="2c059-103">Most code access security APIs are obsolete</span></span>

<span data-ttu-id="2c059-104">.NET のほとんどのコード アクセス セキュリティ (CAS) 関連の型は、古いと見なされ、警告が示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="2c059-104">Most code access security (CAS)-related types in .NET are now obsolete as warning.</span></span> <span data-ttu-id="2c059-105">これには、<xref:System.Security.Permissions.SecurityPermissionAttribute> などの CAS 属性、<xref:System.Net.SocketPermission> などの CAS アクセス許可オブジェクト、<xref:System.Security.Policy.EvidenceBase> 派生型、その他のサポート API が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2c059-105">This includes CAS attributes, such as <xref:System.Security.Permissions.SecurityPermissionAttribute>, CAS permission objects, such as <xref:System.Net.SocketPermission>, <xref:System.Security.Policy.EvidenceBase>-derived types, and other supporting APIs.</span></span>

## <a name="change-description"></a><span data-ttu-id="2c059-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="2c059-106">Change description</span></span>

<span data-ttu-id="2c059-107">.NET Framework 2.x から 4.x では、CAS 属性と API がコードの実行過程に影響する可能性があります。これには、CAS 要求スタック ウォークが成功したか失敗したかを必ず確かめることが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2c059-107">In .NET Framework 2.x - 4.x, CAS attributes and APIs can influence the course of code execution, including ensuring that CAS-demand stack walks succeed or fail.</span></span>

```csharp
// In .NET Framework, the attribute causes CAS stack walks
// to terminate successfully when this permission is demanded.
[SocketPermission(SecurityAction.Assert, Host = "contoso.com", Port = "443")]
public void DoSomething()
{
    // open a socket to contoso.com:443
}
```

<span data-ttu-id="2c059-108">.NET Core 2.x から 3.x では、ランタイムによって CAS 属性や CAS API は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="2c059-108">In .NET Core 2.x - 3.x, the runtime does not honor CAS attributes or CAS APIs.</span></span> <span data-ttu-id="2c059-109">ランタイムによってメソッド エントリの属性は無視され、ほとんどのプログラム API に影響はありません。</span><span class="sxs-lookup"><span data-stu-id="2c059-109">The runtime ignores attributes on method entry, and most programmatic APIs have no effect.</span></span>

```csharp
// The .NET Core runtime ignores the following attribute.
[SocketPermission(SecurityAction.Assert, Host = "contoso.com", Port = "443")]
public void DoSomething()
{
    // open a socket to contoso.com:443
}
```

<span data-ttu-id="2c059-110">また、包括的な API (`Assert`) へのプログラムによる呼び出しは常に成功しますが、限定的な API (`Deny`、`PermitOnly`) へのプログラムによる呼び出しによって常に実行時に例外がスローされます</span><span class="sxs-lookup"><span data-stu-id="2c059-110">Additionally, programmatic calls to expansive APIs (`Assert`) always succeed, while programmatic calls to restrictive APIs (`Deny`, `PermitOnly`) always throw an exception at run time.</span></span> <span data-ttu-id="2c059-111">(<xref:System.Security.Permissions.PrincipalPermission> は、この規則の例外です。</span><span class="sxs-lookup"><span data-stu-id="2c059-111">(<xref:System.Security.Permissions.PrincipalPermission> is an exception to this rule.</span></span> <span data-ttu-id="2c059-112">以下の「[推奨される操作](#cas-action)」セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="2c059-112">See the [Recommended action](#cas-action) section below.)</span></span>

```csharp
public void DoAssert()
{
    // The line below has no effect at run time.
    new SocketPermission(PermissionState.Unrestricted).Assert();
}

public void DoDeny()
{
    // The line below throws PlatformNotSupportedException at run time.
    new SocketPermission(PermissionState.Unrestricted).Deny();
}
```

<span data-ttu-id="2c059-113">.NET 5 以降のバージョンでは、ほとんどの CAS 関連 API は古いと見なされ、コンパイル時の警告 `SYSLIB0003` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2c059-113">In .NET 5 and later versions, most CAS-related APIs are obsolete and produce compile-time warning `SYSLIB0003`.</span></span>

```csharp
[SocketPermission(SecurityAction.Assert, Host = "contoso.com", Port = "443")] // warning SYSLIB0003
public void DoSomething()
{
    new SocketPermission(PermissionState.Unrestricted).Assert(); // warning SYSLIB0003
    new SocketPermission(PermissionState.Unrestricted).Deny(); // warning SYSLIB0003
}
```

<span data-ttu-id="2c059-114">これは、コンパイル時のみの変更です。</span><span class="sxs-lookup"><span data-stu-id="2c059-114">This is a compile-time only change.</span></span> <span data-ttu-id="2c059-115">実行時については、以前のバージョンの .NET Core からの変更はありません。</span><span class="sxs-lookup"><span data-stu-id="2c059-115">There is no run-time change from previous versions of .NET Core.</span></span> <span data-ttu-id="2c059-116">.NET Core 2.x から 3.x で操作を行わないメソッドの場合、.NET 5 以降でも引き続き実行時に操作は行われません。</span><span class="sxs-lookup"><span data-stu-id="2c059-116">Methods that perform no operation in .NET Core 2.x - 3.x will continue to perform no operation at run time in .NET 5 and later.</span></span> <span data-ttu-id="2c059-117">.NET Core 2.x から 3.x で <xref:System.PlatformNotSupportedException> をスローするメソッドの場合、NET 5 以降でも引き続き実行時に <xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2c059-117">Methods that throw <xref:System.PlatformNotSupportedException> in .NET Core 2.x - 3.x will continue to throw a <xref:System.PlatformNotSupportedException> at run time in .NET 5 and later.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="2c059-118">変更理由</span><span class="sxs-lookup"><span data-stu-id="2c059-118">Reason for change</span></span>

<span data-ttu-id="2c059-119">[コード アクセス セキュリティ (CAS)](../../../../framework/misc/code-access-security.md) は、サポートされていないレガシ テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="2c059-119">[Code access security (CAS)](../../../../framework/misc/code-access-security.md) is an unsupported legacy technology.</span></span> <span data-ttu-id="2c059-120">CAS を有効にするためのインフラストラクチャは、.NET Framework 2.x から 4.x のみに存在しますが、非推奨であり、サービスやセキュリティの修正プログラムは受け取れません。</span><span class="sxs-lookup"><span data-stu-id="2c059-120">The infrastructure to enable CAS exists only in .NET Framework 2.x - 4.x, but is deprecated and not receiving servicing or security fixes.</span></span>

<span data-ttu-id="2c059-121">CAS の非推奨化により、[サポート インフラストラクチャは .NET Core](../../../porting/net-framework-tech-unavailable.md) や .NET 5.0 以降には引き継がれませんでした。</span><span class="sxs-lookup"><span data-stu-id="2c059-121">Due to CAS's deprecation, the [supporting infrastructure was not brought forward to .NET Core](../../../porting/net-framework-tech-unavailable.md) or .NET 5.0+.</span></span> <span data-ttu-id="2c059-122">しかし、アプリで .NET Framework と .NET Core に対してクロスコンパイルできるように、API は引き継がれました。</span><span class="sxs-lookup"><span data-stu-id="2c059-122">However, the APIs were brought forward so that apps could cross-compile against .NET Framework and .NET Core.</span></span> <span data-ttu-id="2c059-123">これにより、"フェール オープン" シナリオが発生します。その場合、一部の CAS 関連の API が存在し、呼び出し可能ですが、実行時に操作は行われません。</span><span class="sxs-lookup"><span data-stu-id="2c059-123">This led to "fail open" scenarios, where some CAS-related APIs exist and are callable but perform no action at run time.</span></span> <span data-ttu-id="2c059-124">これにより、ランタイムで CAS 関連の属性またはプログラムによる API 呼び出しが考慮されることを期待するコンポーネントでセキュリティに関する問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2c059-124">This can lead to security issues for components that expect the runtime to honor CAS-related attributes or programmatic API calls.</span></span> <span data-ttu-id="2c059-125">ランタイムでこれらの属性や API が考慮されないことをより適切に伝えるために、.NET 5.0 ではそれらのほとんどが古いと見なされています。</span><span class="sxs-lookup"><span data-stu-id="2c059-125">To better communicate that the runtime doesn't respect these attributes or APIs, we have obsoleted the majority of them in .NET 5.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="2c059-126">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="2c059-126">Version introduced</span></span>

<span data-ttu-id="2c059-127">5.0</span><span class="sxs-lookup"><span data-stu-id="2c059-127">5.0</span></span>

## <a name=""></a><span data-ttu-id="2c059-128"><a id="cas-action">推奨される操作</a></span><span class="sxs-lookup"><span data-stu-id="2c059-128"><a id="cas-action">Recommended action</a></span></span>

- <span data-ttu-id="2c059-129">セキュリティのアクセス許可をアサートする場合は、アクセス許可をアサートする属性または呼び出しを削除します。</span><span class="sxs-lookup"><span data-stu-id="2c059-129">If you're asserting any security permission, remove the attribute or call that asserts the permission.</span></span>

  ```csharp
  // REMOVE the attribute below.
  [SecurityPermission(SecurityAction.Assert, ControlThread = true)]
  public void DoSomething()
  {
  }

  public void DoAssert()
  {
      // REMOVE the line below.
      new SecurityPermission(SecurityPermissionFlag.ControlThread).Assert();
  }
  ```

- <span data-ttu-id="2c059-130">任意のアクセス許可を (`PermitOnly` を使用して) 拒否または制限する場合は、セキュリティ アドバイザーにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="2c059-130">If you're denying or restricting (via `PermitOnly`) any permission, contact your security advisor.</span></span> <span data-ttu-id="2c059-131">CAS の属性は .NET 5.0 以降のランタイムでは考慮されないため、CAS インフラストラクチャに誤って依存してこれらのメソッドへのアクセスを制限してしまうと、お使いのアプリケーションにセキュリティ ホールが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2c059-131">Because CAS attributes are not honored by the .NET 5.0+ runtime, your application could have a security hole if it incorrectly relies on the CAS infrastructure to restrict access to these methods.</span></span>

  ```csharp
  // REVIEW the attribute below; could indicate security vulnerability.
  [SecurityPermission(SecurityAction.Deny, ControlThread = true)]
  public void DoSomething()
  {
  }

  public void DoPermitOnly()
  {
      // REVIEW the line below; could indicate security vulnerability.
      new SecurityPermission(SecurityPermissionFlag.ControlThread).PermitOnly();
  }
  ```

- <span data-ttu-id="2c059-132">(<xref:System.Security.Permissions.PrincipalPermission> を除く) アクセス許可を要求している場合は、要求を削除します。</span><span class="sxs-lookup"><span data-stu-id="2c059-132">If you're demanding any permission (except <xref:System.Security.Permissions.PrincipalPermission>), remove the demand.</span></span> <span data-ttu-id="2c059-133">すべての要求は実行時に成功します。</span><span class="sxs-lookup"><span data-stu-id="2c059-133">All demands will succeed at run time.</span></span>

  ```csharp
  // REMOVE the attribute below; it will always succeed.
  [SecurityPermission(SecurityAction.Demand, ControlThread = true)]
  public void DoSomething()
  {
  }

  public void DoDemand()
  {
      // REMOVE the line below; it will always succeed.
      new SecurityPermission(SecurityPermissionFlag.ControlThread).Demand();
  }
  ```

- <span data-ttu-id="2c059-134"><xref:System.Security.Permissions.PrincipalPermission> を要求する場合は、「[PrincipalPermissionAttribute は古いエラーです](principalpermissionattribute-obsolete.md)」のガイダンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c059-134">If you're demanding <xref:System.Security.Permissions.PrincipalPermission>, consult the guidance for [PrincipalPermissionAttribute is obsolete as error](principalpermissionattribute-obsolete.md).</span></span> <span data-ttu-id="2c059-135">このガイダンスは、<xref:System.Security.Permissions.PrincipalPermission> と <xref:System.Security.Permissions.PrincipalPermissionAttribute> の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="2c059-135">That guidance applies for both <xref:System.Security.Permissions.PrincipalPermission> and <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>

- <span data-ttu-id="2c059-136">これらの警告を確実に無効にする (これは推奨されません) 必要がある場合は、コードで `SYSLIB0003` 警告を抑制することができます。</span><span class="sxs-lookup"><span data-stu-id="2c059-136">If you absolutely must disable these warnings (which is not recommended), you can suppress the `SYSLIB0003` warning in code.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0003 // disable the warning
  [SecurityPermission(SecurityAction.Demand, ControlThread = true)]
  #pragma warning restore SYSLIB0003 // re-enable the warning
  public void DoSomething()
  {
  }

  public void DoDemand()
  {
  #pragma warning disable SYSLIB0003 // disable the warning
      new SecurityPermission(SecurityPermissionFlag.ControlThread).Demand();
  #pragma warning restore SYSLIB0003 // re-enable the warning
  }
  ```

  <span data-ttu-id="2c059-137">また、プロジェクト ファイルで警告を抑制することもできます。</span><span class="sxs-lookup"><span data-stu-id="2c059-137">You can also suppress the warning in your project file.</span></span> <span data-ttu-id="2c059-138">そのようにすると、プロジェクト内のすべてのソース ファイルで警告が無効になります。</span><span class="sxs-lookup"><span data-stu-id="2c059-138">Doing so disables the warning for all source files within the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0003 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > <span data-ttu-id="2c059-139">`SYSLIB0003` を抑制すると、CAS 関連のものが古いという警告のみが無効になります。</span><span class="sxs-lookup"><span data-stu-id="2c059-139">Suppressing `SYSLIB0003` disables only the CAS-related obsoletion warnings.</span></span> <span data-ttu-id="2c059-140">他の警告が無効にされたり、.NET 5.0 以降のランタイムの動作が変更されたりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="2c059-140">It does not disable any other warnings or change the behavior of the .NET 5.0+ runtime.</span></span>
- <span data-ttu-id="2c059-141">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2c059-141">Security</span></span>

## <a name="affected-apis"></a><span data-ttu-id="2c059-142">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="2c059-142">Affected APIs</span></span>

- <xref:System.AppDomain.PermissionSet?displayProperty=fullName>
- <xref:System.Configuration.ConfigurationPermission?displayProperty=fullName>
- <xref:System.Configuration.ConfigurationPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermission?displayProperty=fullName>
- <xref:System.Data.Common.DBDataPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermission?displayProperty=fullName>
- <xref:System.Data.Odbc.OdbcPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermission?displayProperty=fullName>
- <xref:System.Data.OleDb.OleDbPermissionAttribute?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermission?displayProperty=fullName>
- <xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermission?displayProperty=fullName>
- <xref:System.Data.SqlClient.SqlClientPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.EventLogPermission?displayProperty=fullName>
- <xref:System.Diagnostics.EventLogPermissionAttribute?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermission?displayProperty=fullName>
- <xref:System.Diagnostics.PerformanceCounterPermissionAttribute?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermission?displayProperty=fullName>
- <xref:System.DirectoryServices.DirectoryServicesPermissionAttribute?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermission?displayProperty=fullName>
- <xref:System.Drawing.Printing.PrintingPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.DnsPermission?displayProperty=fullName>
- <xref:System.Net.DnsPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermission?displayProperty=fullName>
- <xref:System.Net.Mail.SmtpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermission?displayProperty=fullName>
- <xref:System.Net.NetworkInformation.NetworkInformationPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermission?displayProperty=fullName>
- <xref:System.Net.PeerToPeer.PnrpPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.SocketPermission?displayProperty=fullName>
- <xref:System.Net.SocketPermissionAttribute?displayProperty=fullName>
- <xref:System.Net.WebPermission?displayProperty=fullName>
- <xref:System.Net.WebPermissionAttribute?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.AllowReversePInvokeCallsAttribute?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission?displayProperty=fullName>
- <xref:System.Security.HostProtectionException?displayProperty=fullName>
- <xref:System.Security.IPermission?displayProperty=fullName>
- <xref:System.Security.IStackWalk?displayProperty=fullName>
- <xref:System.Security.NamedPermissionSet?displayProperty=fullName>
- <xref:System.Security.PermissionSet?displayProperty=fullName>
- <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.DataProtectionPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.EnvironmentPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileDialogPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.FileIOPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.GacIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.HostProtectionResource?displayProperty=fullName>
- <xref:System.Security.Permissions.IUnrestrictedPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageContainment?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStorageFilePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.IsolatedStoragePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryCollection?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAccessEntryEnumerator?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.KeyContainerPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionAudio?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionImage?displayProperty=fullName>
- <xref:System.Security.Permissions.MediaPermissionVideo?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionSetAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PermissionState?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.PublisherIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAccess?displayProperty=fullName>
- <xref:System.Security.Permissions.RegistryPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBase?displayProperty=fullName>
- <xref:System.Security.Permissions.ResourcePermissionBaseEntry?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.SecurityPermissionFlag?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.SiteIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StorePermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.StrongNamePublicKeyBlob?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.TypeDescriptorPermissionFlags?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionClipboard?displayProperty=fullName>
- <xref:System.Security.Permissions.UIPermissionWindow?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.UrlIdentityPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionAttribute?displayProperty=fullName>
- <xref:System.Security.Permissions.WebBrowserPermissionLevel?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermission?displayProperty=fullName>
- <xref:System.Security.Permissions.ZoneIdentityPermissionAttribute?displayProperty=fullName>
- [<span data-ttu-id="2c059-143">System.Security.Policy.ApplicationTrust.ApplicationTrust(PermissionSet, IEnumerable\<StrongName>)</span><span class="sxs-lookup"><span data-stu-id="2c059-143">System.Security.Policy.ApplicationTrust.ApplicationTrust(PermissionSet, IEnumerable\<StrongName>)</span></span>](/dotnet/api/system.security.policy.applicationtrust.-ctor#System_Security_Policy_ApplicationTrust__ctor_System_Security_PermissionSet_System_Collections_Generic_IEnumerable_System_Security_Policy_StrongName__)
- <xref:System.Security.Policy.ApplicationTrust.FullTrustAssemblies?displayProperty=fullName>
- <xref:System.Security.Policy.FileCodeGroup?displayProperty=fullName>
- <xref:System.Security.Policy.GacInstalled?displayProperty=fullName>
- <xref:System.Security.Policy.IIdentityPermissionFactory?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.AddNamedPermissionSet(System.Security.NamedPermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.ChangeNamedPermissionSet(System.String,System.Security.PermissionSet)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.GetNamedPermissionSet(System.String)?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet%2A?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyStatement.PermissionSet?displayProperty=fullName>
- <xref:System.Security.Policy.PolicyStatement.%23ctor%2A?displayProperty=fullName>
- <xref:System.Security.Policy.Publisher?displayProperty=fullName>
- <xref:System.Security.Policy.Site?displayProperty=fullName>
- <xref:System.Security.Policy.StrongName?displayProperty=fullName>
- <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=fullName>
- <xref:System.Security.Policy.Url?displayProperty=fullName>
- <xref:System.Security.Policy.Zone?displayProperty=fullName>
- <xref:System.Security.SecurityManager?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermission?displayProperty=fullName>
- <xref:System.ServiceProcess.ServiceControllerPermissionAttribute?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermission?displayProperty=fullName>
- <xref:System.Transactions.DistributedTransactionPermissionAttribute?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermission?displayProperty=fullName>
- <xref:System.Web.AspNetHostingPermissionAttribute?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlLoadPermission?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `P:System.AppDomain.PermissionSet`
- `T:System.Configuration.ConfigurationPermission`
- `T:System.Configuration.ConfigurationPermissionAttribute`
- `T:System.Data.Common.DBDataPermission`
- `T:System.Data.Common.DBDataPermissionAttribute`
- `T:System.Data.Odbc.OdbcPermission`
- `T:System.Data.Odbc.OdbcPermissionAttribute`
- `T:System.Data.OleDb.OleDbPermission`
- `T:System.Data.OleDb.OleDbPermissionAttribute`
- `T:System.Data.OracleClient.OraclePermission`
- `T:System.Data.OracleClient.OraclePermissionAttribute`
- `T:System.Data.SqlClient.SqlClientPermission`
- `T:System.Data.SqlClient.SqlClientPermissionAttribute`
- `T:System.Diagnostics.EventLogPermission`
- `T:System.Diagnostics.EventLogPermissionAttribute`
- `T:System.Diagnostics.PerformanceCounterPermission`
- `T:System.Diagnostics.PerformanceCounterPermissionAttribute`
- `T:System.DirectoryServices.DirectoryServicesPermission`
- `T:System.DirectoryServices.DirectoryServicesPermissionAttribute`
- `T:System.Drawing.Printing.PrintingPermission`
- `T:System.Drawing.Printing.PrintingPermissionAttribute`
- `T:System.Net.DnsPermission`
- `T:System.Net.DnsPermissionAttribute`
- `T:System.Net.Mail.SmtpPermission`
- `T:System.Net.Mail.SmtpPermissionAttribute`
- `T:System.Net.NetworkInformation.NetworkInformationPermission`
- `T:System.Net.NetworkInformation.NetworkInformationPermissionAttribute`
- `T:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermission`
- `T:System.Net.PeerToPeer.Collaboration.PeerCollaborationPermissionAttribute`
- `T:System.Net.PeerToPeer.PnrpPermission`
- `T:System.Net.PeerToPeer.PnrpPermissionAttribute`
- `T:System.Net.SocketPermission`
- `T:System.Net.SocketPermissionAttribute`
- `T:System.Net.WebPermission`
- `T:System.Net.WebPermissionAttribute`
- `T:System.Runtime.InteropServices.AllowReversePInvokeCallsAttribute`
- `T:System.Security.CodeAccessPermission`
- `T:System.Security.HostProtectionException`
- `T:System.Security.IPermission`
- `T:System.Security.IStackWalk`
- `T:System.Security.NamedPermissionSet`
- `T:System.Security.PermissionSet`
- `T:System.Security.Permissions.CodeAccessSecurityAttribute`
- `T:System.Security.Permissions.DataProtectionPermission`
- `T:System.Security.Permissions.DataProtectionPermissionAttribute`
- `T:System.Security.Permissions.DataProtectionPermissionFlags`
- `T:System.Security.Permissions.EnvironmentPermission`
- `T:System.Security.Permissions.EnvironmentPermissionAccess`
- `T:System.Security.Permissions.EnvironmentPermissionAttribute`
- `T:System.Security.Permissions.FileDialogPermission`
- `T:System.Security.Permissions.FileDialogPermissionAccess`
- `T:System.Security.Permissions.FileDialogPermissionAttribute`
- `T:System.Security.Permissions.FileIOPermission`
- `T:System.Security.Permissions.FileIOPermissionAccess`
- `T:System.Security.Permissions.FileIOPermissionAttribute`
- `T:System.Security.Permissions.GacIdentityPermission`
- `T:System.Security.Permissions.GacIdentityPermissionAttribute`
- `T:System.Security.Permissions.HostProtectionAttribute`
- `T:System.Security.Permissions.HostProtectionResource`
- `T:System.Security.Permissions.IUnrestrictedPermission`
- `T:System.Security.Permissions.IsolatedStorageContainment`
- `T:System.Security.Permissions.IsolatedStorageFilePermission`
- `T:System.Security.Permissions.IsolatedStorageFilePermissionAttribute`
- `T:System.Security.Permissions.IsolatedStoragePermission`
- `T:System.Security.Permissions.IsolatedStoragePermissionAttribute`
- `T:System.Security.Permissions.KeyContainerPermission`
- `T:System.Security.Permissions.KeyContainerPermissionAccessEntry`
- `T:System.Security.Permissions.KeyContainerPermissionAccessEntryCollection`
- `T:System.Security.Permissions.KeyContainerPermissionAccessEntryEnumerator`
- `T:System.Security.Permissions.KeyContainerPermissionAttribute`
- `T:System.Security.Permissions.KeyContainerPermissionFlags`
- `T:System.Security.Permissions.MediaPermission`
- `T:System.Security.Permissions.MediaPermissionAttribute`
- `T:System.Security.Permissions.MediaPermissionAudio`
- `T:System.Security.Permissions.MediaPermissionImage`
- `T:System.Security.Permissions.MediaPermissionVideo`
- `T:System.Security.Permissions.PermissionSetAttribute`
- `T:System.Security.Permissions.PermissionState`
- `T:System.Security.Permissions.PrincipalPermission`
- `T:System.Security.Permissions.PrincipalPermissionAttribute`
- `T:System.Security.Permissions.PublisherIdentityPermission`
- `T:System.Security.Permissions.PublisherIdentityPermissionAttribute`
- `T:System.Security.Permissions.ReflectionPermission`
- `T:System.Security.Permissions.ReflectionPermissionAttribute`
- `T:System.Security.Permissions.ReflectionPermissionFlag`
- `T:System.Security.Permissions.RegistryPermission`
- `T:System.Security.Permissions.RegistryPermissionAccess`
- `T:System.Security.Permissions.RegistryPermissionAttribute`
- `T:System.Security.Permissions.ResourcePermissionBase`
- `T:System.Security.Permissions.ResourcePermissionBaseEntry`
- `T:System.Security.Permissions.SecurityAction`
- `T:System.Security.Permissions.SecurityAttribute`
- `T:System.Security.Permissions.SecurityPermission`
- `T:System.Security.Permissions.SecurityPermissionAttribute`
- `T:System.Security.Permissions.SecurityPermissionFlag`
- `T:System.Security.Permissions.SiteIdentityPermission`
- `T:System.Security.Permissions.SiteIdentityPermissionAttribute`
- `T:System.Security.Permissions.StorePermission`
- `T:System.Security.Permissions.StorePermissionAttribute`
- `T:System.Security.Permissions.StorePermissionFlags`
- `T:System.Security.Permissions.StrongNameIdentityPermission`
- `T:System.Security.Permissions.StrongNameIdentityPermissionAttribute`
- `T:System.Security.Permissions.StrongNamePublicKeyBlob`
- `T:System.Security.Permissions.TypeDescriptorPermission`
- `T:System.Security.Permissions.TypeDescriptorPermissionAttribute`
- `T:System.Security.Permissions.TypeDescriptorPermissionFlags`
- `T:System.Security.Permissions.UIPermission`
- `T:System.Security.Permissions.UIPermissionAttribute`
- `T:System.Security.Permissions.UIPermissionClipboard`
- `T:System.Security.Permissions.UIPermissionWindow`
- `T:System.Security.Permissions.UrlIdentityPermission`
- `T:System.Security.Permissions.UrlIdentityPermissionAttribute`
- `T:System.Security.Permissions.WebBrowserPermission`
- `T:System.Security.Permissions.WebBrowserPermissionAttribute`
- `T:System.Security.Permissions.WebBrowserPermissionLevel`
- `T:System.Security.Permissions.ZoneIdentityPermission`
- `T:System.Security.Permissions.ZoneIdentityPermissionAttribute`
- `M:`System.Security.Policy.ApplicationTrust.ApplicationTrust(PermissionSet, IEnumerable<StrongName>)`
- `P:System.Security.Policy.ApplicationTrust.FullTrustAssemblies`
- `T:System.Security.Policy.FileCodeGroup`
- `T:System.Security.Policy.GacInstalled`
- `T:System.Security.Policy.IIdentityPermissionFactory`
- `M:System.Security.Policy.PolicyLevel.AddNamedPermissionSet(System.Security.NamedPermissionSet)`
- `M:System.Security.Policy.PolicyLevel.ChangeNamedPermissionSet(System.String,System.Security.PermissionSet)`
- `M:System.Security.Policy.PolicyLevel.GetNamedPermissionSet(System.String)`
- `Overload:System.Security.Policy.PolicyLevel.RemoveNamedPermissionSet`
- `T:System.Security.Policy.PolicyStatement.PermissionSet`
- `Overload:System.Security.Policy.PolicyStatement.#ctor`
- `T:System.Security.Policy.Publisher`
- `T:System.Security.Policy.Site`
- `T:System.Security.Policy.StrongName`
- `T:System.Security.Policy.StrongNameMembershipCondition`
- `T:System.Security.Policy.Url`
- `T:System.Security.Policy.Zone`
- `T:System.Security.SecurityManager`
- `T:System.ServiceProcess.ServiceControllerPermission`
- `T:System.ServiceProcess.ServiceControllerPermissionAttribute`
- `T:System.Transactions.DistributedTransactionPermission`
- `T:System.Transactions.DistributedTransactionPermissionAttribute`
- `T:System.Web.AspNetHostingPermission`
- `T:System.Web.AspNetHostingPermissionAttribute`
- `T:System.Xaml.Permissions.XamlLoadPermission`

-->
