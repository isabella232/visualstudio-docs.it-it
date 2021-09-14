---
title: Modificare l'esperienza di avvio
description: Informazioni su come personalizzare l'esperienza di avvio Visual Studio con gli strumenti più utili.
ms.custom: SEO-VS-2020
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 0814d4f7c9be48ef881d80d835a28c93921317e8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625956"
---
# <a name="customize-startup"></a>Personalizzare l'avvio

È possibile personalizzare l'esperienza di avvio per Visual Studio in diversi modi, ad esempio con l'apertura della soluzione più recente o semplicemente visualizzando un ambiente di sviluppo vuoto.

::: moniker range="vs-2017"

È inoltre possibile visualizzare una pagina iniziale personalizzata, ovvero una pagina XAML Windows Presentation Foundation (WPF) che viene eseguita in una finestra dello strumento e che può eseguire comandi interni a Visual Studio.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Per modificare l'elemento di avvio

1. Sulla barra dei menu scegliere **Opzioni**  >  **strumenti**.

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

1. Sulla barra dei menu scegliere **Opzioni** > **strumenti**.

1. Espandere **Ambiente**, quindi scegliere **Avvio**.

1. Nell'elenco **Personalizza pagina iniziale** scegliere la pagina desiderata.

> [!TIP]
> Se un errore in una pagina iniziale personalizzata determina un arresto anomalo di Visual Studio, è possibile aprire Visual Studio in modalità sicura e quindi impostare l'uso della pagina iniziale predefinita. Vedere [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Vedi anche

- [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end
