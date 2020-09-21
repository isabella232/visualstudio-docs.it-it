---
title: Introduzione con devinilt
description: Guida introduttiva a devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e0c6676b65637840a1b5878e06d6c5861c34e65d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809313"
---
# <a name="getting-started-with-devinit"></a>Introduzione con devinilt

## <a name="step-1-get-devinit"></a>Passaggio 1: ottenere la devinit

devinit è attualmente disponibile solo come parte degli spazi dei codebase di GitHub quando si usa Visual Studio ed è accessibile dal terminale integrato in Visual Studio. In futuro, la devinit sarà disponibile come parte di Visual Studio.

## <a name="step-2-define-your-environment"></a>Passaggio 2: definire l'ambiente

Il passaggio più importante consiste nel definire l'ambiente di sviluppo in un [ _.devinit.jssu_ file](devinit-json.md). Questo file verrà usato da devinit per creare l'ambiente quando si esegue `devinit init` .

Per questo passaggio, prendere in considerazione le istruzioni che si darebbe a qualcuno per iniziare a usare un repository di progetto. Ad esempio, è necessario che sia installato SQL? Una versione specifica di .NET Core? Via. Quindi, per ognuna di queste dipendenze, cercare uno strumento di devinizzazione corrispondente nell' [elenco degli strumenti](devinit-tool-list.md)e aggiungerlo al _.devinit.js_ del repository nel file.

## <a name="step-3-enjoy"></a>Passaggio 3: divertirsi!

A questo punto, tutti gli utenti devono eseguire la clonazione del repository `devinit init` .

```batch
> devinit init
```

Se si usano gli [spazi](https://github.com/features/codespaces)dei codebase di GitHub, è possibile configurare `devinit init` per l'esecuzione automatica quando viene effettuato il provisioning del codespace. Per altre informazioni, vedere la [documentazione relativa agli spazi dei documenti devinit e GitHub](devinit-and-codespaces.md).
