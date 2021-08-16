---
title: Aggiornare ed eseguire la migrazione Office soluzioni
description: È necessario aggiornare il progetto per usarlo nelle versioni correnti di Visual Studio se si dispone di un progetto offince creato in una versione precedente di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: af09d705ddeb0fdbf01244ee085d93fb54d52ac7969c8e1e6de9917abc32b431
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384145"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Aggiornare ed eseguire la migrazione Office soluzioni
  Se si dispone di un progetto di Microsoft Office che è stato creato in una versione precedente di Visual Studio, è necessario aggiornare il progetto per usarlo nella versione corrente di Visual Studio. Per aggiornare un progetto di Microsoft Office, aprirlo in una versione di Visual Studio che include Microsoft Office Developer Tools. Per altre informazioni sulle versioni di Visual Studio che includono gli strumenti di sviluppo Microsoft Office, vedere Configurare un computer per sviluppare Office [soluzioni](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio non può aggiornare i progetti modello di form InfoPath creati usando versioni precedenti di Visual Studio. Questi tipi di progetti non sono supportati nella versione corrente di Visual Studio.

## <a name="changes-to-upgraded-projects"></a>Modifiche ai progetti aggiornati
 Quando si aggiorna un progetto di Microsoft Office, Visual Studio modifica il progetto in base ai seguenti elementi:

- Strumenti Visual Studio 2010 per Office runtime. Per altre informazioni, vedere panoramica [Visual Studio Tools per Office runtime.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

- I riferimenti dell'assembly corrente.

- Una versione di .NET Framework supportata dal tipo di progetto (solo quando si esegue l'aggiornamento a Visual Studio 2013).

- Una versione di Microsoft Office supportata dal tipo di progetto (solo quando si esegue l'aggiornamento a Visual Studio 2013).

## <a name="assembly-references"></a>Riferimenti ad assembly
 Visual Studio consente di aggiornare i seguenti riferimenti all'assembly nel progetto:

- Assembly di interoperabilità primari di Microsoft Office (PIA)

- Gli assembly in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Per altre informazioni su questi assembly, vedere panoramica Visual Studio Tools per Office [runtime.](../vsto/visual-studio-tools-for-office-runtime-overview.md)

- Versioni nuove o aggiornate degli assembly dipendenti.

## <a name="targeted-net-framework"></a>.NET Framework di destinazione
 Quando si aggiorna un progetto a Visual Studio 2013, Visual Studio modifica il progetto impostando come destinazione [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. La versione di .NET Framework di destinazione del progetto dipende dalla versione di Office installata nel computer. Se è installato [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] , Visual Studio modifica il progetto in base a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. In caso contrario, Visual Studio modifica il progetto in base a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

> [!NOTE]
> Potrebbe essere necessario eseguire alcuni altri passaggi per eseguire una soluzione ridestinata nello sviluppo e nei computer degli utenti finali e il progetto non verrà più compilato se usa alcune funzionalità. Per altre informazioni, vedere [Eseguire la migrazione Office soluzioni a .NET Framework 4 o versioni successive.](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)

 Se la destinazione è [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva in un progetto di Office, è possibile usare alcune funzionalità che non sono disponibili quando la destinazione è .NET Framework 3.5. Per altre informazioni, vedere [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Applicazione Office destinazione
 Quando si aggiorna un progetto di Office a Visual Studio 2013, Visual Studio modifica il progetto impostando come destinazione una versione di Microsoft Office supportata dal tipo di progetto, ad esempio un progetto di personalizzazione a livello di documento o un progetto di componente aggiuntivo VSTO.

 I progetti di Office in Visual Studio 2013 possono essere destinati ad applicazioni [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] . Visual Studio modifica il progetto impostando come destinazione la versione più recente di Office installata. Se nessuna di queste versioni di Office è installata, Visual Studio non aggiorna il progetto.

> [!NOTE]
> Se si aggiorna un progetto di componente aggiuntivo VSTO alla destinazione o a una versione successiva, assicurarsi che il gestore eventi del componente aggiuntivo VSTO non contenga codice che accede a un documento [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] `ThisAddIn_Startup` nell'applicazione. Per altre informazioni, vedere [Accedere a un documento all'avvio Office'applicazione](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Per le personalizzazioni a livello di documento, converte i documenti in un progetto con un formato binario, ad esempio documenti con estensione.xlso.doc, nel formato [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] Office Open XML.   Per altre informazioni su Open XML, vedere [Introduction to new file name extensions (Introduzione alle nuove estensioni di file) e Open XML formats (Formati Open XML).](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1)

> [!NOTE]
> Gli smart tag sono deprecati in Excel 2010 e Word 2010. Pertanto, se la soluzione usa smart tag, è necessario rimuoverli prima di testarla e eseguirne il debug in Visual Studio 2013 o Visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Aggiornare Microsoft Office 2003
 Ci sono alcune altre considerazioni per l'aggiornamento delle personalizzazioni a livello di documento e dei componenti aggiuntivi VSTO destinati a Microsoft Office 2003.

### <a name="document-level-projects"></a>Progetti a livello di documento
 Se il documento nel progetto contiene controlli Windows Form, è inoltre necessario che sia disponibile Visual Studio 2005 Tools per Office Second Edition Runtime installato prima di aggiornare il progetto. Se questa versione di runtime non è installata nel computer di sviluppo prima di aggiornare il progetto, il progetto aggiornato potrebbe contenere errori di compilazione o di runtime. Dopo aver completato l'aggiornamento del progetto, è possibile disinstallare Visual Studio 2005 Tools per Office Second Edition Runtime dal computer di sviluppo se non viene usato da altre soluzioni Office. Questa versione del runtime è disponibile come pacchetto ridistribuibile dall'Area download Microsoft in [Microsoft Visual Studio 2005 Tools per Office Second Edition Runtime (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

### <a name="vsto-add-in-projects"></a>Progetti di componente aggiuntivo VSTO
 Se il file della soluzione per il progetto originale include un progetto di installazione o InstallShield Limited Edition configurato per installare il componente aggiuntivo VSTO, Visual Studio aggiorna il progetto, ma non apporta altre modifiche. Se si intende continuare a usare un file Windows Installer per distribuire il componente aggiuntivo VSTO, è necessario modificare il progetto di installazione o InstallShield Limited Edition per installare nuovi prerequisiti come, ad esempio, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools per Office Runtime e, facoltativamente, gli assembly di interoperabilità primari a cui fa riferimento il componente aggiuntivo VSTO. Per altre informazioni, vedere [Deploy an Office solution by using Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 Se si vuole usare ClickOnce per distribuire il componente aggiuntivo VSTO, è possibile eliminare completamente il progetto di installazione o InstallShield Limited Edition. Per altre informazioni sulla distribuzione VSTO componenti aggiuntivi usando ClickOnce, vedere [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiornare Office soluzioni](/previous-versions/4bez6837(v=vs.140))
- [Eseguire Office soluzioni di migrazione a .NET Framework 4 o versione successiva](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Project Aggiornamento, finestra di dialogo Opzioni](../vsto/project-upgrade-options-dialog-box.md)