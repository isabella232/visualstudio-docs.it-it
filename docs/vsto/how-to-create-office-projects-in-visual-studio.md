---
title: 'Procedura: creare progetti di Office in Visual Studio'
description: Informazioni su come usare Visual Studio per creare componenti aggiuntivi VSTO e personalizzazioni a livello di documento per applicazioni Microsoft Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1d0bd242f3a57031442cb0b39e62a28c01ad1a6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962392"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Procedura: creare progetti di Office in Visual Studio
  È possibile usare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per creare personalizzazioni a livello di documento e di componente aggiuntivo VSTO per applicazioni Microsoft Office. Per altre informazioni su questi tipi di progetti, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-a-vsto-add-in-project"></a>Per creare un progetto di componente aggiuntivo VSTO

1. Nel menu **File**, scegliere **Nuovo** > **Progetto**. Se il Integrated Development Environment (IDE) è impostato per usare [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] le impostazioni di sviluppo,  scegliere **nuovo**  >  **progetto** dal menu file.

    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

   > [!NOTE]
   > Per impostazione predefinita, i progetti di Office hanno come destinazione [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Per ulteriori informazioni, vedere [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).

2. Nel riquadro modelli, nel nodo relativo alla lingua che si desidera utilizzare, espandere **Office/SharePoint**.

3. Scegliere il nodo **componenti aggiuntivi di Office** .

4. Nell'elenco dei modelli di progetto scegliere un modello di progetto del componente aggiuntivo VSTO. Per un elenco dei modelli di progetto di componente aggiuntivo VSTO disponibili, vedere [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > Se i modelli di progetto non sono visibili quando si seleziona il nodo Componenti aggiuntivi di **Office** , assicurarsi che **.NET Framework 4** o versione successiva sia selezionato nella casella combinata nella parte superiore della finestra di dialogo. I modelli di progetto di Office sono visibili per entrambe le versioni di .NET Framework.

5. Nella casella **nome** Digitare un nome per il progetto. Per impostazione predefinita, il nome del progetto viene usato anche come nome della soluzione.

6. Nella casella **percorso** immettere il percorso in cui si desidera creare il progetto. È possibile usare percorsi assoluti e UNC (Universal Naming Convention). Non usare percorsi HTTP, FTP o di altri protocolli.

    I percorsi hanno i formati seguenti:

   * [*unità*\]\:

   * \\\\*Server* \\ di *Condividi*

     Non usare i caratteri seguenti nel percorso:

   * Asterisco (*)

   * Barra verticale {|}

   * Due punti (:) (consentiti solo dopo la lettera di unità)

   * Virgolette doppie (") (nei percorsi che contengono spazi non sono necessarie le virgolette)

   * Minore di (\<)

   * Maggiore di (>)

   * Punto interrogativo (?)

   * Segno di percentuale (%)

7. Fare clic su **OK** .

   ::: moniker range="vs-2017"

   > [!NOTE]
   > I progetti di componente aggiuntivo vengono sempre salvati al momento della creazione e non possono essere creati come progetti temporanei. Per ulteriori informazioni sui progetti temporanei, vedere [progetti temporanei](../ide/creating-solutions-and-projects.md#create-a-temporary-project).

   ::: moniker-end

### <a name="to-create-a-document-level-customization-project"></a>Per creare un progetto di personalizzazione a livello di documento

1. Nel menu **File**, scegliere **Nuovo** > **Progetto**. Se l'IDE è configurato per usare Visual Basic impostazioni di sviluppo, scegliere  **nuovo**  >  **progetto** dal menu file.

    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. Nel riquadro modelli, nel nodo relativo alla lingua che si desidera utilizzare, espandere **Office/SharePoint**.

3. Selezionare il nodo **Componenti aggiuntivi di Office** .

4. Nell'elenco dei modelli di progetto scegliere un modello di progetto a livello di documento. Per un elenco dei modelli di progetto a livello di documento disponibili, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > Se i modelli di progetto non sono visibili quando si seleziona il nodo Componenti aggiuntivi di **Office** , assicurarsi che sia selezionato **.NET Framework 4** o versione successiva.

5. Nella casella **nome** Digitare un nome per il progetto. Per impostazione predefinita, questo nome viene usato anche per il documento. Se l'IDE è configurato per usare le impostazioni di sviluppo di Visual C# o le impostazioni di sviluppo generali, immettere anche un percorso e il nome della soluzione.

   > [!NOTE]
   > Non è possibile usare caratteri surrogati nel percorso o nel nome del progetto. Inoltre, se si prevede di distribuire la soluzione per l'uso offline, i caratteri nel nome del progetto devono rispettare le specifiche del protocollo HTTP.

6. Fare clic su **OK** .

    Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office** .

7. Selezionare **Crea un nuovo documento** se si desidera creare un nuovo documento per la soluzione oppure selezionare **copia un documento esistente** se si desidera personalizzare un documento esistente.

    Se si crea un nuovo documento, specificare il nome nella casella **nome** e selezionare il formato del documento usando la casella **formato** . Per ulteriori informazioni sui formati disponibili, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

    Se si utilizza un documento esistente, specificare il percorso del documento nel **percorso completo della casella del documento esistente** . È possibile usare percorsi assoluti e UNC. Non usare percorsi HTTP, FTP o di altri protocolli per il documento.

    I percorsi hanno i formati seguenti:

   - [*unità*\]\:

   - \\\\*Server* \\ di *Condividi*

     Non usare i caratteri seguenti nel percorso:

   - Asterisco (*)

   - Barra verticale {|}

   - Due punti (:) (consentiti solo dopo la lettera di unità)

   - Virgolette doppie (") (nei percorsi che contengono spazi non sono necessarie le virgolette)

   - Minore di (\<)

   - Maggiore di (>)

   - Punto interrogativo (?)

   - Segno di percentuale (%)

   > [!NOTE]
   > Se si usa un documento esistente in un progetto di [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)], usare solo i documenti creati o convertiti in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Analogamente, se si usa un documento esistente in un progetto di Word 2010, usare solo i documenti creati o convertiti in Word 2010. Alcune funzionalità verranno disabilitate nel documento se si usa un documento creato in una versione precedente di Word. Se si prova a scrivere codice che usa queste funzionalità, potrebbero verificarsi errori nel progetto. Per convertire un documento, aprirlo in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o Word 2010, nella scheda **file** della barra multifunzione, scegliere **info**  >  **Convert**.

8. Scegliere **Fine**.

9. Aggiungere la cartella del progetto e le relative sottocartelle all'elenco di percorsi attendibili nel Centro protezione di Word nei casi seguenti:

   - Si sta creando un documento di Word basato su un file con *estensione docm* e il documento contiene un progetto VBA o ospita Windows Form controlli. Aggiungendo la cartella del progetto all'elenco di percorsi attendibili sarà possibile assicurarsi che il documento funzioni come previsto in fase di progettazione.

   - Si sta creando un progetto di modello di Word basato su un file con *estensione dotx* . È necessario aggiungere la cartella del progetto all'elenco di percorsi attendibili in modo che sia possibile eseguire il progetto e il relativo debug.

     Per ulteriori informazioni su come aggiungere un documento ai percorsi attendibili, vedere il sito Web di Microsoft Office Online [creare, rimuovere o modificare un percorso attendibile per i file](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="see-also"></a>Vedi anche
- [Panoramica sui modelli di progetto di Office](../vsto/office-project-templates-overview.md)
- [Sviluppo collaborativo di soluzioni Office](../vsto/collaborative-development-of-office-solutions.md)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
