---
title: セキュリティと実行時のコード生成
description: より低い信頼度のコードの代わりにコードを生成して、より高い信頼度で実行することは、特に呼び出し側がコードの生成に影響を及ぼす可能性がある場合、セキュリティ上の問題となります。
ms.date: 07/15/2020
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: c94da31f464a5272dd3f3c9f767a40ba7ad88a47
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824149"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="bd3c9-103">セキュリティと実行時のコード生成</span><span class="sxs-lookup"><span data-stu-id="bd3c9-103">Security and On-the-Fly Code Generation</span></span>

<span data-ttu-id="bd3c9-104">ライブラリによっては、コードを生成し、それを実行することによって、呼び出し元のためになんらかの処理を行います。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="bd3c9-105">基本的に問題となるのは、より低い信頼度のコードの代わりに生成し、そのコードをより高い信頼度で実行することです。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="bd3c9-106">呼び出し側がコードの生成に影響を及ぼすと問題はさらに悪化するため、安全と考えられるコードだけが生成されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
<span data-ttu-id="bd3c9-107">常に、どのようなコードが生成されているのかを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="bd3c9-108">これは、ユーザーから取得する値を厳しく制御することが必要であることを意味します。これらの値は、引用符で囲まれた文字列、ID、またはそれ以外です。引用符で囲まれた文字列は予期しないコード要素を含まないようにエスケープ処理が必要で、ID は有効な ID かどうかをチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="bd3c9-109">コンパイルされたアセンブリは変更できるため、変更によってその ID に異常な文字が含まれると、セキュリティが脅かされます。このため、ID にも危険性があります。ただし、これがセキュリティ脆弱性になることは稀です。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
<span data-ttu-id="bd3c9-110">リフレクション出力を指定してコードを生成することをお勧めします。これは、上記の多くの問題を防ぐのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
<span data-ttu-id="bd3c9-111">コードをコンパイルするときに、悪意のあるプログラムがなんらかの方法でコードを変更できるかどうかを考慮します。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="bd3c9-112">コンパイラがソース コードを読み取る前、またはコードが .dll を読み込む前に、悪意のあるコードがソース コードを変更できる時間的なすきまがないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="bd3c9-113">ある場合は、ファイル システムのアクセス制御リストを適切に使用して、これらのファイルが格納されているディレクトリを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd3c9-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd3c9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd3c9-114">See also</span></span>

- [<span data-ttu-id="bd3c9-115">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="bd3c9-115">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="bd3c9-116">ASP.NET Core のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="bd3c9-116">ASP.NET Core Security</span></span>](/aspnet/core/security/)
