---
title: Installare le versioni Visual Studio Side-by-Side | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: ae67e83b2f1444c09129ed5242afac2c3939c954
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532232"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Installare le versioni Visual Studio Side-by-Side
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile installare questa versione di Visual Studio in un computer in cui è già installata una versione precedente. Se si verifica un errore di installazione, è possibile usare lo [strumento di raccolta dei log](http://go.microsoft.com/fwlink/?LinkId=262077) per raccogliere informazioni sugli errori per poter eseguire il debug dei problemi manualmente.  
  
> [!NOTE]
>  È consigliabile installare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] versioni nell'ordine in cui sono state rilasciate. Ad esempio, installare Visual Studio 2013 prima di installare Visual Studio 2015.  
  
 Prima di installare le versioni affiancate, verificare le seguenti condizioni:  
  
-   Se si usa Visual Studio 2015 per aprire una soluzione creata in [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], in un secondo momento è possibile aprire e modificare nuovamente la soluzione nella versione precedente purché non sia stata implementata alcuna funzionalità specifica di Visual Studio 2015.  
  
-   Se si prova a usare Visual Studio 2015 per aprire una soluzione creata in [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] o una versione precedente, potrebbe essere necessario modificare i progetti e file per renderli compatibili con Visual Studio 2015. Per altre informazioni, vedere la [conversione, migrazione e aggiornare i progetti di Visual Studio](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md) pagina.  
  
-   Se si disinstalla una versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] da un computer in cui sono installate più versioni, le associazioni di file per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verranno rimosse per tutte le versioni. È possibile modificare il mapping di queste associazioni di file usando il **Ripristina associazioni File** pulsante la **ambiente**, **generali** pagina del [opzioni](../ide/reference/general-environment-options-dialog-box.md) finestra di dialogo.  
  
-   Visual Studio non aggiorna automaticamente le estensioni, perché non tutte le estensioni sono compatibili. È necessario reinstallare le estensioni da [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=178891) o dall'autore del software.  
  
## <a name="net-framework-versions-and-side-by-side-installations"></a>Versioni di .NET Framework e installazioni affiancate  
  
-   I progetti Visual Basic, Visual C# e Visual F# usano l'opzione **Framework di destinazione** in **Creazione progetti** per specificare la versione di .NET Framework da usare. Per un progetto C++ è possibile modificare manualmente il framework di destinazione modificando il file con estensione vcxproj. Per altre informazioni, vedere [compatibilità delle versioni](http://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).  
  
     Quando si crea un progetto, è possibile specificare a quale versione di .NET Framework è destinato il progetto nell'elenco **.NET Framework** della finestra di dialogo **Nuovo progetto** .  
  
     Per informazioni specifiche del linguaggio, vedere l'argomento corrispondente nella tabella seguente.  
  
    |Linguaggio|Argomento|  
    |--------------|-----------|  
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Pagina Applicazione, Creazione progetti (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C#|[Pagina Applicazione, Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F#|[Configurazione di progetti](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|  
    |C++|[Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|  
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Esegue un'applicazione JScript su una versione precedente di Common Language Runtime](http://msdn.microsoft.com/en-us/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## <a name="see-also"></a>Vedere anche  
 [Installare Visual Studio](../install/install-visual-studio-2015.md) [conversione, migrazione e aggiornare i progetti di Visual Studio](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md)   
 [Creazione di C/C++ applicazioni isolate e assembly Side-by-side](http://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)   
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)