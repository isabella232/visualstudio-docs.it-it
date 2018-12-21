---
title: Installare una pagina iniziale personalizzata o modificare l'elemento di avvio
ms.date: 02/01/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8f09302a459e31406d69596d43b5c39a67c8268
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064047"
---
# <a name="customize-the-start-page-for-visual-studio"></a>Personalizzazione della pagina iniziale per Visual Studio

È possibile personalizzare l'esperienza di avvio per Visual Studio in vari modi diversi, ad esempio visualizzando la finestra di dialogo **Apri progetto** o aprendo la soluzione caricata più di recente. È inoltre possibile visualizzare una pagina iniziale personalizzata, ovvero una pagina XAML Windows Presentation Foundation (WPF) che viene eseguita in una finestra dello strumento e che può eseguire comandi interni a Visual Studio.

## <a name="to-change-the-startup-item"></a>Per modificare l'elemento di avvio

1. Nella barra dei menu scegliere **Strumenti** > **Opzioni**.

1. Espandere **Ambiente**, quindi scegliere **Avvio**.

1. Nell'elenco **All'avvio** scegliere l'elemento da visualizzare dopo l'avvio di Visual Studio.

## <a name="to-show-a-custom-start-page"></a>Per visualizzare una pagina iniziale personalizzata

È possibile [creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) tramite Visual Studio SDK oppure usarne una creata da qualcun altro. Ad esempio, è possibile trovare pagine iniziali personalizzate in [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Per installare una pagina iniziale personalizzata, aprire il file con estensione *vsix* oppure copiare e incollare i file della pagina iniziale nella cartella *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* nel computer.

### <a name="to-select-which-custom-start-page-to-display"></a>Per selezionare la pagina iniziale personalizzata da visualizzare

1. Nella barra dei menu scegliere **Strumenti** > **Opzioni**.

1. Espandere **Ambiente**, quindi scegliere **Avvio**.

1. Nell'elenco **Personalizza pagina iniziale** scegliere la pagina desiderata.

> [!NOTE]
> Se un errore in una pagina iniziale personalizzata determina un arresto anomalo di Visual Studio, è possibile avviare Visual Studio in modalità sicura e quindi impostarne l'utilizzo della pagina iniziale predefinita. Vedere [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Vedere anche

- [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md)