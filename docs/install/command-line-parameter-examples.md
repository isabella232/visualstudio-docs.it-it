---
title: Esempi di parametri della riga di comando per l'installazione
description: Personalizzare questi esempi per creare la propria installazione da riga di comando di Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5685de34235dcd9b903cbf5be6371ebf3f1e84c3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307544"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Esempi di parametri della riga di comando per l'installazione di Visual Studio

Questo articolo include numerosi esempi personalizzabili che illustrano come [usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

In ogni esempio `vs_enterprise.exe`, `vs_professional.exe` e `vs_community.exe` rappresentano la rispettiva edizione del programma di bootstrap di Visual Studio, ovvero un file di dimensioni ridotte (circa 1 MB) che avvia il processo di download. Se si usa un'edizione diversa, sostituire il nome del programma di bootstrap con quello appropriato.

> [!NOTE]
> Con tutti i comandi sono richiesti privilegi amministrativi elevati. Se il processo non viene avviato da un prompt dei comandi con privilegi elevati, viene visualizzata una richiesta di Controllo dell'account utente.
>
> [!NOTE]
> Per concatenare più righe in un unico comando, è possibile usare il carattere `^` alla fine di una riga di comando. In alternativa, è possibile riunire tali righe in un'unica riga. In PowerShell, l'equivalente è il carattere apice inverso (`` ` ``).

Per gli elenchi dei carichi di lavoro e dei componenti che è possibile installare tramite la riga di comando, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md).

## <a name="using---installpath"></a>Uso di --installPath

* Per installare un'istanza minima di Visual Studio, senza prompt interattivi ma con indicazione dello stato di avanzamento dell'operazione:

  ```shell
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Aggiornare un'istanza di Visual Studio dalla riga di comando, senza prompt interattivi ma con indicazione dello stato di avanzamento dell'operazione:

   ```shell
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Entrambi i comandi sono consigliati. Il primo comando aggiorna il programma di installazione di Visual Studio. Il secondo comando aggiorna l'istanza di Visual Studio. Per evitare una finestra di dialogo di Controllo dell'account utente, eseguire il prompt dei comandi come amministratore.

* Per installare automaticamente un'istanza desktop di Visual Studio, unitamente al Language Pack per la lingua francese, senza indicazione dello stato di avanzamento dell'operazione fino al completamento dell'installazione del prodotto.

  ```shell
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Uso di -- wait

* Usare in file batch o script per attendere che il completamento del programma di installazione di Visual Studio prima che venga eseguito il comando successivo. Per i file batch, una variabile di ambiente conterrà il valore restituito del comando, come documentato nella pagina Usare i parametri della riga di comando `%ERRORLEVEL%` [per Visual Studio](use-command-line-parameters-to-install-visual-studio.md) comando. Alcune utilità di comando richiedono parametri aggiuntivi per attendere il completamento e ottenere il valore restituito del programma di installazione. Di seguito è riportato un esempio dei parametri aggiuntivi usati con il comando script di PowerShell 'Start-Process':

   ```shell
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $process = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   Write-Output $process.ExitCode 
   ```

   oppure

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* Il primo '-wait' viene usato dal programma di installazione di Visual Studio, mentre il secondo '-Wait' viene usato da 'Start-Process' per attendere il completamento. Il parametro '-PassThru' viene usato da 'Start-Process' per usare il codice di uscita del programma di installazione per il valore restituito corrispondente.

## <a name="using---layout"></a>Uso di --layout

* Scaricare l'editor principale di Visual Studio (la configurazione di Visual Studio minima). (è incluso solo il Language Pack per la lingua inglese):

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Per scaricare i carichi di lavoro desktop e Web di .NET unitamente a tutti i componenti consigliati e all'estensione GitHub (è incluso solo il Language Pack per la lingua inglese):

  ```shell
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Uso di --all

* Per avviare un'installazione interattiva di tutti i carichi di lavoro e di tutti i componenti disponibili in Visual Studio Enterprise:

   ```shell
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Uso di --includeRecommended

* Per installare una seconda istanza denominata di Visual Studio Professional in un computer in cui è già installato Visual Studio Community, includendo il supporto per lo sviluppo Node.js:

   ```shell
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Uso di --remove

::: moniker range="vs-2017"

* Per rimuovere il componente Strumenti di profilatura dall'istanza installata predefinita di Visual Studio:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Per rimuovere il componente Strumenti di profilatura dall'istanza installata predefinita di Visual Studio:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range=">=vs-2022"

* Per rimuovere il componente Strumenti di profilatura dall'istanza installata predefinita di Visual Studio:

  ```shell
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Uso di --path

::: moniker range="vs-2017"

Questi parametri della riga di comando sono **una novità nella versione 15.7**. Per altre informazioni, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

* Usando i percorsi di installazione, cache e condivisi:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Usando solo i percorsi di installazione e cache:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Usando solo i percorsi di installazione e condivisi:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Usando solo il percorso di installazione:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Uso di export

::: moniker range="vs-2017"

Questo comando dalla riga di comando è una **novità della versione 15.9**. Per altre informazioni, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

* Uso di export per salvare la selezione di un'installazione:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Uso di export per salvare una nuova selezione personalizzata:

  ```shell
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Uso di --config

::: moniker range="vs-2017"

Questo parametro della riga di comando è una **novità della versione 15.9**. Per altre informazioni, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

* Uso di --config per installare i carichi di lavoro e i componenti di un file di configurazione dell'installazione salvato in precedenza:

  ```shell
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Uso di --config per aggiungere i carichi di lavoro e i componenti a un'installazione esistente:

  ```shell
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Visual Studio Administrator Guide](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
