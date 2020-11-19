---
title: Introduzione con devinilt
description: Guida introduttiva a devinit.
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: d071a49c9996c9f7f161faf676117704fbcbbdcd
ms.sourcegitcommit: 3b9a8aec34c7e835069f4db5c133dd002028180c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94937695"
---
# <a name="getting-started-with-devinit"></a>Introduzione con devinilt

devinit è uno strumento che è possibile usare per consentire a chiunque di ottenere codice ed essere produttivo nel repository eseguendo un semplice comando. È possibile usare devinit per definire tutte le dipendenze a livello di sistema necessarie per il repository, ad esempio SQL Server, Node.js, Docker o IIS. Devinit può richiamare altri strumenti e gestori di pacchetti per installare gli elementi necessari per il repository. È possibile definire le dipendenze in un file JSON denominato [.devinit.json](devinit-json.md) e quindi la persona successiva a usare il repository deve eseguire solo [`devinit init`](devinit-commands.md#init) per installare tutte le dipendenze. Quindi, invece di spendere mezza giornata di onboarding in un nuovo repository, può essere eseguita in pochi minuti.

devinit non è uno strumento di gestione pacchetti o di configurazione di macchina virtuale (VM) in e di se stesso. Si tratta di un task Runner per un file manifesto, denominato [.devinit.json](devinit-json.md), che definisce le dipendenze a livello di sistema necessarie per l'applicazione. Per installare queste dipendenze, devinit si avvale degli strumenti che potrebbero essere già in uso, ad esempio [cioccolato](https://chocolatey.org). È possibile esaminare gli strumenti disponibili nell' [elenco completo](devinit-tool-list.md). Usando questi strumenti invece di distribuire direttamente il software, la devinit ti offre la comodità di usare lo strumento di tua scelta e ti permette di usare le configurazioni esistenti, ad esempio un file di [packages.config](https://chocolatey.org/docs/commands-install#packagesconfig) per cioccolato.  

## <a name="step-1-get-devinit"></a>Passaggio 1: ottenere la devinit

devinit è attualmente disponibile solo come parte degli spazi dei codebase di GitHub quando si usa Visual Studio ed è accessibile dal terminale integrato in Visual Studio. In futuro, la devinit sarà disponibile come parte di Visual Studio.

## <a name="step-2-define-your-environment"></a>Passaggio 2: definire l'ambiente

Il passaggio più importante consiste nel definire l'ambiente di sviluppo in un [.devinit.jssu file](devinit-json.md). Questo file verrà usato da devinit per creare l'ambiente quando si esegue `devinit init` .

Per questo passaggio, prendere in considerazione le istruzioni che si darebbe a qualcuno per iniziare a usare un repository di progetto. Ad esempio, è necessario che sia installato SQL? Una versione specifica di .NET Core? e così via. Quindi, per ognuna di queste dipendenze, cercare uno strumento di devinizzazione corrispondente nell' [elenco di strumenti](devinit-tool-list.md) e aggiungerlo al file del repository `.devinit.json` .

È anche possibile visualizzare una selezione degli esempi nella documentazione degli [esempi](sample-readme.md)oppure consultare l' [esercitazione](tutorial.md).

## <a name="step-3-enjoy"></a>Passaggio 3: divertirsi!

A questo punto, tutti gli utenti devono eseguire la clonazione del repository `devinit init` .

```console
devinit init
```

Se si usano gli [spazi](https://github.com/features/codespaces)dei codebase di GitHub, è possibile configurare `devinit init` per l'esecuzione automatica quando viene effettuato il provisioning del codespace. Per altre informazioni, vedere la [documentazione relativa agli spazi dei documenti devinit e GitHub](devinit-and-codespaces.md).
