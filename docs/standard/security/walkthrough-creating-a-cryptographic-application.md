---
title: 'チュートリアル: 暗号化アプリケーションの作成'
description: 暗号化アプリケーションの作成について説明します。 Windows フォーム アプリケーション内のコンテンツを暗号化および復号化する方法について説明します。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET], example
- cryptography [NET], cryptographic application example
- cryptography [NET], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 70218d60abb336cdb35fc2e89e62a50b6bd79c67
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830559"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="d1f59-104">チュートリアル: 暗号化アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="d1f59-104">Walkthrough: Creating a Cryptographic Application</span></span>

> [!NOTE]
> <span data-ttu-id="d1f59-105">この記事は Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-105">This article applies to Windows.</span></span>
>
> <span data-ttu-id="d1f59-106">ASP.NET Core の詳細については、「[ASP.NET Core のデータ保護](/aspnet/core/security/data-protection/introduction)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1f59-106">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="d1f59-107">このチュートリアルでは、コンテンツの暗号化および復号化の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-107">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="d1f59-108">コード例は、Windows フォーム アプリケーション向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="d1f59-108">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="d1f59-109">このアプリケーションは、スマート カードを使用するなどの実際のシナリオは示していません。</span><span class="sxs-lookup"><span data-stu-id="d1f59-109">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="d1f59-110">代わりに、暗号化と復号化の基礎を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1f59-110">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
<span data-ttu-id="d1f59-111">このチュートリアルでは、次の暗号化のガイドラインを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-111">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="d1f59-112">自動生成される <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> と <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> を使用すると、対称アルゴリズムである <xref:System.Security.Cryptography.Aes> クラスでデータの暗号化と復号化を行えます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-112">Use the <xref:System.Security.Cryptography.Aes> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="d1f59-113"><xref:System.Security.Cryptography.RSA> 非対称アルゴリズムを使用して、<xref:System.Security.Cryptography.Aes> によって暗号化されたデータのキーの暗号化と復号化を行います。</span><span class="sxs-lookup"><span data-stu-id="d1f59-113">Use the <xref:System.Security.Cryptography.RSA> asymmetric algorithm to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.Aes>.</span></span> <span data-ttu-id="d1f59-114">非対称アルゴリズムは、キーなどの少量のデータに最適です。</span><span class="sxs-lookup"><span data-stu-id="d1f59-114">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d1f59-115">暗号化されたコンテンツを他のユーザーとやり取りするのではなく、自分のコンピューター上のデータを保護する場合は、<xref:System.Security.Cryptography.ProtectedData> クラスの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="d1f59-115">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> class.</span></span>  
  
 <span data-ttu-id="d1f59-116">次の表は、このトピックの暗号化のタスクをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="d1f59-116">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="d1f59-117">タスク</span><span class="sxs-lookup"><span data-stu-id="d1f59-117">Task</span></span>|<span data-ttu-id="d1f59-118">説明</span><span class="sxs-lookup"><span data-stu-id="d1f59-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="d1f59-119">Windows フォーム アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="d1f59-119">Creating a Windows Forms application</span></span>|<span data-ttu-id="d1f59-120">アプリケーションを実行するために必要なコントロールの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-120">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="d1f59-121">グローバル オブジェクトの宣言</span><span class="sxs-lookup"><span data-stu-id="d1f59-121">Declaring global objects</span></span>|<span data-ttu-id="d1f59-122">文字列のパスの変数、<xref:System.Security.Cryptography.CspParameters>、および <xref:System.Security.Cryptography.RSACryptoServiceProvider> を宣言して、<xref:System.Windows.Forms.Form> クラスのグローバル コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-122">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="d1f59-123">非対称キーを作成する</span><span class="sxs-lookup"><span data-stu-id="d1f59-123">Creating an asymmetric key</span></span>|<span data-ttu-id="d1f59-124">非対称の公開キーと秘密キーの値のペアを作成し、これにキー コンテナー名を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-124">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="d1f59-125">ファイルの暗号化</span><span class="sxs-lookup"><span data-stu-id="d1f59-125">Encrypting a file</span></span>|<span data-ttu-id="d1f59-126">暗号化するファイルを選択するダイアログ ボックスを表示し、ファイルを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-126">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="d1f59-127">ファイルの復号化</span><span class="sxs-lookup"><span data-stu-id="d1f59-127">Decrypting a file</span></span>|<span data-ttu-id="d1f59-128">復号化する暗号化されたファイルを選択するダイアログ ボックスを表示し、ファイルを復号化します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-128">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="d1f59-129">秘密キーの取得</span><span class="sxs-lookup"><span data-stu-id="d1f59-129">Getting a private key</span></span>|<span data-ttu-id="d1f59-130">キー コンテナー名を使用して、完全なキーのペアを取得します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-130">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="d1f59-131">公開キーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="d1f59-131">Exporting a public key</span></span>|<span data-ttu-id="d1f59-132">パブリック パラメーターのみで XML ファイルにキーを保存します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-132">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="d1f59-133">公開キーのインポート</span><span class="sxs-lookup"><span data-stu-id="d1f59-133">Importing a public key</span></span>|<span data-ttu-id="d1f59-134">キーを XML ファイルからキー コンテナーに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-134">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="d1f59-135">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="d1f59-135">Testing the application</span></span>|<span data-ttu-id="d1f59-136">このアプリケーションをテストするための手順を一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-136">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="d1f59-137">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d1f59-137">Prerequisites</span></span>  

<span data-ttu-id="d1f59-138">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="d1f59-138">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="d1f59-139"><xref:System.IO> 名前空間と <xref:System.Security.Cryptography> 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="d1f59-139">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="d1f59-140">Windows フォーム アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="d1f59-140">Creating a Windows Forms Application</span></span>  

<span data-ttu-id="d1f59-141">このチュートリアルにあるほとんどのコード例は、ボタン コントロールのイベント ハンドラーとして設計されています。</span><span class="sxs-lookup"><span data-stu-id="d1f59-141">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="d1f59-142">次の表は、サンプル アプリケーションに必要なコントロールと、コード例に一致する必要な名前を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1f59-142">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="d1f59-143">コントロール</span><span class="sxs-lookup"><span data-stu-id="d1f59-143">Control</span></span>|<span data-ttu-id="d1f59-144">名前</span><span class="sxs-lookup"><span data-stu-id="d1f59-144">Name</span></span>|<span data-ttu-id="d1f59-145">テキストのプロパティ (必要に応じて)</span><span class="sxs-lookup"><span data-stu-id="d1f59-145">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="d1f59-146">ファイルの暗号化</span><span class="sxs-lookup"><span data-stu-id="d1f59-146">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="d1f59-147">ファイルの復号化</span><span class="sxs-lookup"><span data-stu-id="d1f59-147">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="d1f59-148">キーの作成</span><span class="sxs-lookup"><span data-stu-id="d1f59-148">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="d1f59-149">公開キーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="d1f59-149">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="d1f59-150">公開キーのインポート</span><span class="sxs-lookup"><span data-stu-id="d1f59-150">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="d1f59-151">秘密キーの取得</span><span class="sxs-lookup"><span data-stu-id="d1f59-151">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="d1f59-152">キーが設定されていません</span><span class="sxs-lookup"><span data-stu-id="d1f59-152">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="d1f59-153">ボタンのイベント ハンドラーを作成するには、Visual Studio デザイナー内でそのボタンをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-153">Double-click the buttons in the Visual Studio designer to create their event handlers.</span></span>
  
## <a name="declaring-global-objects"></a><span data-ttu-id="d1f59-154">グローバル オブジェクトの宣言</span><span class="sxs-lookup"><span data-stu-id="d1f59-154">Declaring Global Objects</span></span>  

<span data-ttu-id="d1f59-155">次のコードをフォームのコンストラクターに追加します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-155">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="d1f59-156">環境とユーザー設定のための文字列変数を編集します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-156">Edit the string variables for your environment and preferences.</span></span>  
  
[!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
[!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="d1f59-157">非対称キーの作成</span><span class="sxs-lookup"><span data-stu-id="d1f59-157">Creating an Asymmetric Key</span></span>  

<span data-ttu-id="d1f59-158">この作業では、<xref:System.Security.Cryptography.Aes> キーの暗号化と復号化を行う非対称キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-158">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.Aes> key.</span></span> <span data-ttu-id="d1f59-159">このキーは、コンテンツの暗号化に使用されたもので、ラベル コントロールにキー コンテナー名を表示します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-159">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="d1f59-160">次のコードを [`Create Keys`] ボタン (`buttonCreateAsmKeys_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-160">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="d1f59-161">ファイルの暗号化</span><span class="sxs-lookup"><span data-stu-id="d1f59-161">Encrypting a File</span></span>  

<span data-ttu-id="d1f59-162">このタスクには、`Encrypt File` ボタンのイベント ハンドラー メソッド (`buttonEncryptFile_Click`) と `EncryptFile` メソッドという 2 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1f59-162">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="d1f59-163">最初のメソッドは、ファイルを選択するためのダイアログ ボックスを表示し、暗号化を実行する 2 番目のメソッドにファイル名を渡します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-163">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
<span data-ttu-id="d1f59-164">暗号化されたコンテンツ、キー、および IV は、すべて 1 つの <xref:System.IO.FileStream> に保存されます。これを暗号化パッケージといいます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-164">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
<span data-ttu-id="d1f59-165">`EncryptFile` メソッドは以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-165">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="d1f59-166">コンテンツを暗号化する <xref:System.Security.Cryptography.Aes> 対称アルゴリズムを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-166">Creates a <xref:System.Security.Cryptography.Aes> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="d1f59-167"><xref:System.Security.Cryptography.Aes> キーを暗号化する <xref:System.Security.Cryptography.RSACryptoServiceProvider> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-167">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
3. <span data-ttu-id="d1f59-168">ソース ファイルの <xref:System.IO.FileStream> の読み取りと暗号化を行う <xref:System.Security.Cryptography.CryptoStream> オブジェクト (バイトのブロック) を使用して、暗号化ファイルの対象の <xref:System.IO.FileStream> オブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-168">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="d1f59-169">暗号化されたキーと IV の長さを決定し、長さの値のバイト配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-169">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="d1f59-170">暗号化されたパッケージにキー、IV、および長さの値を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-170">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="d1f59-171">暗号化パッケージでは、次の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-171">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="d1f59-172">キーの長さ: 0 - 3 バイト</span><span class="sxs-lookup"><span data-stu-id="d1f59-172">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="d1f59-173">IV の長さ: 4 - 7 バイト</span><span class="sxs-lookup"><span data-stu-id="d1f59-173">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="d1f59-174">暗号化されたキー</span><span class="sxs-lookup"><span data-stu-id="d1f59-174">Encrypted key</span></span>  
  
- <span data-ttu-id="d1f59-175">IV</span><span class="sxs-lookup"><span data-stu-id="d1f59-175">IV</span></span>  
  
- <span data-ttu-id="d1f59-176">暗号化テキスト</span><span class="sxs-lookup"><span data-stu-id="d1f59-176">Cipher text</span></span>  
  
 <span data-ttu-id="d1f59-177">キーと IV の長さを使用すると、暗号化パッケージのすべての部分の開始点と長さを決定することができます。これを使用してファイルを復号化します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-177">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="d1f59-178">次のコードを [`Encrypt File`] ボタン (`buttonEncryptFile_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-178">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="d1f59-179">フォームに次の `EncryptFile` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-179">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="d1f59-180">ファイルの復号化</span><span class="sxs-lookup"><span data-stu-id="d1f59-180">Decrypting a File</span></span>  

<span data-ttu-id="d1f59-181">このタスクには、[`Decrypt File`] ボタン (`buttonDecryptFile_Click`) のイベント ハンドラー メソッドと `DecryptFile` メソッドという 2 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1f59-181">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="d1f59-182">最初のメソッドは、ファイルを選択するためのダイアログ ボックスを表示し、復号化を実行する 2 番目のメソッドにファイル名を渡します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-182">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
<span data-ttu-id="d1f59-183">`Decrypt` メソッドは以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-183">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="d1f59-184">コンテンツを復号化するための <xref:System.Security.Cryptography.Aes> 対称アルゴリズムを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-184">Creates an <xref:System.Security.Cryptography.Aes> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="d1f59-185">暗号化されたキーと IV の長さを取得するには、暗号化パッケージの <xref:System.IO.FileStream> の最初の 8 バイトを読み取ってバイト配列にします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-185">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="d1f59-186">キーと IV を暗号化パッケージから抽出してバイト配列にします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-186">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="d1f59-187"><xref:System.Security.Cryptography.Aes> キーを復号化する <xref:System.Security.Cryptography.RSACryptoServiceProvider> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-187">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
5. <span data-ttu-id="d1f59-188"><xref:System.Security.Cryptography.CryptoStream> オブジェクトを使用して、<xref:System.IO.FileStream> の暗号化パッケージの暗号テキスト セクションをバイトのブロックで読み取って復号化し、復号化されたファイルの <xref:System.IO.FileStream> オブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-188">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="d1f59-189">これが終了すると、復号化は完了です。</span><span class="sxs-lookup"><span data-stu-id="d1f59-189">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="d1f59-190">次のコードを、[`Decrypt File`] ボタンの `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-190">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="d1f59-191">フォームに次の `DecryptFile` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-191">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="d1f59-192">公開キーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="d1f59-192">Exporting a Public Key</span></span>

<span data-ttu-id="d1f59-193">この作業では、[`Create Keys`] ボタンによって作成されたキーをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-193">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="d1f59-194">パブリック パラメーターのみがエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-194">It exports only the public parameters.</span></span>  
  
<span data-ttu-id="d1f59-195">このタスクでは、アリスがボブに公開キーを与えるシナリオをシミュレーションします。そうすることで、ボブはアリスのファイルを暗号化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1f59-195">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="d1f59-196">ボブとその公開キーを持つ他のユーザーはファイルを復号化できなくなります。彼らはプライベート パラメーターを持つ完全なキーのペアを持っていないためです。</span><span class="sxs-lookup"><span data-stu-id="d1f59-196">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="d1f59-197">次のコードを [`Export Public Key`] ボタン (`buttonExportPublicKey_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-197">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
[!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="d1f59-198">公開キーのインポート</span><span class="sxs-lookup"><span data-stu-id="d1f59-198">Importing a Public Key</span></span>

<span data-ttu-id="d1f59-199">このタスクでは、[`Export Public Key`] ボタンによって作成されたパブリック パラメーターのみを持つキーを読み込み、キー コンテナー名として設定します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-199">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
<span data-ttu-id="d1f59-200">この作業では、ボブがアリスのファイルを暗号化できるように、ボブがパブリック パラメーターのみを持つアリスのキーを読み込むシナリオをシミュレーションします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-200">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
<span data-ttu-id="d1f59-201">次のコードを [`Import Public Key`] ボタン (`buttonImportPublicKey_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-201">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
[!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="d1f59-202">秘密キーの取得</span><span class="sxs-lookup"><span data-stu-id="d1f59-202">Getting a Private Key</span></span>  

<span data-ttu-id="d1f59-203">この作業では、[`Create Keys`] ボタンを使用して作成されたキーの名前にキー コンテナー名を設定します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-203">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="d1f59-204">キー コンテナーには、プライベート パラメーターを持つ完全なキーのペアが格納されます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-204">The key container will contain the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="d1f59-205">この作業では、アリスが自分の秘密キーを使用してボブが暗号化したファイルを復号化するシナリオをシミュレーションします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-205">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
<span data-ttu-id="d1f59-206">次のコードを [`Get Private Key`] ボタン (`buttonGetPrivateKey_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-206">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
[!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="d1f59-207">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="d1f59-207">Testing the Application</span></span>

<span data-ttu-id="d1f59-208">アプリケーションをビルドしたら、次のテスト シナリオを実行します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-208">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="d1f59-209">キーの作成、暗号化、および復号化を行うには</span><span class="sxs-lookup"><span data-stu-id="d1f59-209">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="d1f59-210">`Create Keys` ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-210">Click the `Create Keys` button.</span></span> <span data-ttu-id="d1f59-211">ラベルはキー名を表示し、完全なキーのペアであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-211">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="d1f59-212">`Export Public Key` ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-212">Click the `Export Public Key` button.</span></span> <span data-ttu-id="d1f59-213">公開キーのパラメーターのエクスポートにより現在のキーは変更されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d1f59-213">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="d1f59-214">[`Encrypt File`] ボタンをクリックして、ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-214">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="d1f59-215">[`Decrypt File`] ボタンをクリックし、暗号化したファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-215">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="d1f59-216">復号化したファイルを調べます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-216">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="d1f59-217">次のシナリオで保持されたキー コンテナーを取得するテストを実行するには、アプリケーションを閉じて再起動します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-217">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="d1f59-218">公開キーを使用して暗号化するには</span><span class="sxs-lookup"><span data-stu-id="d1f59-218">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="d1f59-219">`Import Public Key` ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-219">Click the `Import Public Key` button.</span></span> <span data-ttu-id="d1f59-220">ラベルはキー名を表示し、公開キーのみであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-220">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="d1f59-221">[`Encrypt File`] ボタンをクリックして、ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-221">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="d1f59-222">[`Decrypt File`] ボタンをクリックし、暗号化したファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-222">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="d1f59-223">復号化するには秘密キーが必要であるため、これは失敗します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-223">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="d1f59-224">このシナリオでは、公開キーのみによる別のユーザーのファイルの暗号化をデモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-224">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="d1f59-225">通常、そのユーザーは公開キーのみを与え、秘密キーは復号化のため与えないでおきます。</span><span class="sxs-lookup"><span data-stu-id="d1f59-225">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="d1f59-226">秘密キーを使用して復号化するには</span><span class="sxs-lookup"><span data-stu-id="d1f59-226">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="d1f59-227">`Get Private Key` ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1f59-227">Click the `Get Private Key` button.</span></span> <span data-ttu-id="d1f59-228">ラベルはキー名を表示し、完全なキーのペアであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-228">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="d1f59-229">[`Decrypt File`] ボタンをクリックし、暗号化したファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-229">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="d1f59-230">復号化するための完全なキーのペアがあるため、これは成功します。</span><span class="sxs-lookup"><span data-stu-id="d1f59-230">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f59-231">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1f59-231">See also</span></span>

- <span data-ttu-id="d1f59-232">[暗号化モデル](cryptography-model.md) - 基本クラス ライブラリに暗号化がどのように実装されているかについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="d1f59-232">[Cryptography Model](cryptography-model.md) - Describes how cryptography is implemented in the base class library.</span></span>
- [<span data-ttu-id="d1f59-233">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="d1f59-233">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="d1f59-234">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="d1f59-234">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="d1f59-235">ASP.NET Core のデータ保護</span><span class="sxs-lookup"><span data-stu-id="d1f59-235">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
