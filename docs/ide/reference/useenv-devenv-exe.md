---
title: -UseEnv (devenv.exe)
ms.date: 01/10/2019
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9006f8a4e6867e9d64db78a40f44e4b852280fe6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934640"
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

- *SolutionName*

  Percorso completo e nome del file di soluzione.

- *ProjectName*

  Percorso completo e nome del file di progetto.

## <a name="remarks"></a>Note

Questa opzione influisce sull'IDE di Visual Studio nelle proprietà del progetto per **Directory di VC++**. Se si specifica l'opzione `/UseEnv`, il nodo **Directory di VC++** mostra i valori per le variabili di ambiente PATH, INCLUDE, LIBPATH e LIB. (Indica anche i valori per **Directory di origine** e **Escludi directory**.) In caso contrario, il nodo sostituisce le variabili di ambiente con cinque valori di directory: **Directory file eseguibili**, **Directory di inclusione**, **Directory riferimenti**, **Directory librerie** e **Directory libreria WinRT**.

> [!TIP]
> Per accedere alle proprietà del progetto, fare clic con il pulsante destro del mouse su un progetto C++ e scegliere **Proprietà**. Nella finestra di dialogo **Pagine delle proprietà** selezionare **Proprietà di configurazione** e quindi **Directory di VC++**.

Quando viene specificato un nome di progetto con questa opzione, lo strumento visualizza le variabili di ambiente per tutti i progetti nella soluzione padre del progetto.

## <a name="example"></a>Esempio

L'esempio seguente avvia Visual Studio e carica le variabili di ambiente nella pagina delle proprietà della soluzione `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Pagina delle proprietà Directory di VC++ (Windows)](/cpp/ide/vcpp-directories-property-page)
