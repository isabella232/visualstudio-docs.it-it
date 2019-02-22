---
title: 'Procedura: Esporre il codice a VBA in un C# progetto'
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6da4d0642738fca2f35adbc2ec4e039e3edf11b2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604479"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Procedura: Esporre il codice a VBA in un oggetto visivo C# progetto
  Se si desidera che i due tipi di codice per interagire tra loro, è possibile esporre codice in un progetto Visual c# in Visual Basic Applications Edition (VBA).

 Il processo di Visual c# è diverso dal processo di Visual Basic. Per altre informazioni, vedere [Procedura: Esporre il codice a VBA in un progetto Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Esporre il codice in un progetto Visual c#
 Per consentire al codice VBA chiamare codice in un progetto Visual c#, modificare il codice in modo da essere reso visibile a COM e quindi impostare il **ReferenceAssemblyFromVbaProject** proprietà **True** nella finestra di progettazione.

 Per una procedura dettagliata che illustra come chiamare un metodo in un oggetto visivo C# progetto da VBA, vedere [procedura dettagliata: Chiamare il codice da VBA in un Visual C&#35; project](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Per esporre il codice in un progetto Visual c# da VBA

1. Aprire o creare un progetto a livello di documento che si basa su un documento di Word, cartella di lavoro di Excel o modello di Excel che supporta le macro e che contiene già codice VBA.

    Per altre informazioni sui formati di file di documento che supportano le macro, vedere [combinare VBA e le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   >  Questa funzionalità non può essere usata nei progetti Modello di Word,

2. Assicurarsi che il codice VBA nel documento può essere eseguita senza chiedere conferma all'utente di attivare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.

3. Aggiungere il membro che si desidera esporre a VBA in una classe pubblica nel progetto e il nuovo membro come dichiarare **pubblica**.

4. Applicare la seguente istruzione <xref:System.Runtime.InteropServices.ComVisibleAttribute> e <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attributi alla classe che si sta esponendo a VBA. Questi attributi rendono visibile la classe a COM, ma senza generare un'interfaccia di classe.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Eseguire l'override di **GetAutomationObject** metodo di una classe di elementi host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA:

   - Se si espone una classe di elementi host a VBA, eseguire l'override di **GetAutomationObject** metodo che appartiene a questa classe e restituisce l'istanza corrente della classe.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Se si espone una classe che non è un elemento host su VBA, eseguire l'override di **GetAutomationObject** metodo di tutti gli host di elemento del progetto e restituire un'istanza della classe di elementi non host. Ad esempio, il codice seguente si presuppone che si espone una classe denominata `DocumentUtilities` a VBA.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Per altre informazioni sugli elementi host, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md).

6. Estrarre un'interfaccia dalla classe che si sta esponendo a VBA. Nel **Estrai interfaccia** finestra di dialogo, selezionare i membri pubblici che si desidera includere nella dichiarazione di interfaccia. Per altre informazioni, vedere [refactoring con estrazione interfaccia](../ide/reference/extract-interface.md).

7. Aggiungere il **pubblica** una parola chiave per la dichiarazione dell'interfaccia.

8. Rendere visibili a COM aggiungendo il codice seguente l'interfaccia <xref:System.Runtime.InteropServices.ComVisibleAttribute> all'interfaccia dell'attributo.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Aprire il documento (per Word) o un foglio di lavoro (per Excel) nella finestra di progettazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

10. Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.

    > [!NOTE]
    >  Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, si riceverà un messaggio di errore quando si impostano i **ReferenceAssemblyFromVbaProject** proprietà **True**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.

11. Fare clic su **OK** nel messaggio visualizzato. Questo messaggio per ricordare che se si aggiungono VBA alla cartella di lavoro di codice o del documento quando si esegue il progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], il codice VBA andranno perso la volta successiva che si compila il progetto. Questo avviene perché il documento nella compilazione di output la cartella verrà sovrascritta ogni volta che si compila il progetto.

     A questo punto, Visual Studio consente di configurare il progetto in modo che il progetto VBA può chiamare nell'assembly. Visual Studio aggiunge anche un metodo denominato `GetManagedClass` al progetto VBA. È possibile chiamare questo metodo da qualsiasi posizione nel progetto VBA per accedere alla classe esposta a VBA.

12. Compilare il progetto.

## <a name="see-also"></a>Vedere anche
- [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Combinazione di VBA e le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Procedura dettagliata: Chiamare il codice da VBA in un Visual C&#35; progetto](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Procedura: Esporre il codice a VBA in un progetto Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
