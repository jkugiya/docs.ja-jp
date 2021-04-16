---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 9235f1bcda7529b71aef542d3a49da08a9d4b59e
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591101"
---
安全でない逆シリアライザーは、信頼されていないデータを逆シリアル化するときに脆弱です。 攻撃者がシリアル化されたデータを変更して予期されない型を追加し、悪意のある副作用を持つオブジェクトを挿入する可能性があります。 たとえば、安全でない逆シリアライザーに対する攻撃では、基になるオペレーティング システムでコマンドが実行されたり、ネットワークを介して通信されたり、ファイルを削除されたりする可能性があります。
