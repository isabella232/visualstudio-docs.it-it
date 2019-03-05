---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6daa21f9db7eef9a651577ad829d884dccf353dc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717520"
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

## <a name="remarks"></a>Osservazioni

Al completamento dell'avvio, nell'IDE viene eseguito il comando specificato.

::: moniker range="vs-2017"

Se si usa questa opzione la pagina iniziale non viene visualizzata nell'IDE all'avvio.

::: moniker-end

Se un componente aggiuntivo visualizza un comando, è possibile usare questa opzione per avviare il componente aggiuntivo dalla riga di comando. Per altre informazioni, vedere [Procedura: Controllare i componenti aggiuntivi tramite Gestione componenti aggiuntivi](/previous-versions/xwdatdwh(v=vs.140)).

## <a name="example"></a>Esempio

Il primo esempio avvia Visual Studio ed esegue automaticamente la macro OpenFavoriteFiles.

Il secondo esempio apre una scheda di esplorazione Web all'interno dell'IDE e passa al sito di Microsoft Docs.

Il terzo esempio crea un nuovo file denominato `some_file.cs` e lo apre in un editor di codice.

```shell
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"

devenv /command "navigate https://docs.microsoft.com/"

devenv /command "nf some_file.cs"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
- [Finestra di comando](command-window.md)