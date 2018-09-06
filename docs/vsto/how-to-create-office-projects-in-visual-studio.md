---
title: 'Procedura: creare progetti di Office in Visual Studio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f39e1a5c5271e806a8e90499e50cb9bd4705a5d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673327"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Procedura: creare progetti di Office in Visual Studio
  È possibile usare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per creare il componente aggiuntivo VSTO e a livello di documento personalizzazioni per le applicazioni Microsoft Office. Per altre informazioni su questi tipi di progetti, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-vsto-add-in-project"></a>Per creare un progetto di componente aggiuntivo VSTO  
  
1.  Nel menu **File** scegliere **Nuovo** > **Progetto**. Se l'ambiente di sviluppo integrato (IDE) è impostato per usare [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] delle impostazioni di sviluppo via il **File** menu, scegliere **New** > **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
    > [!NOTE]  
    >  Per impostazione predefinita, i progetti di Office hanno come destinazione [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per altre informazioni, vedere [profilo client .NET Framework](/dotnet/framework/deployment/client-profile).  
  
2.  Nel riquadro Modelli, sotto il nodo per la lingua da usare, espandere **Office/SharePoint**.  
  
3.  Scegliere il **componenti aggiuntivi di Office** nodo.  
  
4.  Nell'elenco dei modelli di progetto scegliere un modello di progetto del componente aggiuntivo VSTO. Per un elenco dei modelli progetto disponibili del componente aggiuntivo VSTO, vedere [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Se i modelli di progetto non sono visibili quando si seleziona il **Office Add-ins** nodo, verificare che l'opzione **.NET Framework 4** o in un secondo momento è selezionato nella casella combinata nella parte superiore della finestra di dialogo. I modelli di progetto di Office sono visibili per entrambe le versioni di .NET Framework.  
  
5.  Nel **nome** , digitare un nome per il progetto. Per impostazione predefinita, il nome del progetto viene usato anche come nome della soluzione.  
  
6.  Nel **posizione** immettere il percorso in cui si desidera creare il progetto. È possibile usare percorsi assoluti e UNC (Universal Naming Convention). Non usare percorsi HTTP, FTP o di altri protocolli.  
  
     I percorsi hanno i formati seguenti:  
  
      * [*unità*\]\:  
  
      * \\\\*Server*\\*condivisione*  
  
     Non usare i caratteri seguenti nel percorso:  
  
      * Asterisco (*)  
  
      * Barra verticale (|)  
  
      * Due punti (:) (consentiti solo dopo la lettera di unità)  
  
      * Virgolette doppie (") (nei percorsi che contengono spazi non sono necessarie le virgolette)  
  
      * Minore di (\<)  
  
      * Maggiore di (>)  
  
      * Punto interrogativo (?)  
  
      * Segno di percentuale (%)  
  
7. Fare clic sul pulsante **OK** .
  
    > [!NOTE]  
    >  I progetti di componente aggiuntivo vengono sempre salvati al momento della creazione e non possono essere creati come progetti temporanei. Per altre informazioni sui progetti temporanei, vedere [progetti temporanei](http://msdn.microsoft.com/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### <a name="to-create-a-document-level-customization-project"></a>Per creare un progetto di personalizzazione a livello di documento  
  
1.  Nel menu **File** scegliere **Nuovo** > **Progetto**. Se l'IDE è configurato per utilizzare le impostazioni di sviluppo Visual Basic il **File** menu, scegliere **New** > **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
    > [!NOTE]  
    >  Per impostazione predefinita, i progetti di Office hanno come destinazione [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Per altre informazioni, vedere [profilo client .NET Framework](/dotnet/framework/deployment/client-profile).  
  
2.  Nel riquadro Modelli, sotto il nodo per la lingua da usare, espandere **Office/SharePoint**.  
  
3.  Selezionare il nodo **Componenti aggiuntivi di Office** .  
  
4.  Nell'elenco dei modelli di progetto scegliere un modello di progetto a livello di documento. Per un elenco di modelli di progetto a livello di documento disponibili, vedere [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Se i modelli di progetto non sono visibili quando si seleziona il **Office Add-ins** nodo, verificare che l'opzione **.NET Framework 4** o in un secondo momento è selezionato nella casella combinata nella parte superiore della finestra di dialogo. I modelli di progetto di Office sono visibili per entrambe le versioni di .NET Framework.  
  
5.  Nel **nome** , digitare un nome per il progetto. Per impostazione predefinita, questo nome viene usato anche per il documento. Se l'IDE è configurato per usare le impostazioni di sviluppo di Visual C# o le impostazioni di sviluppo generali, immettere anche un percorso e il nome della soluzione.  
  
    > [!NOTE]  
    >  Non è possibile usare caratteri surrogati nel percorso o nel nome del progetto. Inoltre, se si prevede di distribuire la soluzione per l'uso offline, i caratteri nel nome del progetto devono rispettare le specifiche del protocollo HTTP.  
  
6.  Fare clic sul pulsante **OK** .  
  
     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .  
  
7.  Selezionare **creare un nuovo documento** se si desidera creare un nuovo documento per la soluzione o selezionarne **copia un documento esistente** se si vuole personalizzare un documento esistente.  
  
     Se si crea un nuovo documento, specificare il nome nel **nome** e selezionare il formato del documento utilizzando il **formato** casella. Per altre informazioni sui formati disponibili, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
     Se si usa un documento esistente, specificare il percorso del documento nella **percorso completo del documento esistente** casella. È possibile usare percorsi assoluti e UNC. Non usare percorsi HTTP, FTP o di altri protocolli per il documento.  
  
     I percorsi hanno i formati seguenti:  
  
    -   [*unità*\]\:  
  
    -   \\\\*Server*\\*condivisione*  
  
     Non usare i caratteri seguenti nel percorso:  
  
    -   Asterisco (*)  
  
    -   Barra verticale (|)  
  
    -   Due punti (:) (consentiti solo dopo la lettera di unità)  
  
    -   Virgolette doppie (") (nei percorsi che contengono spazi non sono necessarie le virgolette)  
  
    -   Minore di (\<)  
  
    -   Maggiore di (>)  
  
    -   Punto interrogativo (?)  
  
    -   Segno di percentuale (%)  
  
    > [!NOTE]  
    >  Se si usa un documento esistente in un progetto di [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)], usare solo i documenti creati o convertiti in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Analogamente, se si usa un documento esistente in un progetto di Word 2010, usare solo i documenti creati o convertiti in Word 2010. Alcune funzionalità verranno disabilitate nel documento se si usa un documento creato in una versione precedente di Word. Se si prova a scrivere codice che usa queste funzionalità, potrebbero verificarsi errori nel progetto. Per convertire un documento, aprirlo in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o Word 2010 e nel **File** sulla barra multifunzione, scegliere **Info** > **convertire**.  
  
8.  Scegliere **Fine**.  
  
9. Aggiungere la cartella del progetto e le relative sottocartelle all'elenco di percorsi attendibili nel Centro protezione di Word nei casi seguenti:  
  
    -   Si sta creando un documento di Word basato su un *docm* file e il documento contiene un progetto VBA oppure ospita controlli Windows Form. Aggiungendo la cartella del progetto all'elenco di percorsi attendibili sarà possibile assicurarsi che il documento funzioni come previsto in fase di progettazione.  
  
    -   Si sta creando un progetto di modello di Word basato su un *dotx* file. È necessario aggiungere la cartella del progetto all'elenco di percorsi attendibili in modo che sia possibile eseguire il progetto e il relativo debug.  
  
     Per altre informazioni su come aggiungere un documento ai percorsi attendibili, vedere il sito web Microsoft Office Online [creazione, rimozione o modifica di un percorso attendibile per i file](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="see-also"></a>Vedere anche  
 [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md)   
 [Sviluppo collaborativo di soluzioni Office](../vsto/collaborative-development-of-office-solutions.md)   
 [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Introduzione a programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  
