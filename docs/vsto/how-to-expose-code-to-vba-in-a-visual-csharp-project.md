---
title: 'Procedura: Esporre codice a VBA in un progetto C#'
description: Informazioni su come esporre il codice in un progetto Visual C# Visual Basic, Applications Edition (VBA) se si vuole che i due tipi di codice interagiscano tra loro.
ms.custom: seodec18, SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 214330d50059a4f1021e5c3e9983613e8b488c76
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100075"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Procedura: Esporre codice a VBA in un progetto Visual C#
  È possibile esporre il codice in un progetto Visual C# Visual Basic, Applications Edition (VBA) se si vuole che i due tipi di codice interagiscano tra loro.

 Il processo di Visual C# è diverso da quello Visual Basic processo. Per altre informazioni, vedere [Procedura: Esporre il](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)codice a VBA in un Visual Basic progetto .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Esporre il codice in un progetto Visual C#
 Per consentire al codice VBA di chiamare codice in un progetto Visual C#, modificare il codice in modo che sia visibile a COM e quindi impostare la proprietà **ReferenceAssemblyFromVbaProject** su **True** nella finestra di progettazione.

 Per una procedura dettagliata che illustra come chiamare un metodo in un progetto Visual C# da VBA, vedere [Procedura dettagliata:](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)Chiamare codice da VBA in un progetto Visual C&#35; .

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Per esporre il codice in un progetto Visual C# a VBA

1. Aprire o creare un progetto a livello di documento basato su un documento di Word, una cartella di lavoro Excel o un modello Excel che supporta le macro e che contiene già codice VBA.

    Per altre informazioni sui formati di file di documento che supportano le macro, vedere [Combinare VBA e personalizzazioni a livello di documento.](../vsto/combining-vba-and-document-level-customizations.md)

   > [!NOTE]
   > Questa funzionalità non può essere usata nei progetti Modello di Word,

2. Assicurarsi che al codice VBA nel documento sia consentita l'esecuzione senza chiedere all'utente di abilitare le macro. È possibile considerare attendibile l'esecuzione del codice VBA aggiungendo il percorso del progetto di Office all'elenco di percorsi attendibili nelle impostazioni del Centro protezione per Word o Excel.

3. Aggiungere il membro che si vuole esporre a VBA a una classe pubblica nel progetto e dichiarare il nuovo membro come **public**.

4. Applicare gli <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributi e seguenti alla classe che si sta <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> esponendo a VBA. Questi attributi rendono visibile la classe a COM, ma senza generare un'interfaccia di classe.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Eseguire l'override del metodo **GetAutomationObject** di una classe di elemento host nel progetto per restituire un'istanza della classe che si sta esponendo a VBA:

   - Se si espone una classe di elemento host a VBA, eseguire l'override del **metodo GetAutomationObject** che appartiene a questa classe e restituire l'istanza corrente della classe.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Se si espone una classe che non è un elemento host a VBA, eseguire l'override del metodo **GetAutomationObject** di qualsiasi elemento host nel progetto e restituire un'istanza della classe dell'elemento non host. Ad esempio, il codice seguente presuppone che si esponga una classe denominata `DocumentUtilities` a VBA.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Per altre informazioni sugli elementi host, vedere [Panoramica di elementi host e controlli host](../vsto/host-items-and-host-controls-overview.md).

6. Estrarre un'interfaccia dalla classe che si sta esponendo a VBA. Nella finestra **di dialogo** Estrai interfaccia selezionare i membri pubblici da includere nella dichiarazione dell'interfaccia. Per altre informazioni, vedere [Estrarre il refactoring dell'interfaccia](../ide/reference/extract-interface.md).

7. Aggiungere la **parola chiave public** alla dichiarazione dell'interfaccia.

8. Rendere visibile l'interfaccia a COM aggiungendo <xref:System.Runtime.InteropServices.ComVisibleAttribute> l'attributo seguente all'interfaccia .

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Aprire il documento (per Word) o il foglio di lavoro (Excel) nella finestra di progettazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. Nella finestra **Proprietà** selezionare la proprietà **ReferenceAssemblyFromVbaProject** e modificarne il valore impostandola su **True**.

    > [!NOTE]
    > Se la cartella di lavoro o il documento non contiene già codice VBA o se il codice VBA nel documento non è attendibile per l'esecuzione, verrà visualizzato un messaggio di errore quando si imposta la proprietà **ReferenceAssemblyFromVbaProject** su **True**. Ciò avviene perché in questa situazione, in Visual Studio non è possibile modificare il progetto VBA nel documento.

11. Fare clic su **OK** nel messaggio visualizzato. Questo messaggio ricorda che se si aggiunge codice VBA alla cartella di lavoro o al documento quando si esegue il progetto da , il codice VBA andrà perso alla successiva compilazione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] del progetto. Questo perché il documento nella cartella dell'output di compilazione viene sovrascritto ogni volta che si compila il progetto.

     A questo punto, Visual Studio il progetto in modo che il progetto VBA possa chiamare nell'assembly. Visual Studio aggiunge anche un metodo `GetManagedClass` denominato al progetto VBA. È possibile chiamare questo metodo da qualsiasi punto del progetto VBA per accedere alla classe esposta a VBA.

12. Compilare il progetto.

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Combinare le personalizzazioni VBA e a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)
- [Procedura dettagliata: Chiamare codice da VBA in un progetto Visual C&#35; codice](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Procedura: Esporre codice a VBA in un progetto Visual Basic codice](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
