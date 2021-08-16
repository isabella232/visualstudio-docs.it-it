---
title: -UseEnv (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando Devenv UseEnv per avviare Visual Studio e caricare determinate variabili di ambiente per la compilazione.
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a8c4cd8b54ab7127fb9503cc461281bd176d15aff4320424eb5641eb4929d6ff
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400075"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Avvia Visual Studio e carica alcune variabili di ambiente per la compilazione.

> [!NOTE]
> Questa opzione viene installata con il carico di lavoro **Sviluppo di applicazioni desktop con C++**.

## <a name="syntax"></a>Sintassi

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argomenti

- *Solutionname*

  Percorso completo e nome del file di soluzione.

- *Nome progetto*

  Percorso completo e nome del file di progetto.

## <a name="remarks"></a>Commenti

Questa opzione influisce sull'IDE di Visual Studio nelle proprietà del progetto per **Directory di VC++**. Se si specifica l'opzione `/UseEnv`, il nodo **Directory di VC++** mostra i valori per le variabili di ambiente PATH, INCLUDE, LIBPATH e LIB. Vengono visualizzati anche i valori per **Directory di origine** ed **Escludi** directory. In caso contrario, il nodo sostituisce le variabili di ambiente con cinque valori di directory: **Directory** eseguibili , **Directory** di inclusione **,** Directory di riferimento **,** Directory libreria e Directory **WinRT della libreria**.

> [!TIP]
> Per accedere alle proprietà del progetto, fare clic con il pulsante destro del mouse su un progetto C++ e scegliere **Proprietà**. Nella finestra di dialogo **Pagine delle proprietà** selezionare **Proprietà di configurazione** e quindi **Directory di VC++**.

Quando viene specificato un nome di progetto con questa opzione, lo strumento visualizza le variabili di ambiente per tutti i progetti nella soluzione padre del progetto.

## <a name="example"></a>Esempio

L'esempio seguente avvia Visual Studio e carica le variabili di ambiente nella pagina delle proprietà della soluzione `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Pagina delle proprietà Directory di VC++ (Windows)](/cpp/build/reference/vcpp-directories-property-page)
