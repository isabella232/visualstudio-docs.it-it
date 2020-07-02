---
title: 'Procedura: esporre il codice a VBA in un progetto C#'
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 21d7672d3c08012e75d73ee8bf4d9816b850eb2c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544833"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Procedura: esporre il codice a VBA in un progetto Visual C#
  È possibile esporre il codice in un progetto Visual C# per Visual Basic, Applications Edition codice (VBA) se si desidera che i due tipi di codice interagiranno tra loro.

 Il processo di Visual C# è diverso da quello del Visual Basic processo. Per altre informazioni, vedere [procedura: esporre il codice a VBA in un progetto Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Esporre il codice in un progetto Visual C#
 Per consentire al codice VBA di chiamare il codice in un progetto Visual C#, modificare il codice in modo che sia visibile a COM, quindi impostare la proprietà **ReferenceAssemblyFromVbaProject** su **true** nella finestra di progettazione.

 Per una procedura dettagliata in cui viene illustrato come chiamare un metodo in un progetto Visual C# da VBA, vedere [procedura dettagliata: chiamata di codice da VBA in un progetto Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Per esporre il codice in un progetto Visual C# a VBA

1. Aprire o creare un progetto a livello di documento basato su un documento di Word, una cartella di lavoro di Excel o un modello di Excel che supporta le macro e che già contiene codice VBA.

    Per ulteriori informazioni sui formati di file di documento che supportano le macro, vedere [combinare VBA e personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   > Questa funzionalità non può essere usata nei progetti Modello di Word,

2. Verificare che il codice VBA nel documento possa essere eseguito senza richiedere all'utente di abilitare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.

3. Aggiungere il membro che si desidera esporre a VBA a una classe pubblica nel progetto e dichiarare il nuovo membro come **public**.

4. Applicare gli <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributi e seguenti <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> alla classe che si sta esponendo a VBA. Questi attributi rendono visibile la classe a COM, ma senza generare un'interfaccia di classe.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Eseguire l'override del metodo **GetAutomationObject** di una classe di elementi host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA:

   - Se si espone una classe dell'elemento host a VBA, eseguire l'override del metodo **GetAutomationObject** che appartiene a questa classe e restituire l'istanza corrente della classe.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Se si espone una classe che non è un elemento host a VBA, eseguire l'override del metodo **GetAutomationObject** di qualsiasi elemento host nel progetto e restituire un'istanza della classe di elementi non host. Il codice seguente, ad esempio, presuppone che si stia esponendo una classe denominata `DocumentUtilities` a VBA.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Per ulteriori informazioni sugli elementi host, vedere [Cenni preliminari sugli elementi host e sui controlli host](../vsto/host-items-and-host-controls-overview.md).

6. Estrarre un'interfaccia dalla classe che si sta esponendo a VBA. Nella finestra di dialogo **Estrai interfaccia** selezionare i membri pubblici che si desidera includere nella dichiarazione di interfaccia. Per altre informazioni, vedere [estrarre il refactoring dell'interfaccia](../ide/reference/extract-interface.md).

7. Aggiungere la parola chiave **public** alla dichiarazione dell'interfaccia.

8. Rendere visibile l'interfaccia a COM aggiungendo l'attributo seguente <xref:System.Runtime.InteropServices.ComVisibleAttribute> all'interfaccia.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Aprire il documento (per Word) o il foglio di lavoro (per Excel) nella finestra di progettazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.

    > [!NOTE]
    > Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, verrà visualizzato un messaggio di errore quando si imposta la proprietà **ReferenceAssemblyFromVbaProject** su **true**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.

11. Fare clic su **OK** nel messaggio visualizzato. Questo messaggio ricorda che se si aggiunge codice VBA alla cartella di lavoro o al documento durante l'esecuzione del progetto da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , il codice VBA verrà perso la volta successiva che si compila il progetto. Questo perché il documento nella cartella dell'output di compilazione viene sovrascritto ogni volta che si compila il progetto.

     A questo punto, Visual Studio configura il progetto in modo che il progetto VBA possa chiamare nell'assembly. Visual Studio aggiunge anche un metodo denominato `GetManagedClass` al progetto VBA. È possibile chiamare questo metodo da qualsiasi punto del progetto VBA per accedere alla classe esposta a VBA.

12. Compilare il progetto.

## <a name="see-also"></a>Vedere anche
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Combinare VBA e personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Procedura dettagliata: chiamata di codice da VBA in un progetto Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Procedura: esporre il codice a VBA in un progetto Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
