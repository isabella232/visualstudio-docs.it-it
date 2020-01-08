---
title: -UseEnv (devenv.exe)
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35808b27964b3ca8fa0488f1be2ce6dc5530b3dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596395"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Avvia Visual Studio e carica alcune variabili di ambiente per la compilazione.

> [!NOTE]
> Questa opzione viene installata con il carico di lavoro **Sviluppo di applicazioni desktop con C++** .

## <a name="syntax"></a>Sintassi

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argomenti

- *SolutionName*

  Percorso completo e nome del file di soluzione.

- *ProjectName*

  Percorso completo e nome del file di progetto.

## <a name="remarks"></a>Note

Questa opzione influisce sull'IDE di Visual Studio nelle proprietà del progetto per **Directory di VC++** . Se si specifica l'opzione `/UseEnv`, il nodo **Directory di VC++** mostra i valori per le variabili di ambiente PATH, INCLUDE, LIBPATH e LIB. Mostra anche i valori per le **directory di origine** e le **directory di esclusione**. In caso contrario, il nodo sostituisce le variabili di ambiente con cinque valori di directory: **directory eseguibili**, **directory di inclusione**, **directory di riferimento**, **directory di libreria**e **directory WinRT della libreria**.

> [!TIP]
> Per accedere alle proprietà del progetto, fare clic con il pulsante destro del mouse su un progetto C++ e scegliere **Proprietà**. Nella finestra di dialogo **Pagine delle proprietà** selezionare **Proprietà di configurazione** e quindi **Directory di VC++** .

Quando viene specificato un nome di progetto con questa opzione, lo strumento visualizza le variabili di ambiente per tutti i progetti nella soluzione padre del progetto.

## <a name="example"></a>Esempio

L'esempio seguente avvia Visual Studio e carica le variabili di ambiente nella pagina delle proprietà della soluzione `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Pagina delle proprietà Directory di VC++ (Windows)](/cpp/build/reference/vcpp-directories-property-page)
