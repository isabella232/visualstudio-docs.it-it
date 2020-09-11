---
title: Individuazione di Visual Studio | Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93a6f39a9240002cd8008c9368799e10ab63b78d
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012477"
---
# <a name="locate-visual-studio"></a>Individuare Visual Studio

A partire da Visual Studio 2017, è possibile installare più istanze della stessa versione o persino dell'edizione. Questa operazione è utile quando si desidera visualizzare in anteprima nuove funzionalità nel computer di sviluppo primario mantenendo l'installazione precedente. A causa di queste modifiche, non esiste una singola variabile di ambiente o un valore del registro di sistema che è possibile utilizzare per individuare un'istanza. È invece possibile usare un' [API di query com](/dotnet/api/microsoft.visualstudio.setup.configuration) per individuare le istanze in base ai criteri rilevanti per l'estensione.

Si tratta di un'API veloce di sola lettura con pacchetti NuGet disponibili per il codice nativo e gestito.

| Codice | Pacchetto |
| ---- | --- |
| Nativo | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Gestiti | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

È possibile individuare una singola istanza in base a un percorso o al processo corrente oppure enumerare tutte le istanze. Per esempi completi su come individuare Visual Studio [, vedere gli esempi.](https://github.com/Microsoft/vs-setup-samples)

## <a name="tools"></a>Strumenti

Per trovare Visual Studio e altri strumenti negli ambienti di compilazione, script PowerShell, programmi di installazione e altri scenari, sono disponibili diversi strumenti open source che è possibile usare direttamente o ridistribuire insieme a script personalizzati.

| Progetto | Descrizione |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | File eseguibile nativo a file singolo per individuare le istanze che soddisfano i criteri, ad esempio il rilascio o la versione non definitiva, il prodotto installato e i carichi di lavoro installati. Supporta anche la ricerca di Visual Studio 2010 e versioni successive, anche se vengono restituite meno informazioni per Visual Studio 2017 e versioni successive. Per esempi, vedere il [wiki](https://github.com/Microsoft/vswhere/wiki) . |
| [Cmdlet VSSetup](https://github.com/Microsoft/vssetup.powershell) | I cmdlet di PowerShell supportano 2,0 e versioni successive che restituiscono informazioni dettagliate come oggetti che è possibile usare per trovare le istanze in base agli stessi criteri di _vswhere_ e per individuare ancora più proprietà sulle istanze. Per esempi, vedere il [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) . |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Individua automaticamente _VSIX Installer_ e passa la riga di comando tramite per installare un file **. vsix* . Questa funzionalità può essere utile nei programmi di installazione che non dispongono di supporto diretto per le API di query. Per esempi, vedere il [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) . |

## <a name="see-also"></a>Vedere anche

* [Modifiche al programma di installazione di Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Avviare Visual Studio tramite DTE](launch-visual-studio-dte.md)