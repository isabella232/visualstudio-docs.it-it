---
title: Opzione Build (DevEnv)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 777347ba36cf3443a509d1d6c8c44c23a86901e0
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764969"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Consente di compilare una soluzione con un file di configurazione della soluzione specificato.

## <a name="syntax"></a>Sintassi

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Argomenti

|||
|-|-|
|*SolutionName*|Obbligatorio. Il percorso completo e il nome del file della soluzione.|
|*SolnConfigName*|Obbligatorio. Nome della configurazione della soluzione da usare per compilare la soluzione indicata in *SolutionName*. Se per la soluzione sono disponibili più piattaforme, è necessario specificare anche la piattaforma, ad esempio **"Debug\|Win32"**.|
|/project *ProjName*|Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere nel file di progetto il percorso relativo dalla cartella *SolutionName*, il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.|
|/projectconfig *ProjConfigName*|Facoltativo. Nome della configurazione di compilazione del progetto da usare per la compilazione del progetto denominato. Se per il progetto sono disponibili più piattaforme, è necessario specificare anche la piattaforma, ad esempio **"Debug\|Win32"**.|

## <a name="remarks"></a>Note

- L'opzione **/build** esegue la stessa funzione del comando di menu **Compila soluzione** nell'ambiente di sviluppo integrato (IDE).

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo sulle compilazioni, inclusi gli errori, possono essere visualizzate nella finestra di comando o in qualsiasi file di log specificato con l'opzione **/out**.

- L'opzione **/build** esegue la compilazione dei soli progetti modificati dopo l'ultima compilazione. Per compilare tutti i progetti in una soluzione, usare [/rebuild](../../ide/reference/rebuild-devenv-exe.md).

- Se viene visualizzato il messaggio di errore **Configurazione progetto non valida**, assicurarsi di aver specificato la piattaforma di una soluzione o di un progetto, ad esempio **"Debug\|Win32"**.

## <a name="example"></a>Esempio

Il comando seguente compila il progetto "CSharpConsoleApp" usando la configurazione di compilazione "Debug" all'interno della configurazione di soluzione "Debug" di "MySolution".

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedere anche

- [Compilare e pulire progetti e soluzioni](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)