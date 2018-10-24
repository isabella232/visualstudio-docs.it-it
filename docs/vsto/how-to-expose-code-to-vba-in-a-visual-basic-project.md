---
title: 'Procedura: esporre il codice a VBA in un progetto Visual Basic'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e4bc9f4227c11f8e34838a2785b27da62a0a6b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839648"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Procedura: esporre il codice a VBA in un progetto Visual Basic
  È possibile esporre il codice in un [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] progetto di Visual Basic Applications Edition (VBA) se si desidera che i due tipi di codice per interagire tra loro.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Il processo di Visual Basic è diverso dal processo di Visual c#. Per altre informazioni, vedere [procedura: esporre il codice a VBA in un Visual C&#35; progetto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
 Il processo è diverso da quella per il codice in altre classi per il codice in una classe di elementi host:  
  
- [Esporre il codice in una classe di elementi host](#HostItemCode)  
  
- [Esporre il codice che non è in una classe di elementi host](#NonHostItem)  
  
  ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [come eseguire operazioni VSTO di ricerca per categorie: chiamare codice da VBA?](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> Esporre il codice in una classe di elementi host  
 Per consentire al codice VBA di chiamare codice Visual Basic in una classe di elementi host, impostare il **EnableVbaCallers** proprietà dell'elemento host **True**.  
  
 Per una procedura dettagliata che illustra come esporre un metodo di una classe di elementi host e chiamarlo successivamente da VBA, vedere [procedura dettagliata: chiamata di codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Per altre informazioni sugli elementi host, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md).  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Per esporre il codice in un elemento host su VBA  
  
1.  Aprire o creare un livello di documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] progetto basato su un documento di Word, cartella di lavoro di Excel o modello di Excel che supporta le macro e che contiene già codice VBA.  
  
     Per altre informazioni sui formati di file di documento che supportano le macro, vedere [combinare VBA e le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Questa funzionalità non può essere usata nei progetti Modello di Word,  
  
2.  Assicurarsi che il codice VBA nel documento può essere eseguita senza chiedere conferma all'utente di attivare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.  
  
3.  Aggiungere la proprietà, metodo o evento che si vuole esporre a VBA in una delle classi dell'elemento host del progetto e il nuovo membro come dichiarare **pubblica**. Il nome della classe dipende dall'applicazione:  
  
    -   In un progetto Word, la classe dell'elemento host è denominata `ThisDocument` per impostazione predefinita.  
  
    -   In un progetto di Excel, sono denominate classi dell'elemento host `ThisWorkbook`, `Sheet1`, `Sheet2`, e `Sheet3` per impostazione predefinita.  
  
4.  Impostare il **EnableVbaCallers** proprietà per l'elemento host **True**. Questa proprietà è disponibile nel **proprietà** finestra quando l'elemento host è aperto nella finestra di progettazione.  
  
     Dopo aver impostato questa proprietà, Visual Studio imposta automaticamente il **ReferenceAssemblyFromVbaProject** proprietà **True**.  
  
    > [!NOTE]  
    >  Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, si riceverà un messaggio di errore quando si impostano i **EnableVbaCallers** proprietà **True**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.  
  
5.  Fare clic su **OK** nel messaggio visualizzato. Questo messaggio per ricordare che se si aggiunge codice VBA alla cartella di lavoro o al documento mentre si eseguono il progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il codice VBA andranno perso la volta successiva che si compila il progetto. Questo avviene perché il documento nella cartella di output di compilazione viene sovrascritto ogni volta che si compila il progetto.  
  
     A questo punto, Visual Studio consente di configurare il progetto in modo che il progetto VBA può chiamare nell'assembly. Visual Studio aggiunge anche una proprietà denominata `CallVSTOAssembly` per il `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, o `Sheet3` modulo nel progetto VBA. È possibile usare questa proprietà per accedere ai membri pubblici della classe esposta a VBA.  
  
6.  Compilare il progetto.  
  
##  <a name="NonHostItem"></a> Esporre il codice che non è in una classe di elementi host  
 Per consentire al codice VBA chiamare il codice Visual Basic non è in una classe di elementi host, modificare il codice in modo da essere reso visibile a VBA.  
  
### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Per esporre il codice che non è in una classe di elementi host a VBA  
  
1.  Aprire o creare un livello di documento [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] progetto basato su un documento di Word, cartella di lavoro di Excel o modello di Excel che supporta le macro e che contiene già codice VBA.  
  
     Per altre informazioni sui formati di file di documento che supportano le macro, vedere [combinare VBA e le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Questa funzionalità non può essere usata nei progetti Modello di Word,  
  
2.  Assicurarsi che il codice VBA nel documento può essere eseguita senza chiedere conferma all'utente di attivare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.  
  
3.  Aggiungere il membro che si desidera esporre a VBA in una classe pubblica nel progetto e il nuovo membro come dichiarare **pubblica**.  
  
4.  Applicare la seguente istruzione <xref:System.Runtime.InteropServices.ComVisibleAttribute> e <xref:Microsoft.VisualBasic.ComClassAttribute> attributi alla classe che si sta esponendo a VBA. Questi attributi rendono visibili a VBA la classe.  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  Eseguire l'override del metodo **GetAutomationObject** di una classe di elementi host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA. L'esempio di codice seguente presuppone che si espone una classe denominata `DocumentUtilities` a VBA.  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Aprire il documento (per Word) o un foglio di lavoro (per Excel) finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
7.  Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.  
  
    > [!NOTE]  
    >  Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, si riceverà un messaggio di errore quando si impostano i **ReferenceAssemblyFromVbaProject** proprietà **True** . Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.  
  
8.  Fare clic su **OK** nel messaggio visualizzato. Questo messaggio per ricordare che se si aggiunge codice VBA alla cartella di lavoro o al documento mentre si eseguono il progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il codice VBA andranno perso la volta successiva che si compila il progetto. Questo avviene perché il documento nella cartella di output di compilazione viene sovrascritto ogni volta che si compila il progetto.  
  
     A questo punto, Visual Studio consente di configurare il progetto in modo che il progetto VBA può chiamare nell'assembly. Visual Studio aggiunge anche un metodo denominato `GetManagedClass` al progetto VBA. È possibile chiamare questo metodo da qualsiasi posizione nel progetto VBA per accedere alla classe esposta a VBA.  
  
9. Compilare il progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combinazione di VBA e le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Procedura dettagliata: Chiamata di codice da VBA in un progetto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [Procedura: esporre il codice a VBA in un Visual C&#35; progetto](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  