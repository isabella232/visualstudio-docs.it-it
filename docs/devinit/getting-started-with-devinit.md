---
title: Introduzione con devinilt
description: Guida introduttiva a devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ae274e460f4404efa92c4cf3785a3c2e41fd9691
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134077"
---
# <a name="getting-started-with-devinit"></a>Introduzione con devinilt

## <a name="step-1-get-devinit"></a>Passaggio 1: ottenere la devinit

devinit è attualmente disponibile solo come parte degli spazi dei codebase di GitHub quando si usa Visual Studio ed è accessibile dal terminale integrato in Visual Studio. In futuro, la devinit sarà disponibile come parte di Visual Studio.

## <a name="step-2-define-your-environment"></a>Passaggio 2: definire l'ambiente

Il passaggio più importante consiste nel definire l'ambiente di sviluppo in un [ _.devinit.jssu_ file](devinit-json.md). Questo file verrà usato da devinit per creare l'ambiente quando si esegue `devinit init` .

Per questo passaggio, prendere in considerazione le istruzioni che si darebbe a qualcuno per iniziare a usare un repository di progetto. Ad esempio, è necessario che sia installato SQL? Una versione specifica di .NET Core? Via. Quindi, per ognuna di queste dipendenze, cercare uno strumento di devinizzazione corrispondente nell' [elenco di strumenti](devinit-tool-list.md) e aggiungerlo al _.devinit.js_ del repository nel file.

## <a name="step-3-enjoy"></a>Passaggio 3: divertirsi!

A questo punto, tutti gli utenti devono eseguire la clonazione del repository `devinit init` .

```console
devinit init
```

Se si usano gli [spazi](https://github.com/features/codespaces)dei codebase di GitHub, è possibile configurare `devinit init` per l'esecuzione automatica quando viene effettuato il provisioning del codespace. Per altre informazioni, vedere la [documentazione relativa agli spazi dei documenti devinit e GitHub](devinit-and-codespaces.md).
