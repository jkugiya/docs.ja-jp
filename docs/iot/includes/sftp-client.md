---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594019"
---
<span data-ttu-id="0a0f5-101">[SFTP クライアントを使用して](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md)、開発用コンピューターの発行場所から Raspberry Pi 上の新しいフォルダーにファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-101">[Using an SFTP client](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), copy the files from the publish location on the development computer to a new folder on the Raspberry Pi.</span></span>

<span data-ttu-id="0a0f5-102">たとえば、`scp` コマンドを使用して開発用コンピューターから Raspberry Pi にファイルをコピーするには、コマンド プロンプトを開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-102">For example, to use the `scp` command to copy files from the development computer to your Raspberry Pi, open a command prompt and execute the following:</span></span>

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

<span data-ttu-id="0a0f5-103">各値の説明:</span><span class="sxs-lookup"><span data-stu-id="0a0f5-103">Where:</span></span>

- <span data-ttu-id="0a0f5-104">`-r` オプションは、ファイルを再帰的にコピーするように `scp` に指示します。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-104">The `-r` option instructs `scp` to copy files recursively.</span></span>
- <span data-ttu-id="0a0f5-105">*/publish-location/* は、前のステップで発行したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-105">*/publish-location/* is the folder you published to in the previous step.</span></span>
- <span data-ttu-id="0a0f5-106">`pi@raspberypi` は、`<username>@<hostname>` 形式のユーザー名とホスト名です。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-106">`pi@raspberypi` is the user and host names in the format `<username>@<hostname>`.</span></span>
- <span data-ttu-id="0a0f5-107">*/home/pi/deployment-location/* は、Raspberry Pi 上の新しいフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-107">*/home/pi/deployment-location/* is the new folder on the Raspberry Pi.</span></span>

> [!TIP]
> <span data-ttu-id="0a0f5-108">最新バージョンの Windows には、インストール済みの `scp` が含まれている OpenSSH があります。</span><span class="sxs-lookup"><span data-stu-id="0a0f5-108">Recent versions of Windows have OpenSSH, which includes `scp`, pre-installed.</span></span>
