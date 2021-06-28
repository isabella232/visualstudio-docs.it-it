---
title: Individuazione dei Visual Studio | Microsoft Docs
description: È possibile installare più istanze della stessa versione di Visual Studio. Informazioni su come usare un'API di query COM per trovare l'istanza desiderata.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: cd0fcd294983d6a6567676f06703b4bd1dd376c4
ms.sourcegitcommit: b4cc3dee59421f7089112becf128a369acadaf61
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2021
ms.locfileid: "112990506"
---
# <a name="locate-visual-studio"></a>Individuare Visual Studio

A partire Visual Studio 2017, è possibile installare più istanze della stessa versione o anche della stessa edizione. Ciò è utile quando si vuole visualizzare in anteprima le nuove funzionalità nel computer di sviluppo principale mantenendo l'installazione precedente. A causa di queste modifiche, non esiste una singola variabile di ambiente o valore del Registro di sistema che è possibile usare per individuare un'istanza. È invece possibile usare [un'API di query COM](/dotnet/api/microsoft.visualstudio.setup.configuration) per trovare le istanze in base ai criteri rilevanti per l'estensione.

Si tratta di un'API rapida di sola lettura con pacchetti NuGet disponibili per il codice nativo e gestito.

| Codice | Pacchetto |
| ---- | --- |
| Nativo | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Gestita | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

È possibile individuare una singola istanza in base a un percorso o al processo corrente oppure enumerare tutte le istanze. Vedere [gli esempi](https://github.com/Microsoft/vs-setup-samples) per esempi completi su come individuare Visual Studio.

## <a name="tools"></a>Strumenti

Per trovare Visual Studio e altri strumenti in ambienti di compilazione, script di PowerShell, programmi di installazione e altri scenari, sono disponibili diversi strumenti open source che è possibile usare direttamente o ridistribuire insieme ai propri script.

| Progetto | Descrizione |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Eseguibile nativo a file singolo per individuare le istanze che soddisfano i criteri, ad esempio versione non definitiva, prodotto installato e carichi di lavoro installati. Supporta anche la ricerca Visual Studio 2010 e versione più recente, anche se vengono restituite meno informazioni rispetto a Visual Studio 2017 e più recente. Per [esempi, vedere](https://github.com/Microsoft/vswhere/wiki) il wiki. |
| [Cmdlet di VSSetup](https://github.com/Microsoft/vssetup.powershell) | I cmdlet di PowerShell supportano la versione 2.0 e versioni più nuove che restituiscono informazioni avanzate come oggetti che è possibile usare per trovare istanze in base agli stessi criteri di _vswhere_ e per individuare altre proprietà sulle istanze. Per [esempi, vedere](https://github.com/Microsoft/vssetup.powershell/wiki) il wiki. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Individua automaticamente _VSIXInstaller e_ passa la riga di comando tramite per installare un file **con estensione vsix.* Questa funzionalità può essere utile nei programmi di installazione che non supportano direttamente le API di query. Per [esempi, vedere](https://github.com/Microsoft/vsixbootstrapper/wiki) il wiki. |

## <a name="see-also"></a>Vedere anche

* [Modifiche alla configurazione Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Avviare Visual Studio tramite DTE](launch-visual-studio-dte.md)
