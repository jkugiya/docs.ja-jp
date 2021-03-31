---
description: '詳細情報: アクセス制御リスト エントリを追加または削除する方法 (.NET Framework のみ)'
title: '方法: アクセス制御リスト エントリを追加または削除する (.NET Framework のみ)'
ms.date: 01/14/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
ms.openlocfilehash: 6a880b26dcfb328be4a788bc52596c2dee442511
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775826"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="30f2a-103">方法: アクセス制御リスト エントリを追加または削除する (.NET Framework のみ)</span><span class="sxs-lookup"><span data-stu-id="30f2a-103">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>

<span data-ttu-id="30f2a-104">ファイルまたはディレクトリでアクセス制御リスト (ACL) エントリを追加したり、削除したりするには、<xref:System.Security.AccessControl.FileSecurity> または <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトをファイルまたはディレクトリから取得します。</span><span class="sxs-lookup"><span data-stu-id="30f2a-104">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="30f2a-105">オブジェクトを変更し、ファイルまたはディレクトリに戻します。</span><span class="sxs-lookup"><span data-stu-id="30f2a-105">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="30f2a-106">ACL エントリをファイルに追加するか、ファイルから削除する</span><span class="sxs-lookup"><span data-stu-id="30f2a-106">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="30f2a-107"><xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> メソッドを呼び出して、ファイルの現在の ACL エントリを含む <xref:System.Security.AccessControl.FileSecurity> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="30f2a-107">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="30f2a-108">手順 1. から返された <xref:System.Security.AccessControl.FileSecurity> オブジェクトで ACL エントリの追加または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="30f2a-108">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="30f2a-109">変更を適用するには、<xref:System.Security.AccessControl.FileSecurity> オブジェクトを <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="30f2a-109">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="30f2a-110">ACL エントリをディレクトリに追加するか、ディレクトリから削除する</span><span class="sxs-lookup"><span data-stu-id="30f2a-110">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="30f2a-111"><xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> メソッドを呼び出して、ディレクトリの現在の ACL エントリを含む <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="30f2a-111">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="30f2a-112">手順 1. から返された <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトで ACL エントリの追加または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="30f2a-112">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="30f2a-113">変更を適用するには、<xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="30f2a-113">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30f2a-114">例</span><span class="sxs-lookup"><span data-stu-id="30f2a-114">Example</span></span>  

 <span data-ttu-id="30f2a-115">この例を実行するには、有効なユーザーまたはグループ アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30f2a-115">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="30f2a-116">この例は <xref:System.IO.File> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="30f2a-116">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="30f2a-117"><xref:System.IO.FileInfo>、<xref:System.IO.Directory>、<xref:System.IO.DirectoryInfo> クラスに対して同じ手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="30f2a-117">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
