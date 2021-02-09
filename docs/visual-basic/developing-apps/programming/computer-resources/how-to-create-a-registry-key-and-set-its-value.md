---
description: '詳細情報: 方法:レジストリ キーを作成し、その値を設定する (Visual Basic)'
title: '方法: レジストリ キーを作成し、その値を設定する'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 73a6f5b2a092bb05df704fe6b9954ccbe13b5d90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797732"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="bb404-103">方法: レジストリ キーを作成し、その値を設定する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb404-103">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="bb404-104">レジストリ キーを作成するには、`My.Computer.Registry` オブジェクトの `CreateSubKey` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb404-104">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="bb404-105">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="bb404-105">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="bb404-106">レジストリ キーを作成するには</span><span class="sxs-lookup"><span data-stu-id="bb404-106">To create a registry key</span></span>

- <span data-ttu-id="bb404-107">`CreateSubKey` メソッドを使用し、キーを入れるハイブとキー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb404-107">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="bb404-108">パラメーター `Subkey` では、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="bb404-108">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="bb404-109">この例では、HKEY_CURRENT_USER の下にレジストリ キー `MyTestKey` を作成します。</span><span class="sxs-lookup"><span data-stu-id="bb404-109">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="bb404-110">レジストリ キーを作成し、それに値を設定するには</span><span class="sxs-lookup"><span data-stu-id="bb404-110">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="bb404-111">`CreateSubkey` メソッドを使用し、キーを入れるハイブとキー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb404-111">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="bb404-112">この例では、HKEY_CURRENT_USER の下にレジストリ キー `MyTestKey` を作成します。</span><span class="sxs-lookup"><span data-stu-id="bb404-112">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="bb404-113">値は、`SetValue` メソッドを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="bb404-113">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="bb404-114">この例では、文字列値</span><span class="sxs-lookup"><span data-stu-id="bb404-114">This example sets the string value.</span></span> <span data-ttu-id="bb404-115">"MyTestKeyValue" を "This is a test value" に設定します。</span><span class="sxs-lookup"><span data-stu-id="bb404-115">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="bb404-116">例</span><span class="sxs-lookup"><span data-stu-id="bb404-116">Example</span></span>

<span data-ttu-id="bb404-117">この例では、HKEY_CURRENT_USER の下にレジストリ キー `MyTestKey` を作成し、文字列値 `MyTestKeyValue` を `This is a test value` に設定します。</span><span class="sxs-lookup"><span data-stu-id="bb404-117">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="bb404-118">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="bb404-118">Robust Programming</span></span>

<span data-ttu-id="bb404-119">レジストリの構造を調べて、キーの適切な場所を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="bb404-119">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="bb404-120">たとえば、現在のユーザーの HKEY_CURRENT_USER\Software キーを開き、会社名のキーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="bb404-120">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="bb404-121">その後で、会社名のキーにレジストリ値を追加します。</span><span class="sxs-lookup"><span data-stu-id="bb404-121">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="bb404-122">Web アプリケーションからレジストリを読み取る際、現在のユーザーは Web アプリケーションに実装されている認証と偽装によります。</span><span class="sxs-lookup"><span data-stu-id="bb404-122">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="bb404-123">ローカル コンピューター (<xref:Microsoft.Win32.Registry.LocalMachine>) よりもユーザー フォルダー (<xref:Microsoft.Win32.Registry.CurrentUser>) にデータを書き込む方が安全です。</span><span class="sxs-lookup"><span data-stu-id="bb404-123">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="bb404-124">レジストリの値を作成するときは、その値が既存の値である場合の処理を決めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb404-124">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="bb404-125">悪意のあるユーザーによって作成された別のプロセスが既に値を作成し、アクセス権を持っている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb404-125">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="bb404-126">レジストリ値にデータを設定すると、そのデータを他のプロセスから利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bb404-126">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="bb404-127">これを回避するには、<xref:Microsoft.Win32.RegistryKey.GetValue%2A> メソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="bb404-127">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="bb404-128">このメソッドは、キーがまだ存在しない場合、`Nothing` を返します。</span><span class="sxs-lookup"><span data-stu-id="bb404-128">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="bb404-129">レジストリ キーがアクセス制御リスト (ACL: Access Control List) によって保護されていても、パスワードなど他人に知られたくないデータをプレーン テキストでレジストリに格納するのは危険です。</span><span class="sxs-lookup"><span data-stu-id="bb404-129">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="bb404-130">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb404-130">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="bb404-131">キーの名前が `Nothing` である場合 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="bb404-131">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="bb404-132">レジストリ キーを作成するためのアクセス許可がユーザーにない場合 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="bb404-132">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="bb404-133">キー名が 255 文字の制限を超えている場合 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="bb404-133">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="bb404-134">キーが閉じている場合 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="bb404-134">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="bb404-135">レジストリ キーが読み取り専用の場合 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="bb404-135">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="bb404-136">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="bb404-136">.NET Framework Security</span></span>

<span data-ttu-id="bb404-137">このプロセスを実行するには、アセンブリに対して <xref:System.Security.Permissions.RegistryPermission> クラスで特権レベルが許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb404-137">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="bb404-138">部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないために例外をスローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb404-138">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="bb404-139">同様に、ユーザーには、設定に対する作成や書き込みを行うための適切な ACL が必要です。</span><span class="sxs-lookup"><span data-stu-id="bb404-139">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="bb404-140">たとえば、コード アクセス セキュリティのアクセス許可を持つローカル アプリケーションには、オペレーティング システムのアクセス許可がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb404-140">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="bb404-141">詳しくは、「[コード アクセス セキュリティの基礎](../../../../framework/misc/code-access-security-basics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bb404-141">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb404-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb404-142">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="bb404-143">レジストリからの読み取りとレジストリへの書き込み</span><span class="sxs-lookup"><span data-stu-id="bb404-143">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="bb404-144">コード アクセス セキュリティの基礎</span><span class="sxs-lookup"><span data-stu-id="bb404-144">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
