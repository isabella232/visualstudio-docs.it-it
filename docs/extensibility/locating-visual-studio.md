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
ms.openlocfilehash: c13146d0d48dc176417040bcb756bf8069ad3c3e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907301"
---
# <a name="locate-visual-studio"></a>Individuare Visual Studio

A partire da Visual Studio 2017, è possibile installare più istanze della stessa versione o edition anche. Ciò è utile quando si desidera visualizzare in anteprima nuove funzionalità nel computer di sviluppo primario, mantenendo l'installazione precedente. Grazie a queste modifiche, non è disponibile alcun valore di variabile o del Registro di sistema unico ambiente che è possibile usare per individuare un'istanza. In alternativa, è possibile usare una [API di query COM](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) per trovare le istanze in base a criteri appropriati per l'estensione.

Si tratta di un'API veloce, di sola lettura con i pacchetti NuGet disponibile per il codice nativo e gestito.

| Codice | Pacchetto |
| ---- | --- |
| Nativo | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Gestito | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

È possibile individuare una singola istanza, data un percorso o il processo corrente o enumerare tutte le istanze. Visualizzare [esempi](https://github.com/Microsoft/vs-setup-samples) per esempi completi di come individuare Visual Studio.

## <a name="tools"></a>Strumenti

Per trovare Visual Studio e altri strumenti in ambienti di compilazione, gli script PowerShell, i programmi di installazione e altri scenari, sono disponibili numerosi strumenti open source, è possibile usare direttamente o ridistribuire insieme i propri script.

| Progetto | Descrizione |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Singolo file eseguibile nativo per individuare le istanze che soddisfano criteri, ad esempio versione o versioni non definitive, il prodotto sia installato e quali carichi di lavoro siano installati. Supporta anche la ricerca di Visual Studio 2010 e versioni successive, anche se meno informazioni vengano restituite che per Visual Studio 2017 e versioni successive. Vedere le [wiki](https://github.com/Microsoft/vswhere/wiki) per alcuni esempi. |
| [Cmdlet di VSSetup](https://github.com/Microsoft/vssetup.powershell) | I cmdlet di PowerShell supportati 2.0 e versioni più recenti che restituiscono informazioni avanzate come oggetti, è possibile usare per trovare le istanze in base agli stessi criteri _vswhere_ e per individuare proprietà anche altre informazioni sulle istanze. Vedere le [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) per alcuni esempi. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Viene automaticamente individuata _VSIX Installer_ e passa attraverso la riga di comando per installare un **VSIX* file. Questa funzionalità può essere utile per i programmi di installazione che non hanno supporto diretto per l'API di query. Vedere le [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) per alcuni esempi. |

## <a name="see-also"></a>Vedere anche

* [Modifiche all'installazione di Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
