---
description: '詳細情報: SQL Server でのデータの暗号化'
title: SQL Server でのデータの暗号化
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: ddf46834c408c98e3e82b1375c13cb6c24ba044b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695919"
---
# <a name="data-encryption-in-sql-server"></a><span data-ttu-id="df2dd-103">SQL Server でのデータの暗号化</span><span class="sxs-lookup"><span data-stu-id="df2dd-103">Data Encryption in SQL Server</span></span>

<span data-ttu-id="df2dd-104">SQL Server には、証明書、非対称キー、対称キーのいずれかを使ってデータを暗号化したり、復号化したりできる関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="df2dd-104">SQL Server provides functions to encrypt and decrypt data using a certificate, asymmetric key, or symmetric key.</span></span> <span data-ttu-id="df2dd-105">これらはすべて内部の証明書ストアで管理されます。</span><span class="sxs-lookup"><span data-stu-id="df2dd-105">It manages all of these in an internal certificate store.</span></span> <span data-ttu-id="df2dd-106">証明書ストアは、1 つ上の層がその下の層を保護する暗号化階層を使用することによって、証明書およびキーを保護します。</span><span class="sxs-lookup"><span data-stu-id="df2dd-106">The store uses an encryption hierarchy that secures certificates and keys at one level with the layer above it in the hierarchy.</span></span> <span data-ttu-id="df2dd-107">SQL Server では、この機能領域をシークレット ストレージと呼びます。</span><span class="sxs-lookup"><span data-stu-id="df2dd-107">This feature area of SQL Server is called Secret Storage.</span></span>  
  
 <span data-ttu-id="df2dd-108">暗号化関数によってサポートされる最速の暗号化方式は対称キーによる暗号化です。</span><span class="sxs-lookup"><span data-stu-id="df2dd-108">The fastest mode of encryption supported by the encryption functions is symmetric key encryption.</span></span> <span data-ttu-id="df2dd-109">この方法は大量のデータを処理する場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="df2dd-109">This mode is suitable for handling large volumes of data.</span></span> <span data-ttu-id="df2dd-110">対称キーは、証明書、パスワードまたは他の対称キーで暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="df2dd-110">The symmetric keys can be encrypted by certificates, passwords or other symmetric keys.</span></span>  
  
## <a name="keys-and-algorithms"></a><span data-ttu-id="df2dd-111">キーとアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="df2dd-111">Keys and Algorithms</span></span>  

 <span data-ttu-id="df2dd-112">SQL Server は、DES、Triple DES、RC2、RC4、128 ビット RC4、DESX、128 ビット AES、192 ビット AES、256 ビット AES など、複数の対称キー暗号化アルゴリズムをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="df2dd-112">SQL Server supports several symmetric key encryption algorithms, including DES, Triple DES, RC2, RC4, 128-bit RC4, DESX, 128-bit AES, 192-bit AES, and 256-bit AES.</span></span> <span data-ttu-id="df2dd-113">アルゴリズムは Windows Crypto API を使って実装されています。</span><span class="sxs-lookup"><span data-stu-id="df2dd-113">The algorithms are implemented using the Windows Crypto API.</span></span>  
  
 <span data-ttu-id="df2dd-114">SQL Server は、オープンする対称キーをデータベース接続のスコープ内で複数管理できます。</span><span class="sxs-lookup"><span data-stu-id="df2dd-114">Within the scope of a database connection, SQL Server can maintain multiple open symmetric keys.</span></span> <span data-ttu-id="df2dd-115">オープンするキーは証明書ストアから取得でき、データを復号化する際に使用できます。</span><span class="sxs-lookup"><span data-stu-id="df2dd-115">An open key is retrieved from the store and is available for decrypting data.</span></span> <span data-ttu-id="df2dd-116">データの一部が復号化されていれば、使用する対称キーを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="df2dd-116">When a piece of data is decrypted, there is no need to specify the symmetric key to use.</span></span> <span data-ttu-id="df2dd-117">暗号化された各値は、どのキーを使って暗号化されたかを示すキー識別子 (キー GUID) を保持します。</span><span class="sxs-lookup"><span data-stu-id="df2dd-117">Each encrypted value contains the key identifier (key GUID) of the key used to encrypt it.</span></span> <span data-ttu-id="df2dd-118">正しいキーが復号化されてオープンされた場合、暗号化されたバイト ストリームとオープンする対称キーとがエンジンによって照合されます。</span><span class="sxs-lookup"><span data-stu-id="df2dd-118">The engine matches the encrypted byte stream to an open symmetric key, if the correct key has been decrypted and is open.</span></span> <span data-ttu-id="df2dd-119">次に、このキーを使って復号化が実行されて、データが返されます。</span><span class="sxs-lookup"><span data-stu-id="df2dd-119">This key is then used to perform decryption and return the data.</span></span> <span data-ttu-id="df2dd-120">正しいキーがオープンされなかった場合は NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="df2dd-120">If the correct key is not open, NULL is returned.</span></span>  
  
 <span data-ttu-id="df2dd-121">データベース内の暗号化されたデータを使用する方法がわかる例については、「[データの列の暗号化](/sql/relational-databases/security/encryption/encrypt-a-column-of-data)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="df2dd-121">For an example that shows how to work with encrypted data in a database, see [Encrypt a Column of Data](/sql/relational-databases/security/encryption/encrypt-a-column-of-data).</span></span>
  
## <a name="external-resources"></a><span data-ttu-id="df2dd-122">外部リソース</span><span class="sxs-lookup"><span data-stu-id="df2dd-122">External Resources</span></span>  

 <span data-ttu-id="df2dd-123">データの暗号化の詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="df2dd-123">For more information on data encryption, see the following resources.</span></span>  
  
|<span data-ttu-id="df2dd-124">リソース</span><span class="sxs-lookup"><span data-stu-id="df2dd-124">Resource</span></span>|<span data-ttu-id="df2dd-125">説明</span><span class="sxs-lookup"><span data-stu-id="df2dd-125">Description</span></span>|  
|-|-|  
|[<span data-ttu-id="df2dd-126">SQL Server の暗号化</span><span class="sxs-lookup"><span data-stu-id="df2dd-126">SQL Server Encryption</span></span>](/sql/relational-databases/security/encryption/sql-server-encryption)|<span data-ttu-id="df2dd-127">SQL Server における暗号化の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="df2dd-127">Provides an overview of encryption in SQL Server.</span></span> <span data-ttu-id="df2dd-128">このトピックには、他の記事へのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="df2dd-128">This topic includes links to additional articles.</span></span>|  
|[<span data-ttu-id="df2dd-129">暗号化階層</span><span class="sxs-lookup"><span data-stu-id="df2dd-129">Encryption Hierarchy</span></span>](/sql/relational-databases/security/encryption/encryption-hierarchy)|<span data-ttu-id="df2dd-130">SQL Server における暗号化の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="df2dd-130">Provides an overview of encryption in SQL Server.</span></span> <span data-ttu-id="df2dd-131">このトピックでは、他の記事へのリンクが提供されています。</span><span class="sxs-lookup"><span data-stu-id="df2dd-131">This topic provides links to additional articles.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df2dd-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="df2dd-132">See also</span></span>

- [<span data-ttu-id="df2dd-133">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="df2dd-133">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="df2dd-134">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="df2dd-134">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="df2dd-135">SQL Server での認証</span><span class="sxs-lookup"><span data-stu-id="df2dd-135">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)
- [<span data-ttu-id="df2dd-136">SQL Server のサーバー ロールとデータベース ロール</span><span class="sxs-lookup"><span data-stu-id="df2dd-136">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)
- [<span data-ttu-id="df2dd-137">SQL Server における所有権とユーザーとスキーマの分離</span><span class="sxs-lookup"><span data-stu-id="df2dd-137">Ownership and User-Schema Separation in SQL Server</span></span>](ownership-and-user-schema-separation-in-sql-server.md)
- [<span data-ttu-id="df2dd-138">SQL Server の承認とアクセス許可</span><span class="sxs-lookup"><span data-stu-id="df2dd-138">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)
- [<span data-ttu-id="df2dd-139">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="df2dd-139">ADO.NET Overview</span></span>](../ado-net-overview.md)
