---
title: Eseguire l'aggiornamento e la migrazione di soluzioni Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b86699f11ab59aaf0ef09f5c7ae52d69e41e96c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671742"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Eseguire l'aggiornamento e la migrazione di soluzioni Office
  Se si dispone di un progetto di Microsoft Office che è stato creato in una versione precedente di Visual Studio, è necessario aggiornare il progetto per usarlo nella versione corrente di Visual Studio. Per aggiornare un progetto di Microsoft Office, aprirlo in una versione di Visual Studio che include Microsoft Office Developer Tools. Per altre informazioni sulle versioni di Visual Studio che includono Microsoft Office developer tools, vedere [configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
> [!NOTE]  
>  Se ti interessa sviluppare soluzioni che estendono l'esperienza di Office attraverso [piattaforme multiple](https://dev.office.com/add-in-availability)? Consultare la nuova [modello di componenti aggiuntivi di Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Componenti aggiuntivi di Office con footprint ridotto rispetto alle soluzioni e componenti aggiuntivi VSTO e si possono essere compilate usando praticamente qualsiasi tecnologia, ad esempio HTML5, JavaScript, CSS3 e XML di programmazione web.  
  
> [!NOTE]  
>  Visual Studio non può aggiornare i progetti modello di form InfoPath creati usando versioni precedenti di Visual Studio. Questi tipi di progetti non sono supportati nella versione corrente di Visual Studio.  
  
## <a name="changes-to-upgraded-projects"></a>Modifiche apportate ai progetti aggiornati  
 Quando si aggiorna un progetto di Microsoft Office, Visual Studio modifica il progetto in base ai seguenti elementi:  
  
-   Visual Studio 2010 Tools per Office runtime. Per altre informazioni, vedere [Visual Studio Tools per Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   I riferimenti dell'assembly corrente.  
  
-   Una versione di .NET Framework supportata dal tipo di progetto (solo quando si esegue l'aggiornamento a Visual Studio 2013).  
  
-   Una versione di Microsoft Office supportata dal tipo di progetto (solo quando si esegue l'aggiornamento a Visual Studio 2013).  
  
## <a name="assembly-references"></a>Riferimenti ad assembly  
 Visual Studio consente di aggiornare i seguenti riferimenti all'assembly nel progetto:  
  
-   Assembly di interoperabilità primari di Microsoft Office (PIA)  
  
-   Gli assembly in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Per altre informazioni su questi assembly, vedere [Visual Studio Tools per Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
-   Versioni nuove o aggiornate degli assembly dipendenti.  
  
## <a name="targeted-net-framework"></a>.NET Framework di destinazione  
 Quando si aggiorna un progetto a Visual Studio 2013, Visual Studio modifica il progetto impostando come destinazione [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. La versione di .NET Framework di destinazione del progetto dipende dalla versione di Office installata nel computer. Se è installato [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] , Visual Studio modifica il progetto in base a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. In caso contrario, Visual Studio modifica il progetto in base a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
> [!NOTE]  
>  Potrebbe essere necessario eseguire alcuni altri passaggi per eseguire una soluzione ridestinata nello sviluppo e nei computer degli utenti finali e il progetto non verrà più compilato se usa alcune funzionalità. Per altre informazioni, vedere [soluzioni di Office di eseguire la migrazione a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Se la destinazione è [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva in un progetto di Office, è possibile usare alcune funzionalità che non sono disponibili quando la destinazione è .NET Framework 3.5. Per altre informazioni, vedere [progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="targeted-office-application"></a>Applicazione di Office di destinazione  
 Quando si aggiorna un progetto di Office a Visual Studio 2013, Visual Studio modifica il progetto impostando come destinazione una versione di Microsoft Office supportata dal tipo di progetto, ad esempio un progetto di personalizzazione a livello di documento o un progetto di componente aggiuntivo VSTO.  
  
 I progetti di Office in Visual Studio 2013 possono essere destinati ad applicazioni [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] . Visual Studio modifica il progetto impostando come destinazione la versione più recente di Office installata. Se nessuna di queste versioni di Office è installata, Visual Studio non aggiorna il progetto.  
  
> [!NOTE]  
>  Se si aggiorna un progetto di componente aggiuntivo VSTO di destinazione [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o versione successiva, assicurarsi che il `ThisAddIn_Startup` gestore eventi del componente aggiuntivo VSTO non contenga codice che accede a un documento nell'applicazione. Per altre informazioni, vedere [accedere a un documento all'avvio dell'applicazione di Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Per le personalizzazioni a livello di documento, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] converte i documenti in un progetto con un formato binario, ad esempio i documenti privi di un' *xls* oppure *doc* estensione, nel formato Office Open XML. Per altre informazioni sul formato Open XML, vedere [formati Open XML e introduzione di nuove estensioni di file](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).  
  
> [!NOTE]  
>  Gli smart tag sono deprecati in Excel 2010 e Word 2010. Pertanto, se la soluzione usa smart tag, è necessario rimuoverli prima di testarla e eseguirne il debug in Visual Studio 2013 o Visual Studio 2015.  
  
## <a name="upgrade-microsoft-office-2003-projects"></a>Aggiornare i progetti di Microsoft Office 2003  
 Ci sono alcune altre considerazioni per l'aggiornamento delle personalizzazioni a livello di documento e dei componenti aggiuntivi VSTO destinati a Microsoft Office 2003.  
  
### <a name="document-level-projects"></a>Progetti a livello di documento  
 Se il documento nel progetto contiene controlli Windows Form, è inoltre necessario che sia disponibile Visual Studio 2005 Tools per Office Second Edition Runtime installato prima di aggiornare il progetto. Se questa versione di runtime non è installata nel computer di sviluppo prima di aggiornare il progetto, il progetto aggiornato potrebbe contenere errori di compilazione o di runtime. Dopo aver completato l'aggiornamento del progetto, è possibile disinstallare Visual Studio 2005 Tools per Office Second Edition Runtime dal computer di sviluppo se non viene usato da altre soluzioni Office. Questa versione del runtime è disponibile come pacchetto ridistribuibile dall'Area download Microsoft in [Microsoft Visual Studio 2005 Tools per Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
### <a name="vsto-add-in-projects"></a>Progetti di componente aggiuntivo VSTO  
 Se il file della soluzione per il progetto originale include un progetto di installazione o InstallShield Limited Edition configurato per installare il componente aggiuntivo VSTO, Visual Studio aggiorna il progetto, ma non apporta altre modifiche. Se si intende continuare a usare un file Windows Installer per distribuire il componente aggiuntivo VSTO, è necessario modificare il progetto di installazione o InstallShield Limited Edition per installare nuovi prerequisiti come, ad esempio, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools per Office Runtime e, facoltativamente, gli assembly di interoperabilità primari a cui fa riferimento il componente aggiuntivo VSTO. Per altre informazioni, vedere [distribuire una soluzione Office tramite Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
 Se si vuole usare ClickOnce per distribuire il componente aggiuntivo VSTO, è possibile eliminare completamente il progetto di installazione o InstallShield Limited Edition. Per altre informazioni sulla distribuzione di componenti aggiuntivi VSTO usando ClickOnce, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiornamento di Office solutions](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)   
 [Eseguire la migrazione di soluzioni Office a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Esegue l'aggiornamento, finestra di dialogo Opzioni progetto](../vsto/project-upgrade-options-dialog-box.md)  
  
  