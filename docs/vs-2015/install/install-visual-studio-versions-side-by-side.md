---
title: Installare le versioni Visual Studio Side-by-Side | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 67a564b789d24b11b92b218c2a30673c6bd7baad
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834861"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Installare le versioni Visual Studio Side-by-Side
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile installare questa versione di Visual Studio in un computer in cui è già installata una versione precedente. Se si verifica un errore di installazione, è possibile usare lo [strumento di raccolta dei log](http://go.microsoft.com/fwlink/?LinkId=262077) per raccogliere informazioni sugli errori per poter eseguire il debug dei problemi manualmente.

> [!NOTE]
> Si consiglia di installare le versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nell'ordine nel quale vengono rilasciate. Ad esempio, installare Visual Studio 2013 prima di installare Visual Studio 2015.

 Prima di installare le versioni affiancate, verificare le seguenti condizioni:

-   Se si usa Visual Studio 2015 per aprire una soluzione creata in [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], successivamente è possibile aprire e modificare nuovamente la soluzione nella versione precedente purché non sia stata implementata alcuna funzionalità specifica di Visual Studio 2015.

-   Se si prova a usare Visual Studio 2015 per aprire una soluzione creata in [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] o in una versione precedente, potrebbe essere necessario modificare i progetti e i file per renderli compatibili con Visual Studio 2015. Per altre informazioni, vedere la [conversione, migrazione e aggiornare i progetti di Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) pagina.

-   Se si disinstalla una versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] da un computer in cui sono installate più versioni, le associazioni di file per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verranno rimosse per tutte le versioni. È possibile eseguire di nuovo il mapping di queste associazioni di file tramite il pulsante **Ripristina associazioni file** in **Ambiente**nella pagina **Generale** della finestra di dialogo [Opzioni](../ide/reference/general-environment-options-dialog-box.md) .

-   Visual Studio non aggiorna automaticamente le estensioni, perché non tutte le estensioni sono compatibili. È necessario reinstallare le estensioni dal [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkId=178891) o dall'autore del software.

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
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Esecuzione di un'applicazione JScript su una versione precedente di Common Language Runtime](http://msdn.microsoft.com/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>Vedere anche

- [Installare Visual Studio](../install/install-visual-studio-2015.md)
- [Conversione, migrazione e aggiornamento dei progetti di Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [Compilazione di applicazioni isolate C/C++ e di assembly side-by-side](http://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)