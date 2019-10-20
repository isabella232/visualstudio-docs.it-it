---
title: -Command (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Command switch
- /Command Devenv switch
- Command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ca9a6550fd5fd141a5f8051d1948ccd626e970b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654601"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)

Esegue il comando specificato dopo l'avvio dell'IDE di Visual Studio.

## <a name="syntax"></a>Sintassi

```shell
devenv /Command CommandName
```

## <a name="arguments"></a>argomenti

*CommandName*

Obbligatorio. Nome completo di un comando di Visual Studio o del relativo alias, racchiuso tra virgolette doppie. Per altre informazioni sulla sintassi dei comandi e degli alias, vedere [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md).

## <a name="remarks"></a>Note

Al completamento dell'avvio, nell'IDE viene eseguito il comando specificato.

::: moniker range="vs-2017"

Se si usa questa opzione la pagina iniziale non viene visualizzata nell'IDE all'avvio.

::: moniker-end

Se un componente aggiuntivo visualizza un comando, è possibile usare questa opzione per avviare il componente aggiuntivo dalla riga di comando. Per altre informazioni, vedere [procedura: controllare i componenti aggiuntivi tramite Gestione componenti](/previous-versions/xwdatdwh(v=vs.140))aggiuntivi.

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
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Finestra di comando](command-window.md)