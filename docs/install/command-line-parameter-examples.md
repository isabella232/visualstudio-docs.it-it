---
title: Esempi di parametri della riga di comando per l'installazione
description: Personalizzare questi esempi per creare la propria installazione da riga di comando di Visual Studio.
ms.date: 11/14/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6584d1b1864712a1c97b8d2405e7b366c5dd69d6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989987"
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Esempi di parametri della riga di comando per l'installazione di Visual Studio 2017

Questo articolo include numerosi esempi personalizzabili che illustrano come [usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

In ogni esempio `vs_enterprise.exe`, `vs_professional.exe` e `vs_community.exe` rappresentano la rispettiva edizione del programma di bootstrap di Visual Studio, ovvero un file di dimensioni ridotte (circa 1 MB) che avvia il processo di download. Se si usa un'edizione diversa, sostituire il nome del programma di bootstrap con quello appropriato.

> [!NOTE]
> Con tutti i comandi sono richiesti privilegi amministrativi elevati. Se il processo non viene avviato da un prompt dei comandi con privilegi elevati, viene visualizzata una richiesta di Controllo dell'account utente.
>
> [!NOTE]
>  Per concatenare più righe in un unico comando, è possibile usare il carattere `^` alla fine di una riga di comando. In alternativa, è possibile riunire tali righe in un'unica riga. In PowerShell, l'equivalente è il carattere apice inverso (`` ` ``).

## <a name="using---installpath"></a>Uso di --installPath

* Per installare un'istanza minima di Visual Studio, senza prompt interattivi ma con indicazione dello stato di avanzamento dell'operazione:

  ```cmd
  vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Aggiornare un'istanza di Visual Studio dalla riga di comando, senza prompt interattivi ma con indicazione dello stato di avanzamento dell'operazione:

  ```cmd
  vs_enterprise.exe --update --quiet --wait
  vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
  ```

  > [!NOTE]
  > Entrambi i comandi sono necessari. Il primo comando aggiorna il programma di installazione di Visual Studio. Il secondo comando aggiorna l'istanza di Visual Studio. Per evitare una finestra di dialogo di Controllo dell'account utente, eseguire il prompt dei comandi come amministratore.

* Per installare automaticamente un'istanza desktop di Visual Studio, unitamente al Language Pack per la lingua francese, senza indicazione dello stato di avanzamento dell'operazione fino al completamento dell'installazione del prodotto.

  ```cmd
  vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

  > [!NOTE]
  > Il parametro `--wait` deve essere usato in un file batch. In un file batch l'esecuzione del comando successivo verrà avviata solo dopo il completamento dell'installazione. La variabile di ambiente `%ERRORLEVEL%` conterrà solo il valore restituito del comando, come documentato nella pagina [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

## <a name="using---layout"></a>Uso di --layout

* Scaricare l'editor principale di Visual Studio (la configurazione di Visual Studio minima). (è incluso solo il Language Pack per la lingua inglese):

  ```cmd
  vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Per scaricare i carichi di lavoro desktop e Web di .NET unitamente a tutti i componenti consigliati e all'estensione GitHub (è incluso solo il Language Pack per la lingua inglese):

  ```cmd
  vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---includerecommended"></a>Uso di --includeRecommended

* Per avviare un'installazione interattiva di tutti i carichi di lavoro e di tutti i componenti disponibili in Visual Studio 2017 Enterprise:

  ```cmd
  vs_enterprise.exe --all --includeRecommended --includeOptional
  ```

* Per installare una seconda istanza denominata di Visual Studio 2017 Professional in un computer in cui è già installato Visual Studio 2017 Community, includendo il supporto per lo sviluppo Node.js:

  ```cmd
  vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Uso di --remove

* Per rimuovere il componente Strumenti di profilatura dall'istanza installata predefinita di Visual Studio:

  ```cmd
  vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

## <a name="using---path"></a>Uso di --path

Questi parametri della riga di comando sono **una novità nella versione 15.7**. Per altre informazioni, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Usando i percorsi di installazione, cache e condivisi:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Usando solo i percorsi di installazione e cache:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Usando solo i percorsi di installazione e condivisi:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Usando solo il percorso di installazione:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Uso di export

Questo comando dalla riga di comando è una **novità della versione 15.9**. Per altre informazioni, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Uso di export per salvare la selezione di un'installazione:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
```

* Uso di export per salvare una nuova selezione personalizzata:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
```

## <a name="using---config"></a>Uso di --config

Questo parametro della riga di comando è una **novità della versione 15.9**. Per altre informazioni, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Uso di --config per installare i carichi di lavoro e i componenti di un file di configurazione dell'installazione salvato in precedenza:

```cmd
vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
```

* Uso di --config per aggiungere i carichi di lavoro e i componenti a un'installazione esistente:

```cmd
vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
```


[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Creare un'installazione offline di Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
