---
title: -Command (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando devenv del comando per eseguire un comando specificato dopo l'avvio dell Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 871eeddd248255924d8fa0787af9dad73b250c7b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634428"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Esegue il comando specificato dopo l'avvio dell'IDE di Visual Studio.

## <a name="syntax"></a>Sintassi

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>Argomenti

*CommandName*

Obbligatorio. Nome completo di un comando di Visual Studio o del relativo alias, racchiuso tra virgolette doppie. Per altre informazioni sulla sintassi dei comandi e degli alias, vedere [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Commenti

Al completamento dell'avvio, nell'IDE viene eseguito il comando specificato.

::: moniker range="vs-2017"

Se si usa questa opzione la pagina iniziale non viene visualizzata nell'IDE all'avvio.

::: moniker-end

Se un componente aggiuntivo visualizza un comando, è possibile usare questa opzione per avviare il componente aggiuntivo dalla riga di comando. Per altre informazioni, [vedere How to: Control add-ins by using the add-in manager](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Esempio

Il primo esempio avvia Visual Studio ed esegue automaticamente la macro OpenFavoriteFiles.

Il secondo esempio apre una scheda di esplorazione Web all'interno dell'IDE e passa al sito di Microsoft Docs.

Il terzo esempio crea un nuovo file denominato `some_file.cs` e lo apre in un editor di codice.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)
- [Finestra di comando](command-window.md)
