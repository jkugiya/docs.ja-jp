---
description: '詳細情報: UnsafeNclNativeMethods クラス'
title: UnsafeNclNativeMethods クラス (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fa1084efddae0ba5cbfc9a949dcd94d2c64f3272
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699494"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="6bc9f-103">UnsafeNclNativeMethods クラス</span><span class="sxs-lookup"><span data-stu-id="6bc9f-103">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="6bc9f-104">Unsafe ネイティブネットワークメソッドをインポートするクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6bc9f-104">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="6bc9f-105">このクラスは継承できません。</span><span class="sxs-lookup"><span data-stu-id="6bc9f-105">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="6bc9f-106">このクラスは内部的なものであり、コードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="6bc9f-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6bc9f-107">Microsoft では、どのような状況でも、実稼働アプリケーションでのこのクラスの使用はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6bc9f-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="6bc9f-108">Pipki クラス</span><span class="sxs-lookup"><span data-stu-id="6bc9f-108">NativePKI class</span></span>

<span data-ttu-id="6bc9f-109">crypt32.dll からインポートされたメソッドを格納します。</span><span class="sxs-lookup"><span data-stu-id="6bc9f-109">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="6bc9f-110">これらのメソッドは、ハイパーテキスト転送プロトコルセキュア (HTTPS) を使用する場合に証明書を処理します。</span><span class="sxs-lookup"><span data-stu-id="6bc9f-110">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="6bc9f-111">このクラスは継承できません。</span><span class="sxs-lookup"><span data-stu-id="6bc9f-111">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="6bc9f-112">Pipki. FindClientCertificates メソッド</span><span class="sxs-lookup"><span data-stu-id="6bc9f-112">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="6bc9f-113">サーバーに送信できる使用可能なクライアント証明書を検出します。</span><span class="sxs-lookup"><span data-stu-id="6bc9f-113">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="6bc9f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="6bc9f-114">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="6bc9f-115">使用可能なクライアント証明書のコレクション。</span><span class="sxs-lookup"><span data-stu-id="6bc9f-115">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="6bc9f-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="6bc9f-116">Requirements</span></span>

<span data-ttu-id="6bc9f-117">**名前空間:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6bc9f-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6bc9f-118">**アセンブリ:** システム (System.dll)</span><span class="sxs-lookup"><span data-stu-id="6bc9f-118">**Assembly:** System (in System.dll)</span></span>
