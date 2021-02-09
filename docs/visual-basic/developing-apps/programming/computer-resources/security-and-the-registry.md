---
description: '詳細情報: セキュリティとレジストリ (Visual Basic)'
title: セキュリティとレジストリ
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 2dc6413328bc32c004d281b096ee095d4f827feb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666382"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="d45ef-103">セキュリティとレジストリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d45ef-103">Security and the Registry (Visual Basic)</span></span>

<span data-ttu-id="d45ef-104">ここでは、レジストリにデータを格納するときのセキュリティへの影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="d45ef-104">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="d45ef-105">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="d45ef-105">Permissions</span></span>  

 <span data-ttu-id="d45ef-106">レジストリ キーがアクセス制御リスト (ACL) によって保護されていても、パスワードなど他人に知られたくないデータをプレーン テキストでレジストリに格納するのは危険です。</span><span class="sxs-lookup"><span data-stu-id="d45ef-106">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="d45ef-107">レジストリを操作すると、システム リソースや保護情報への不適切なアクセスが許可され、セキュリティが損なわれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d45ef-107">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="d45ef-108">これらのプロパティを使うには、<xref:System.Security.Permissions.RegistryPermissionAccess> 列挙型の読み書きアクセス許可が必要です。これは、レジストリ変数へのアクセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="d45ef-108">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="d45ef-109">完全な信頼で実行されるコード (既定のセキュリティ ポリシーでは、これはユーザーのローカル ハード ディスクにインストールされているコードです) は、レジストリにアクセスするために必要なアクセス許可を持っています。</span><span class="sxs-lookup"><span data-stu-id="d45ef-109">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="d45ef-110">詳細については、<xref:System.Security.Permissions.RegistryPermission> クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d45ef-110">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="d45ef-111">レジストリ変数は、<xref:System.Security.Permissions.RegistryPermission> を持たないコードがアクセスできるメモリの場所には格納しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d45ef-111">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="d45ef-112">同様に、アクセス許可を付与するときは、ジョブの実行に必要な最低限の特権を付与します。</span><span class="sxs-lookup"><span data-stu-id="d45ef-112">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="d45ef-113">レジストリ アクセス許可のアクセス値は <xref:System.Security.Permissions.RegistryPermissionAccess> 列挙型により定義されます。</span><span class="sxs-lookup"><span data-stu-id="d45ef-113">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="d45ef-114">次の表はそのメンバーの詳細です。</span><span class="sxs-lookup"><span data-stu-id="d45ef-114">The following table details its members.</span></span>  
  
|<span data-ttu-id="d45ef-115">値</span><span class="sxs-lookup"><span data-stu-id="d45ef-115">Value</span></span>|<span data-ttu-id="d45ef-116">レジストリ変数へのアクセス</span><span class="sxs-lookup"><span data-stu-id="d45ef-116">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="d45ef-117">作成、読み取り、書き込み</span><span class="sxs-lookup"><span data-stu-id="d45ef-117">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="d45ef-118">作成</span><span class="sxs-lookup"><span data-stu-id="d45ef-118">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="d45ef-119">アクセス権なし</span><span class="sxs-lookup"><span data-stu-id="d45ef-119">No access</span></span>|  
|`Read`|<span data-ttu-id="d45ef-120">Read</span><span class="sxs-lookup"><span data-stu-id="d45ef-120">Read</span></span>|  
|`Write`|<span data-ttu-id="d45ef-121">Write</span><span class="sxs-lookup"><span data-stu-id="d45ef-121">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="d45ef-122">レジストリ キーの値のチェック</span><span class="sxs-lookup"><span data-stu-id="d45ef-122">Checking Values in Registry Keys</span></span>  

 <span data-ttu-id="d45ef-123">レジストリの値を作成するときは、その値が既存の値である場合の処理を決めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d45ef-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="d45ef-124">悪意のあるユーザーによって作成された別のプロセスが既に値を作成し、アクセス権を持っている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d45ef-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="d45ef-125">レジストリ値にデータを設定すると、そのデータを他のプロセスから利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d45ef-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="d45ef-126">これを回避するには、`GetValue` メソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="d45ef-126">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="d45ef-127">このメソッドは、キーがまだ存在しない場合、`Nothing` を返します。</span><span class="sxs-lookup"><span data-stu-id="d45ef-127">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d45ef-128">Web アプリケーションからレジストリを読み取るとき、現在のユーザーの ID は Web アプリケーションに実装されている認証と偽装によって決まります。</span><span class="sxs-lookup"><span data-stu-id="d45ef-128">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45ef-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="d45ef-129">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="d45ef-130">レジストリからの読み取りとレジストリへの書き込み</span><span class="sxs-lookup"><span data-stu-id="d45ef-130">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
