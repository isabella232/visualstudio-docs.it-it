---
title: Esempi di parametri della riga di comando per l'installazione di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tims
manager: ghogen
ms.openlocfilehash: a3b12bfe0c289bfdefc6e3107960fd94889df287
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2017
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Esempi di parametri della riga di comando per l'installazione di Visual Studio 2017
Questo articolo include numerosi esempi personalizzabili che illustrano come [usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

In ogni esempio `vs_enterprise.exe`, `vs_professional.exe` e `vs_community.exe` rappresentano la rispettiva edizione del programma di bootstrap di Visual Studio, ovvero un file di dimensioni ridotte (circa 1 MB) che avvia il processo di download. Se si usa un'edizione diversa, sostituire il nome del programma di bootstrap con quello appropriato.

> [!NOTE]
> Con tutti i comandi sono richiesti privilegi amministrativi elevati. Se il processo non viene avviato da un prompt dei comandi con privilegi elevati, viene visualizzata una richiesta di Controllo dell'account utente.

> [!NOTE]
>  Per concatenare più righe in un unico comando, è possibile usare il carattere `^` alla fine di una riga di comando. In alternativa, è possibile riunire tali righe in un'unica riga. In PowerShell, l'equivalente è il carattere apice inverso (`` ` ``).

* Per installare un'istanza minima di Visual Studio, senza prompt interattivi ma con indicazione dello stato di avanzamento dell'operazione:
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Per installare automaticamente un'istanza desktop di Visual Studio, unitamente al Language Pack per la lingua francese, senza indicazione dello stato di avanzamento dell'operazione fino al completamento dell'installazione del prodotto.
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  Il parametro `--wait` deve essere usato in un file batch. In un file batch l'esecuzione del comando successivo verrà avviata solo dopo il completamento dell'installazione. La variabile di ambiente `%ERRORLEVEL%` conterrà solo il valore restituito del comando, come documentato nella pagina [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Scaricare l'editor principale di Visual Studio (la configurazione di Visual Studio minima). (è incluso solo il Language Pack per la lingua inglese):

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* Per scaricare i carichi di lavoro desktop e Web di .NET unitamente a tutti i componenti consigliati e all'estensione GitHub (è incluso solo il Language Pack per la lingua inglese):
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* Per avviare un'installazione interattiva di tutti i carichi di lavoro e di tutti i componenti disponibili in Visual Studio 2017 Enterprise:
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Per installare una seconda istanza denominata di Visual Studio 2017 Professional in un computer in cui è già installato Visual Studio 2017 Community, includendo il supporto per lo sviluppo Node.js:
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* Per rimuovere il componente Strumenti di profilatura dall'istanza installata predefinita di Visual Studio:
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce,per suggerimenti per la risoluzione dei problemi vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). È anche possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) nell'IDE di Visual Studio o condividere un suggerimento su [UserVoice](https://visualstudio.uservoice.com/forums/121579). È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte. È anche possibile comunicare con Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio) (è necessario un account [GitHub](https://github.com/)).

## <a name="see-also"></a>Vedere anche

 * [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
 * [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Creare un'installazione offline di Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
