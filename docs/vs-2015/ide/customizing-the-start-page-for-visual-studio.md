---
title: Personalizzazione della pagina iniziale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1c3dfb145e70665156c921cc9a6f740539bc4e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665844"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Personalizzazione della pagina iniziale per Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile personalizzare la pagina iniziale di Visual Studio con diverse modalità predefinite, ad esempio facendo in modo che visualizzi la finestra di dialogo **Apri progetto** o che apra la soluzione caricata più di recente. È inoltre possibile visualizzare una pagina iniziale personalizzata, ovvero una pagina XAML Windows Presentation Foundation (WPF) che viene eseguita in una finestra dello strumento e che può eseguire comandi interni a Visual Studio.

## <a name="customizing-the-default-start-page"></a>Personalizzazione della pagina iniziale predefinita

1. Nella barra dei menu scegliere **Strumenti**, **Opzioni**.

2. Espandere **Ambiente**, quindi scegliere **Avvio**.

3. Nell'elenco **At startup** (All'avvio), scegliere l'elemento corrispondente alla personalizzazione desiderata.

## <a name="show-a-custom-start-page"></a>Visualizzare una pagina iniziale personalizzata

1. Installare una pagina iniziale personalizzata in uno dei modi seguenti:

    - Installarla da [Visual Studio Marketplace](https://marketplace.visualstudio.com/), da un altro sito Web o da una pagina nell'Intranet locale.

        > [!NOTE]
        > Se si desidera utilizzare una pagina destinata a una versione precedente di Visual Studio, è possibile aggiornarla tramite Visual Studio SDK. Vedere [Procedura: aggiornare una pagina iniziale personalizzata di Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Aprire un file con estensione vsix contenente una pagina iniziale personalizzata oppure copiare e incollare i file della pagina iniziale nella cartella **%USERPROFILE% \Documenti\Visual Studio 2015\StartPages** nel computer.

    - Creare una pagina iniziale personalizzata se è stato installato Visual Studio SDK.

         Vedere [Creazione di una pagina iniziale personalizzata](../misc/creating-your-own-start-page.md).

2. Nella barra dei menu scegliere **Strumenti**, **Opzioni**.

3. Espandere **Ambiente**, quindi scegliere **Avvio**.

4. Nell'elenco **Personalizza pagina iniziale** scegliere la pagina desiderata.

> [!NOTE]
> Se un errore in una pagina iniziale personalizzata determina un arresto anomalo di Visual Studio, è possibile avviare Visual Studio in modalità sicura e quindi impostarne l'utilizzo della pagina iniziale predefinita. Vedere [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Vedere anche
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Creazione di una pagina iniziale personalizzata](../misc/creating-your-own-start-page.md)
