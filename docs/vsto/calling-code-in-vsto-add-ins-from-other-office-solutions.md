---
title: Chiamare il codice VSTO componenti aggiuntivi da altre Office soluzioni
description: Informazioni su come esporre un oggetto nel VSTO componente aggiuntivo ad altre soluzioni, incluse altre Microsoft Office personalizzate.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 857cff3d396cfa08d45d7c15bc9b045f7fe23f0c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635443"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Chiamare il codice VSTO componenti aggiuntivi da altre Office soluzioni
  È possibile esporre un oggetto del componente aggiuntivo VSTO in altre soluzioni, ad esempio in altre soluzioni Microsoft Office. Questa funzionalità è utile se il componente aggiuntivo VSTO fornisce un servizio che si vuole usare anche in altre soluzioni. Ad esempio, se si dispone di un componente aggiuntivo VSTO per Microsoft Office Excel che esegue calcoli sui dati finanziari da un servizio Web, altre soluzioni possono eseguire questi calcoli chiamando il componente aggiuntivo Excel VSTO in fase di esecuzione.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Questo processo prevede due passaggi principali:

- Nel componente aggiuntivo VSTO esporre un oggetto ad altre soluzioni.

- In un'altra soluzione accedere all'oggetto esposto dal componente aggiuntivo VSTO e chiamare i membri dell'oggetto.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Tipi di soluzioni che possono chiamare codice in un componente aggiuntivo
 È possibile esporre un oggetto in VSTO componente aggiuntivo ai tipi di soluzioni seguenti:

- Codice Visual Basic, Applications Edition (VBA) di un documento caricato nello stesso processo dell'applicazione del componente aggiuntivo VSTO.

- Personalizzazioni a livello di documento caricate nello stesso processo dell'applicazione del componente aggiuntivo VSTO.

- Altri componenti aggiuntivi VSTO creati usando i modelli di progetto di Office in Visual Studio.

- Componenti aggiuntivi VSTO COM, ovvero componenti aggiuntivi VSTO che implementano direttamente l'interfaccia <xref:Extensibility.IDTExtensibility2> .

- Qualsiasi soluzione in esecuzione in un processo diverso dal componente aggiuntivo VSTO. Questi tipi di soluzioni sono detti anche *client out-of-process*. Sono incluse le applicazioni che automatizzano un'applicazione di Office, ad esempio Windows Form o un'applicazione console, e i componenti aggiuntivi VSTO caricati in un processo diverso.

## <a name="expose-objects-to-other-solutions"></a>Esporre oggetti ad altre soluzioni
 Per esporre un oggetto del componente aggiuntivo VSTO ad altre soluzioni, eseguire la procedura seguente nel componente aggiuntivo:

1. Definire una classe da esporre ad altre soluzioni.

2. Eseguire l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> nella classe `ThisAddIn` . Restituire un'istanza della classe da esporre ad altre soluzioni.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Definire la classe che si vuole esporre ad altre soluzioni
 Questa classe deve essere almeno pubblica, deve avere l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su **true** e deve esporre l'interfaccia [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) .

 Il metodo consigliato per esporre l'interfaccia [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) consiste nell'eseguire la procedura seguente:

1. Definire un'interfaccia che dichiari i membri da esporre ad altre soluzioni. È possibile definire questa interfaccia nel progetto di componente aggiuntivo VSTO. È tuttavia consigliabile definire l'interfaccia in un progetto di libreria di classi separato, se si vuole esporre la classe a soluzioni non VBA. In questo modo, le soluzioni che chiamano il componente aggiuntivo VSTO possono fare riferimento all'interfaccia senza fare riferimento al progetto di componente aggiuntivo VSTO.

2. Applicare l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> a questa interfaccia e impostarlo su **true**.

3. Modificare la classe per implementare l'interfaccia.

4. Applicare <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> l'attributo alla classe e impostare questo attributo sul **valore None** dell'enumerazione <xref:System.Runtime.InteropServices.ClassInterfaceType> .

5. Se si vuole esporre questa classe ai client out-of-process, potrebbe anche essere necessario eseguire le operazioni seguenti:

   - Derivare la classe da <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Per altre informazioni, vedere [Esporre classi a client out-of-process.](#outofproc)

   - Impostare la proprietà **Registra per interoperabilità COM** nel progetto in cui si definisce l'interfaccia. Questa proprietà è necessaria solo se si vuole consentire ai client di usare l'associazione anticipata per chiamare il VSTO componente aggiuntivo.

   L'esempio di codice seguente illustra una classe `AddInUtilities` con un metodo `ImportData` che è possibile chiamare da altre soluzioni. Per visualizzare questo codice nel contesto di una procedura dettagliata più ampia, vedere Procedura dettagliata: Chiamare codice in un componente [VSTO componente aggiuntivo da VBA.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

### <a name="expose-classes-to-vba"></a>Esporre classi a VBA
 Quando si esegue la procedura riportata sopra, il codice VBA può chiamare solo i metodi dichiarati nell'interfaccia. Il codice VBA non può chiamare altri metodi della classe, inclusi i metodi che la classe ottiene dalle classi base, ad esempio <xref:System.Object>.

 In alternativa, è possibile esporre [l'interfaccia IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) impostando l'attributo sul valore AutoDispatch o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> AutoDual <xref:System.Runtime.InteropServices.ClassInterfaceType> dell'enumerazione . Se si espone l'interfaccia , non è necessario dichiarare i metodi in un'interfaccia separata. Il codice VBA può tuttavia chiamare qualsiasi metodo pubblico e non statico della classe, inclusi i metodi ottenuti dalle classi base, ad esempio <xref:System.Object>. Inoltre, i client out-of-process che usano l'associazione anticipata non possono chiamare la classe.

### <a name="expose-classes-to-out-of-process-clients"></a><a name="outofproc"></a> Esporre le classi ai client out-of-process
 Per esporre una classe del componente aggiuntivo VSTO a client out-of-process, è necessario derivare la classe da <xref:System.Runtime.InteropServices.StandardOleMarshalObject> per assicurarsi che i client out-of-process possano chiamare l'oggetto componente aggiuntivo VSTO esposto. In caso contrario, i tentativi di ottenere un'istanza dell'oggetto esposto in un client out-of-process potrebbero non riuscire in modo imprevisto.

 Questo errore è dovuto al fatto che tutte le chiamate nel modello a oggetti di un'applicazione Office devono essere effettuate nel thread principale dell'interfaccia utente, ma le chiamate da un client out-of-process all'oggetto arriveranno su un thread RPC (remote procedure call) arbitrario. Il meccanismo di marshalling COM in .NET Framework non cambia thread e tenta invece di effettuare il marshalling della chiamata all'oggetto nel thread RPC in ingresso anziché nel thread principale dell'interfaccia utente. Se l'oggetto è un'istanza di una classe che deriva da <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, viene effettuato automaticamente il marshalling delle chiamate in ingresso all'oggetto in relazione al thread in cui è stato creato l'oggetto esposto, che sarà il thread principale dell'interfaccia utente dell'applicazione host.

 Per altre informazioni sull'uso dei thread nelle Office, vedere [Supporto del threading in Office](../vsto/threading-support-in-office.md).

### <a name="override-the-requestcomaddinautomationservice-method"></a>Eseguire l'override del metodo RequestComAddInAutomationService
 L'esempio di codice seguente illustra come eseguire l'override del metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> nella classe `ThisAddIn` del componente aggiuntivo VSTO. Nell'esempio si presuppone che sia stata definita una classe `AddInUtilities` denominata che si vuole esporre ad altre soluzioni. Per visualizzare questo codice nel contesto di una procedura dettagliata più ampia, vedere Procedura dettagliata: Chiamare codice in un componente [VSTO componente aggiuntivo da VBA.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

 Quando il componente aggiuntivo VSTO viene caricato, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama il metodo <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Il runtime assegna l'oggetto restituito alla proprietà COMAddIn.Object di un oggetto che rappresenta VSTO <xref:Microsoft.Office.Core.COMAddIn> componente aggiuntivo. Questo oggetto <xref:Microsoft.Office.Core.COMAddIn> è disponibile per altre soluzioni Office e per soluzioni che automatizzano Office.

## <a name="access-objects-from-other-solutions"></a>Accedere agli oggetti da altre soluzioni
 Per chiamare l'oggetto esposto del componente aggiuntivo VSTO, eseguire i passaggi seguenti nella soluzione client:

1. Ottenere l'oggetto <xref:Microsoft.Office.Core.COMAddIn> che rappresenta il componente aggiuntivo VSTO esposto. I client possono accedere a tutti i componenti aggiuntivi VSTO disponibili usando la proprietà `Application.COMAddIns` nel modello a oggetti dell'applicazione host di Office.

2. Accedere alla proprietà COMAddIn.Object <xref:Microsoft.Office.Core.COMAddIn> dell'oggetto . Questa proprietà restituisce l'oggetto esposto dal componente aggiuntivo VSTO.

3. Chiamare i membri dell'oggetto esposto.

   Il modo in cui si usa il valore restituito della proprietà COMAddIn.Object è diverso per i client VBA e non VBA. Per i client out-of-process, il codice aggiuntivo è necessario per evitare una possibile race condition.

### <a name="access-objects-from-vba-solutions"></a>Accedere agli oggetti dalle soluzioni VBA
 Nell'esempio di codice seguente viene illustrato come utilizzare VBA per chiamare un metodo esposto da VSTO componente aggiuntivo. Questa macro VBA chiama un metodo denominato definito in VSTO componente aggiuntivo denominato `ImportData` **ExcelImportData.** Per visualizzare questo codice nel contesto di una procedura dettagliata più ampia, vedere Procedura dettagliata: Chiamare codice in un componente [VSTO componente aggiuntivo da VBA.](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)

```vb
Sub CallVSTOMethod()
    Dim addIn As COMAddIn
    Dim automationObject As Object
    Set addIn = Application.COMAddIns("ExcelImportData")
    Set automationObject = addIn.Object
    automationObject.ImportData
End Sub
```

### <a name="access-objects-from-non-vba-solutions"></a>Accedere agli oggetti da soluzioni non VBA
 In una soluzione non VBA è necessario eseguire il cast del valore della proprietà COMAddIn.Object all'interfaccia implementata e quindi chiamare i metodi esposti sull'oggetto interfaccia. L'esempio di codice seguente illustra come chiamare il metodo `ImportData` da un componente aggiuntivo VSTO diverso creato usando gli strumenti di sviluppo per Office in Visual Studio.

```vb
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _
    addIn.Object, ExcelImportData.IAddInUtilities)
utilities.ImportData()
```

```csharp
object addInName = "ExcelImportData";
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;
utilities.ImportData();
```

 In questo esempio, se si tenta di eseguire il cast del valore della proprietà COMAddIn.Object alla classe anziché all'interfaccia , il codice `AddInUtilities` `IAddInUtilities` genererà un'eccezione <xref:System.InvalidCastException> .

## <a name="see-also"></a>Vedi anche
- [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md)
- [Procedura dettagliata: Chiamare il codice in VSTO componente aggiuntivo da VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Sviluppare Office soluzioni](../vsto/developing-office-solutions.md)
- [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Personalizzare le funzionalità dell'interfaccia utente usando le interfacce di estendibilità](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
