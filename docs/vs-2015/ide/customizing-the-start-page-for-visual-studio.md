---
title: Personalizzazione della pagina iniziale per Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ece49968c4a887e89f91feb83fae3de23aa2c282
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211484"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Personalizzazione della pagina iniziale per Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile personalizzare la pagina iniziale di Visual Studio con diverse modalità predefinite, ad esempio facendo in modo che visualizzi la finestra di dialogo **Apri progetto** o che apra la soluzione caricata più di recente. È inoltre possibile visualizzare una pagina iniziale personalizzata, ovvero una pagina XAML Windows Presentation Foundation (WPF) che viene eseguita in una finestra dello strumento e che può eseguire comandi interni a Visual Studio.  
  
## <a name="customizing-the-default-start-page"></a>Personalizzazione della pagina iniziale predefinita  
  
1.  Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  
  
2.  Espandere **Ambiente**, quindi scegliere **Avvio**.  
  
3.  Nell'elenco **At startup** (All'avvio), scegliere l'elemento corrispondente alla personalizzazione desiderata.  
  
## <a name="show-a-custom-start-page"></a>Visualizzare una pagina iniziale personalizzata  
  
1.  Installare una pagina iniziale personalizzata in uno dei modi seguenti:  
  
    -   Installarla da [Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), da un altro sito Web o da una pagina nell'Intranet locale.  
  
        > [!NOTE]
        >  Se si desidera utilizzare una pagina destinata a una versione precedente di Visual Studio, è possibile aggiornarla tramite Visual Studio SDK. Visualizzare [procedura: eseguire l'aggiornamento di una pagina iniziale personalizzata di Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
         Aprire un file. VSIX contenente una pagina iniziale personalizzata oppure copiare e incollare i file della pagina iniziale nel **% USERPROFILE % Documents\Visual Studio 2015\StartPages** cartella nel computer.  
  
    -   Creare una pagina iniziale personalizzata se è stato installato Visual Studio SDK.  
  
         Visualizzare [crearne una nuova pagina iniziale](../misc/creating-your-own-start-page.md).  
  
2.  Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  
  
3.  Espandere **Ambiente**, quindi scegliere **Avvio**.  
  
4.  Nell'elenco **Personalizza pagina iniziale** scegliere la pagina desiderata.  
  
> [!NOTE]
>  Se un errore in una pagina iniziale personalizzata determina un arresto anomalo di Visual Studio, è possibile avviare Visual Studio in modalità sicura e quindi impostarne l'utilizzo della pagina iniziale predefinita. Vedere [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Creazione di pagina iniziale personalizzata](../misc/creating-your-own-start-page.md)



