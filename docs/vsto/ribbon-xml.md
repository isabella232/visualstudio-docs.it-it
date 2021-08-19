---
title: Ribbon XML
description: Informazioni su come usare l'elemento Barra multifunzione (XML) se si vuole personalizzare la barra multifunzione in modo che non sia supportata dall'elemento Barra multifunzione (finestra di progettazione visiva).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 23172ee92923faab31a6b5c534076ddf067dc0a0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155551"
---
# <a name="ribbon-xml"></a>Ribbon XML
  L'elemento Barra multifunzione (XML) consente di personalizzare una barra multifunzione tramite XML. Usare l'elemento Barra multifunzione (XML) se si vuole personalizzare la barra multifunzione in modo che non sia supportata dall'elemento Barra multifunzione (finestra di progettazione visiva). Per un confronto tra le attività che è possibile eseguire con ogni elemento, vedere Panoramica [della barra multifunzione.](../vsto/Ribbon-overview.md)

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Aggiungere un elemento Barra multifunzione (XML) a un progetto
 È possibile aggiungere un elemento **Barra multifunzione (XML)** a qualsiasi progetto di Office dalla finestra di dialogo **Aggiungi nuovo elemento** . Visual Studio aggiunge automaticamente i file seguenti al progetto:

- Un file XML della barra multifunzione. Questo file definisce l'interfaccia utente della barra multifunzione. Usare questo file per aggiungere elementi dell'interfaccia utente, ad esempio schede, gruppi e controlli. Per informazioni dettagliate, vedere [Informazioni di riferimento sul file XML della barra](#RibbonDescriptorFile) multifunzione più avanti in questo argomento.

- Un file di codice della barra multifunzione. Questo file contiene la *classe Ribbon*. Il nome della classe corrisponde a quello specificato per l'elemento **Barra multifunzione (XML)** nella finestra di dialogo **Aggiungi nuovo elemento** . Microsoft Office applicazioni usano un'istanza di questa classe per caricare la barra multifunzione personalizzata. Per informazioni dettagliate, vedere [Informazioni di riferimento sulla classe Ribbon](#RibbonExtensionClass) più avanti in questo argomento.

  Per impostazione predefinita, questi file aggiungono un gruppo personalizzato **alla** scheda Componenti aggiuntivi della barra multifunzione.

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Visualizzare la barra multifunzione personalizzata in un'Microsoft Office personalizzata
 Dopo aver aggiunto un elemento **Ribbon (XML)** al progetto, è necessario aggiungere codice alla classe **ThisAddin**, **ThisWorkbook** o **ThisDocument** che esegue l'override del metodo e restituisce la classe RIBBON XML all'applicazione `CreateRibbonExtensibilityObject` Office.

 L'esempio di codice seguente esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce una classe Ribbon XML denominata MyRibbon.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Definire il comportamento della barra multifunzione personalizzata
 È possibile rispondere alle azioni dell'utente, ad esempio fare clic su un pulsante sulla barra multifunzione, creando metodi *di callback*. I metodi di callback sono simili agli eventi nei controlli Windows Form, ma vengono identificati da un attributo nel codice XML dell'elemento dell'interfaccia utente. I metodi vengono scritti nella classe Ribbon e un controllo chiama il metodo con lo stesso nome del valore dell'attributo. Ad esempio, è possibile creare un metodo di callback che viene chiamato quando un utente fa clic su un pulsante sulla barra multifunzione. Per creare un metodo di callback, sono necessari due passaggi:

- Assegnare un attributo a un controllo nel file XML della barra multifunzione che identifica un metodo di callback nel codice.

- Definire il metodo di callback nella classe Ribbon.

> [!NOTE]
> Outlook richiede un ulteriore passaggio. Per altre informazioni, vedere [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

 Per una procedura dettagliata che illustra come automatizzare un'applicazione dalla barra multifunzione, vedere Procedura dettagliata: Creare una scheda [personalizzata tramite XML della barra multifunzione.](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)

### <a name="assign-callback-methods-to-controls"></a>Assegnare metodi di callback ai controlli
 Per assegnare un metodo di callback a un controllo nel file XML della barra multifunzione, aggiungere un attributo che specifica il tipo del metodo di callback e il nome del metodo. Ad esempio, l'elemento seguente definisce un interruttore con un metodo di callback **onAction** denominato `OnToggleButton1`.

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 **onAction** viene chiamato quando l'utente esegue l'attività principale associata a un controllo specifico. Ad esempio, il metodo di callback **onAction** di un interruttore viene chiamato quanto l'utente fa clic sul pulsante.

 Il metodo specificato nell'attributo può avere qualsiasi nome. Tuttavia, deve corrispondere al nome del metodo definito nel file di codice della barra multifunzione.

 Ci sono molti tipi diversi di metodi di callback che è possibile assegnare ai controlli della barra multifunzione. Per un elenco completo dei metodi di callback disponibili per ogni controllo, vedere l'articolo tecnico Personalizzare l'interfaccia utente della barra multifunzione [Office (2007)](/previous-versions/office/developer/office-2007/aa722523(v=office.12))per gli sviluppatori (parte 3 di 3).

### <a name="define-callback-methods"></a><a name="CallBackMethods"></a> Definire i metodi di callback
 Definire i metodi di callback nella classe Ribbon nel file di codice della barra multifunzione. Un metodo di callback presenta diversi requisiti:

- Deve essere dichiarato come pubblico.

- Il nome deve corrispondere al nome di un metodo di callback assegnato a un controllo nel file XML della barra multifunzione.

- La firma deve corrispondere alla firma di un tipo di metodo di callback disponibile per il controllo barra multifunzione associato.

  Per un elenco completo delle firme del metodo di callback per i controlli barra multifunzione, vedere l'articolo tecnico Personalizzare l'interfaccia utente della barra multifunzione [Office (2007)](/previous-versions/office/developer/office-2007/aa722523(v=office.12))per gli sviluppatori (parte 3 di 3). Visual Studio non fornisce supporto IntelliSense per i metodi di callback creati nel file di codice della barra multifunzione. Se si crea un metodo di callback che non corrisponde a una firma valida, il codice verrà compilato, ma non succederà niente quando l'utente fa clic sul controllo.

  Tutti i metodi di callback hanno un parametro <xref:Microsoft.Office.Core.IRibbonControl> che rappresenta il controllo che ha chiamato il metodo. È possibile usare questo parametro per riutilizzare lo stesso metodo di callback per più controlli. L'esempio di codice seguente illustra un metodo di callback **onAction** che esegue attività diverse a seconda del controllo su cui l'utente fa clic.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs" id="Snippet2":::
  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb" id="Snippet2":::

## <a name="ribbon-xml-file-reference"></a><a name="RibbonDescriptorFile"></a> Informazioni di riferimento sul file XML della barra multifunzione
 È possibile definire la barra multifunzione personalizzata aggiungendo elementi e attributi al file XML della barra multifunzione. Per impostazione predefinita, il file XML della barra multifunzione contiene il codice XML seguente.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">
  <ribbon>
    <tabs>
      <tab idMso="TabAddIns">
        <group id="MyGroup"
               label="My Group">
        </group>
      </tab>
    </tabs>
  </ribbon>
</customUI>
```

 La tabella seguente descrive gli elementi predefiniti del file XML della barra multifunzione:

|Elemento|Descrizione|
|-------------|-----------------|
|**customUI**|Rappresenta la barra multifunzione personalizzata nel VSTO del componente aggiuntivo.|
|**Nastro**|Rappresenta la barra multifunzione.|
|**Schede**|Rappresenta un set di schede della barra multifunzione.|
|**Scheda**|Rappresenta una singola scheda della barra multifunzione.|
|**utenti**|Rappresenta un gruppo di controlli nella scheda della barra multifunzione.|

 Questi elementi hanno attributi che specificano l'aspetto e il comportamento della barra multifunzione personalizzata. La tabella seguente descrive gli attributi predefiniti del file XML della barra multifunzione:

|Attributo|Elemento padre|Descrizione|
|---------------|--------------------|-----------------|
|**Onload**|**customUI**|Identifica un metodo chiamato quando l'applicazione carica la barra multifunzione.|
|**Idmso**|**Scheda**|Identifica una scheda incorporata da visualizzare nella barra multifunzione.|
|**id**|**utenti**|Identifica il gruppo.|
|**label**|**utenti**|Specifica il testo visualizzato nel gruppo.|

 Gli elementi e gli attributi predefiniti nel file XML della barra multifunzione sono un piccolo subset degli elementi e degli attributi disponibili. Per un elenco completo degli elementi e degli attributi disponibili, vedere l'articolo tecnico Personalizzare l'interfaccia utente della barra multifunzione [Office (2007)](/previous-versions/office/developer/office-2007/aa338199(v=office.12))per gli sviluppatori (parte 2 di 3).

## <a name="ribbon-class-reference"></a><a name="RibbonExtensionClass"></a> Informazioni di riferimento sulla classe Ribbon
 Visual Studio genera la classe Ribbon nel file di codice della barra multifunzione. Aggiungere i metodi di callback per i controlli sulla barra multifunzione a questa classe. Questa classe implementa l'interfaccia <xref:Microsoft.Office.Core.IRibbonExtensibility> .

 La tabella seguente descrive i metodi predefiniti della classe.

|Metodo|Descrizione|
|------------|-----------------|
|`GetCustomUI`|Restituisce il contenuto del file XML della barra multifunzione. Microsoft Office le applicazioni chiamano questo metodo per ottenere una stringa XML che definisce l'interfaccia utente della barra multifunzione personalizzata. Questo metodo implementa il metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> . **Nota:** `GetCustomUI` deve essere implementato solo per restituire il contenuto del file XML della barra multifunzione. non deve essere usato per inizializzare il componente VSTO componente aggiuntivo.   In particolare, non tentare di visualizzare finestre di dialogo o altre finestre nell'implementazione di `GetCustomUI` . In caso contrario, la barra multifunzione personalizzata potrebbe non funzionare correttamente. Se è necessario eseguire codice per l'inizializzazione del componente aggiuntivo VSTO, aggiungere il codice al gestore eventi `ThisAddIn_Startup` .|
|`OnLoad`|Assegna il parametro <xref:Microsoft.Office.Core.IRibbonControl> al campo `Ribbon` . Microsoft Office le applicazioni chiamano questo metodo quando caricano la barra multifunzione personalizzata. È possibile usare questo campo per aggiornare dinamicamente la barra multifunzione personalizzata. Per altre informazioni, vedere l'articolo tecnico Personalizzare l'interfaccia utente della barra multifunzione Office [(2007)](/previous-versions/office/developer/office-2007/aa338202(v=office.12))per gli sviluppatori (parte 1 di 3).|
|`GetResourceText`|Chiamato dal metodo `GetCustomUI` per ottenere il contenuto del file XML della barra multifunzione.|

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando xml della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
