---
title: Installare una pagina iniziale personalizzata oppure modificare l'elemento di avvio in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d6bf05e014ff70b221d1ec77c4ee5677764142ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>Personalizzazione della pagina iniziale per Visual Studio

È possibile personalizzare l'esperienza di avvio per Visual Studio in vari modi diversi, ad esempio visualizzando la finestra di dialogo **Apri progetto** o aprendo la soluzione caricata più di recente. È inoltre possibile visualizzare una pagina iniziale personalizzata, ovvero una pagina XAML Windows Presentation Foundation (WPF) che viene eseguita in una finestra dello strumento e che può eseguire comandi interni a Visual Studio.

## <a name="to-change-the-startup-item"></a>Per modificare l'elemento di avvio

1. Nella barra dei menu scegliere **Strumenti**, **Opzioni**.

1. Espandere **Ambiente**, quindi scegliere **Avvio**.

1. Nell'elenco **All'avvio** scegliere l'elemento da visualizzare dopo l'avvio di Visual Studio.

## <a name="to-show-a-custom-start-page"></a>Per visualizzare una pagina iniziale personalizzata

È possibile [creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md) tramite Visual Studio SDK oppure usarne una creata da qualcun altro. Ad esempio, è possibile trovare pagine iniziali personalizzate in [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Per installare una pagina iniziale personalizzata, aprire il file con estensione vsix oppure copiare e incollare i file della pagina iniziale nella cartella **%USERPROFILE%\Documenti\Visual Studio 2017\StartPages** nel computer.

### <a name="to-select-which-custom-start-page-to-display"></a>Per selezionare la pagina iniziale personalizzata da visualizzare

1. Nella barra dei menu scegliere **Strumenti**, **Opzioni**.

1. Espandere **Ambiente**, quindi scegliere **Avvio**.

1. Nell'elenco **Personalizza pagina iniziale** scegliere la pagina desiderata.

> [!NOTE]
> Se un errore in una pagina iniziale personalizzata determina un arresto anomalo di Visual Studio, è possibile avviare Visual Studio in modalità sicura e quindi impostarne l'utilizzo della pagina iniziale predefinita. Vedere [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Vedere anche

[Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md)
