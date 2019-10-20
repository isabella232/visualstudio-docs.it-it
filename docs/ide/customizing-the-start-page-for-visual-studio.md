---
title: Modificare l'esperienza di avvio
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0a415c8a61e360ed1bcc323214d4144b2875cc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652543"
---
# <a name="customize-startup"></a>Personalizzare l'avvio

È possibile personalizzare l'esperienza di avvio per Visual Studio in diversi modi, ad esempio con l'apertura della soluzione più recente o semplicemente visualizzando un ambiente di sviluppo vuoto.

::: moniker range="vs-2017"

È inoltre possibile visualizzare una pagina iniziale personalizzata, ovvero una pagina XAML Windows Presentation Foundation (WPF) che viene eseguita in una finestra dello strumento e che può eseguire comandi interni a Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Per modificare l'elemento di avvio

1. Nella barra dei menu scegliere **Strumenti** > **Opzioni**.

2. Espandere **Ambiente**, quindi scegliere **Avvio**.

::: moniker range="vs-2017"

3. Nell'elenco **All'avvio** scegliere l'elemento da visualizzare dopo l'avvio di Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

3. Nell'elenco **All'avvio apri** scegliere l'operazione che verrà eseguita all'avvio di Visual Studio. È possibile scegliere tra **Finestra iniziale** (che consente di aprire un progetto nuovo o esistente), **Soluzione più recente** o **Ambiente vuoto**.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Per visualizzare una pagina iniziale personalizzata

È possibile [creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) tramite Visual Studio SDK oppure usarne una creata da qualcun altro. Ad esempio, è possibile trovare pagine iniziali personalizzate in [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Per installare una pagina iniziale personalizzata, aprire il file con estensione *vsix* oppure copiare e incollare i file della pagina iniziale nella cartella *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* nel computer.

### <a name="to-select-which-custom-start-page-to-display"></a>Per selezionare la pagina iniziale personalizzata da visualizzare

1. Nella barra dei menu scegliere **Strumenti** > **Opzioni**.

1. Espandere **Ambiente**, quindi scegliere **Avvio**.

1. Nell'elenco **Personalizza pagina iniziale** scegliere la pagina desiderata.

> [!TIP]
> Se un errore in una pagina iniziale personalizzata determina un arresto anomalo di Visual Studio, è possibile aprire Visual Studio in modalità sicura e quindi impostare l'uso della pagina iniziale predefinita. Vedere [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Vedere anche

- [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end