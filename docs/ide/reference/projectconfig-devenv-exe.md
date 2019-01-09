---
title: Opzione ProjectConfig di DevEnv
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ca481d23757cc9022042db42a6d4be477880367
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967917"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Specifica la configurazione di compilazione da applicare quando si compila, si pulisce, si ricompila o si distribuisce il progetto indicato nell'argomento **/project**.

## <a name="syntax"></a>Sintassi

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argomenti

|||
|-|-|
|/build|Compila il progetto specificato dall'argomento **/project**.|
|/clean|Pulisce tutti i file intermedi e le directory di output creati durante una compilazione.|
|/rebuild|Pulisce e quindi compila il progetto specificato dall'argomento **/project**.|
|/deploy|Specifica che il progetto deve essere distribuito dopo una compilazione o una ricompilazione.|
|*SolnConfigName*|Obbligatorio. Il nome della configurazione di soluzione da applicare alla soluzione indicata in *SolutionName*. Se per la soluzione sono disponibili più piattaforme, è necessario specificare anche la piattaforma, ad esempio **"Debug\|Win32"**.|
|*SolutionName*|Obbligatorio. Il percorso completo e il nome del file della soluzione.|
|/project *ProjName*|Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere nel file di progetto il percorso relativo dalla cartella *SolutionName*, il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.|
|/projectconfig *ProjConfigName*|Facoltativo. Il nome della configurazione di compilazione da applicare al progetto specificato dall'argomento **/project**. Se per la soluzione sono disponibili più piattaforme, è necessario specificare anche la piattaforma, ad esempio **"Debug\|Win32"**.|

## <a name="remarks"></a>Note

L'opzione **/projectconfig** deve essere usata con l'opzione **/project** nell'ambito di un comando **/build**, **/clean**, **/rebuild** o **/deploy**.

Racchiudere le stringhe che includono spazi tra virgolette doppie.

Le informazioni di riepilogo sulle compilazioni, inclusi gli errori, possono essere visualizzate nella finestra di comando o in qualsiasi file di log specificato con l'opzione **/out**.

## <a name="example"></a>Esempio

Il comando seguente compila il progetto "CSharpConsoleApp" usando la configurazione di compilazione "Debug" all'interno della configurazione di soluzione "Debug" di "MySolution":

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)