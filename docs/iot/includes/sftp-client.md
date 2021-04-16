---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594019"
---
[SFTP クライアントを使用して](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md)、開発用コンピューターの発行場所から Raspberry Pi 上の新しいフォルダーにファイルをコピーします。

たとえば、`scp` コマンドを使用して開発用コンピューターから Raspberry Pi にファイルをコピーするには、コマンド プロンプトを開き、次のコマンドを実行します。

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

各値の説明:

- `-r` オプションは、ファイルを再帰的にコピーするように `scp` に指示します。
- */publish-location/* は、前のステップで発行したフォルダーです。
- `pi@raspberypi` は、`<username>@<hostname>` 形式のユーザー名とホスト名です。
- */home/pi/deployment-location/* は、Raspberry Pi 上の新しいフォルダーです。

> [!TIP]
> 最新バージョンの Windows には、インストール済みの `scp` が含まれている OpenSSH があります。
