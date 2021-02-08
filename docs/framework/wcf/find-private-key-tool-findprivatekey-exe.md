---
description: '詳細情報: 秘密キーの検索ツール (FindPrivateKey.exe)'
title: 秘密キー検索ツール (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 1d87d19e17c1de89c13db6d7ca092eedf630e6ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793286"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="a377e-103">秘密キー検索ツール (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="a377e-103">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="a377e-104">このコマンド ライン ツールを使用して、証明書ストアから秘密キーを取得できます。</span><span class="sxs-lookup"><span data-stu-id="a377e-104">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="a377e-105">たとえば、 *FindPrivateKey.exe* を使用して、証明書ストア内の特定の x.509 証明書に関連付けられている秘密キーファイルの場所と名前を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="a377e-105">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a377e-106">FindPrivateKey ツールは、WCF のサンプルとして付属しています。</span><span class="sxs-lookup"><span data-stu-id="a377e-106">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="a377e-107">サンプルの場所とビルド方法の詳細については、「 [FindPrivateKey](./samples/findprivatekey.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a377e-107">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="a377e-108">構文</span><span class="sxs-lookup"><span data-stu-id="a377e-108">Syntax</span></span>

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="a377e-109">解説</span><span class="sxs-lookup"><span data-stu-id="a377e-109">Remarks</span></span>

<span data-ttu-id="a377e-110">次の表では、秘密キー検索ツール (FindPrivateKey.exe) で使用できる引数とオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a377e-110">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="a377e-111">引数</span><span class="sxs-lookup"><span data-stu-id="a377e-111">Argument</span></span>|<span data-ttu-id="a377e-112">説明</span><span class="sxs-lookup"><span data-stu-id="a377e-112">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="a377e-113">証明書ストアの名前。</span><span class="sxs-lookup"><span data-stu-id="a377e-113">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="a377e-114">証明書ストアの場所。</span><span class="sxs-lookup"><span data-stu-id="a377e-114">The location of the certificate store.</span></span>|

|<span data-ttu-id="a377e-115">オプション</span><span class="sxs-lookup"><span data-stu-id="a377e-115">Option</span></span>|<span data-ttu-id="a377e-116">説明</span><span class="sxs-lookup"><span data-stu-id="a377e-116">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="a377e-117">`/n <`*subjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="a377e-117">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="a377e-118">証明書のサブジェクト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a377e-118">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="a377e-119">`/t <`*拇印*`>`</span><span class="sxs-lookup"><span data-stu-id="a377e-119">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="a377e-120">証明書のサムプリントを指定します。</span><span class="sxs-lookup"><span data-stu-id="a377e-120">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="a377e-121">Certmgr.exe を使用して証明書のサムプリントを取得します。</span><span class="sxs-lookup"><span data-stu-id="a377e-121">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="a377e-122">ファイル名だけを出力します。</span><span class="sxs-lookup"><span data-stu-id="a377e-122">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="a377e-123">ディレクトリだけを出力します。</span><span class="sxs-lookup"><span data-stu-id="a377e-123">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="a377e-124">絶対ファイル名を出力します。</span><span class="sxs-lookup"><span data-stu-id="a377e-124">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="a377e-125">例</span><span class="sxs-lookup"><span data-stu-id="a377e-125">Examples</span></span>

<span data-ttu-id="a377e-126">John Doe の秘密キーを取得するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a377e-126">The following command retrieves the private key for John Doe:</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="a377e-127">次のコマンドは、ローカルコンピューターの秘密キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="a377e-127">The following command retrieves the private key for the local machine:</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
