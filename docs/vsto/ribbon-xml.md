---
title: Elemento XML della barra multifunzione
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aec5c0d2fbbf46978a42cfe2808e708eb4a2b35e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53929575"
---
# <a name="ribbon-xml"></a>Elemento XML della barra multifunzione
  L'elemento della barra multifunzione (XML) consente di personalizzare una barra multifunzione utilizzando XML. Se si desidera personalizzare la barra multifunzione in modo che non è supportato dall'elemento barra multifunzione (finestra di progettazione visiva), usare l'elemento della barra multifunzione (XML). Per un confronto delle operazioni eseguibili con ogni elemento, vedere [Panoramica della barra multifunzione](../vsto/Ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="add-a-ribbon-xml-item-to-a-project"></a>Aggiungere un elemento della barra multifunzione (XML) a un progetto  
 È possibile aggiungere un elemento **Barra multifunzione (XML)** a qualsiasi progetto di Office dalla finestra di dialogo **Aggiungi nuovo elemento** . Visual Studio aggiunge automaticamente i file seguenti al progetto:  
  
- Un file XML della barra multifunzione. Questo file definisce l'interfaccia utente della barra multifunzione. Usare questo file per aggiungere elementi dell'interfaccia utente, ad esempio schede, gruppi e controlli. Per informazioni dettagliate, vedere [riferimento al file XML della barra multifunzione](#RibbonDescriptorFile) più avanti in questo argomento.  
  
- Un file di codice della barra multifunzione. Questo file contiene la *classe Ribbon*. Il nome della classe corrisponde a quello specificato per l'elemento **Barra multifunzione (XML)** nella finestra di dialogo **Aggiungi nuovo elemento** . Applicazioni di Microsoft Office usano un'istanza di questa classe per caricare la barra multifunzione personalizzata. Per informazioni dettagliate, vedere [sulla barra multifunzione riferimento alla classe](#RibbonExtensionClass) più avanti in questo argomento.  
  
  Per impostazione predefinita, questi file aggiungono un gruppo personalizzato per il **Add-Ins** della barra multifunzione.  
  
## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Visualizzare la barra multifunzione personalizzata in un'applicazione Microsoft Office  
 Dopo aver aggiunto un **della barra multifunzione (XML)** elemento al progetto, è necessario aggiungere codice per il **ThisAddin**, **ThisWorkbook**, oppure **ThisDocument** classe che esegue l'override di `CreateRibbonExtensibilityObject` metodo e restituisce il codice XML della barra multifunzione classe all'applicazione di Office.  
  
 L'esempio di codice seguente esegue l'override del metodo `CreateRibbonExtensibilityObject` e restituisce una classe Ribbon XML denominata MyRibbon.  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
## <a name="define-the-behavior-of-the-custom-ribbon"></a>Definire il comportamento della barra multifunzione personalizzata  
 È possibile rispondere alle azioni dell'utente, ad esempio la selezione di un pulsante della barra multifunzione, creando *metodi di callback*. I metodi di callback sono simili agli eventi nei controlli Windows Form, ma vengono identificati da un attributo nel codice XML dell'elemento dell'interfaccia utente. I metodi vengono scritti nella classe Ribbon e un controllo chiama il metodo con lo stesso nome del valore dell'attributo. Ad esempio, è possibile creare un metodo di callback che viene chiamato quando un utente fa clic su un pulsante della barra multifunzione. Per creare un metodo di callback, sono necessari due passaggi:  
  
-   Assegnare un attributo a un controllo nel file XML della barra multifunzione che identifica un metodo di callback nel codice.  
  
-   Definire il metodo di callback nella classe Ribbon.  
  
> [!NOTE]  
>  Outlook richiede un ulteriore passaggio. Per altre informazioni, vedere [personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
 Per una procedura dettagliata che illustri come automatizzare un'applicazione dalla barra multifunzione, vedere [procedura dettagliata: Creare una scheda personalizzata utilizzando XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).  
  
### <a name="assign-callback-methods-to-controls"></a>Assegnare i metodi di callback ai controlli  
 Per assegnare un metodo di callback a un controllo nel file XML della barra multifunzione, aggiungere un attributo che specifica il tipo del metodo di callback e il nome del metodo. Ad esempio, l'elemento seguente definisce un interruttore con un metodo di callback **onAction** denominato `OnToggleButton1`.  
  
```xml  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 **onAction** viene chiamato quando l'utente esegue l'attività principale associata a un controllo specifico. Ad esempio, il metodo di callback **onAction** di un interruttore viene chiamato quanto l'utente fa clic sul pulsante.  
  
 Il metodo specificato nell'attributo può avere qualsiasi nome. Tuttavia, deve corrispondere al nome del metodo definito nel file di codice della barra multifunzione.  
  
 Ci sono molti tipi diversi di metodi di callback che è possibile assegnare ai controlli della barra multifunzione. Per un elenco completo dei metodi di callback disponibili per ogni controllo, vedere l'articolo tecnico [personalizzare l'interfaccia utente della barra multifunzione di Office (2007) per gli sviluppatori (parte 3 di 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)).  
  
###  <a name="CallBackMethods"></a> Definire i metodi di callback  
 Definire i metodi di callback nella classe Ribbon nel file di codice della barra multifunzione. Un metodo di callback presenta diversi requisiti:  
  
- Deve essere dichiarato come pubblico.  
  
- Il nome deve corrispondere al nome di un metodo di callback assegnato a un controllo nel file XML della barra multifunzione.  
  
- La firma deve corrispondere alla firma di un tipo di metodo di callback disponibile per il controllo barra multifunzione associato.  
  
  Per un elenco completo delle firme dei metodi di callback per i controlli della barra multifunzione, vedere l'articolo tecnico [personalizzare l'interfaccia utente della barra multifunzione di Office (2007) per gli sviluppatori (parte 3 di 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)). Visual Studio non fornisce supporto IntelliSense per i metodi di callback creati nel file di codice della barra multifunzione. Se si crea un metodo di callback che non corrisponde a una firma valida, il codice verrà compilato, ma non succederà niente quando l'utente fa clic sul controllo.  
  
  Tutti i metodi di callback hanno un parametro <xref:Microsoft.Office.Core.IRibbonControl> che rappresenta il controllo che ha chiamato il metodo. È possibile usare questo parametro per riutilizzare lo stesso metodo di callback per più controlli. L'esempio di codice seguente illustra un metodo di callback **onAction** che esegue attività diverse a seconda del controllo su cui l'utente fa clic.  
  
  [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
  [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a> Riferimento al file XML della barra multifunzione  
 È possibile definire la barra multifunzione personalizzata aggiungendo elementi e attributi del file XML della barra multifunzione. Per impostazione predefinita, il file XML della barra multifunzione contiene il codice XML seguente.  
  
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
|**customUI**|Rappresenta la barra multifunzione personalizzata nel progetto di componente aggiuntivo VSTO.|  
|**ribbon**|Rappresenta la barra multifunzione.|  
|**Schede**|Rappresenta un set di schede della barra multifunzione.|  
|**scheda**|Rappresenta una singola scheda della barra multifunzione.|  
|**group**|Rappresenta un gruppo di controlli nella scheda della barra multifunzione.|  
  
 Questi elementi hanno gli attributi che specificano l'aspetto e il comportamento della barra multifunzione personalizzata. La tabella seguente descrive gli attributi predefiniti del file XML della barra multifunzione:  
  
|Attributo|Elemento padre|Descrizione|  
|---------------|--------------------|-----------------|  
|**onLoad**|**customUI**|Identifica un metodo che viene chiamato quando l'applicazione carica la barra multifunzione.|  
|**idMso**|**scheda**|Identifica una scheda incorporata da visualizzare nella barra multifunzione.|  
|**ID**|**group**|Identifica il gruppo.|  
|**label**|**group**|Specifica il testo visualizzato nel gruppo.|  
  
 Gli elementi e gli attributi predefiniti nel file XML della barra multifunzione sono un piccolo subset degli elementi e degli attributi disponibili. Per un elenco completo degli attributi ed elementi disponibili, vedere l'articolo tecnico [personalizzare l'interfaccia utente della barra multifunzione di Office (2007) per gli sviluppatori (parte 2 di 3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12)).  
  
##  <a name="RibbonExtensionClass"></a> Riferimento alla classe Ribbon  
 Visual Studio genera la classe Ribbon nel file di codice della barra multifunzione. Aggiungere i metodi di callback per i controlli della barra multifunzione a questa classe. Questa classe implementa l'interfaccia <xref:Microsoft.Office.Core.IRibbonExtensibility> .  
  
 La tabella seguente descrive i metodi predefiniti della classe.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`GetCustomUI`|Restituisce il contenuto del file XML della barra multifunzione. Le applicazioni Microsoft Office chiamano questo metodo per ottenere una stringa XML che definisce l'interfaccia utente per la barra multifunzione personalizzata. Questo metodo implementa il metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> . **Nota:** `GetCustomUI` deve essere implementato solo per restituire il contenuto del file XML della barra multifunzione; e non deve essere usato per inizializzare il componente aggiuntivo VSTO. In particolare, non tentare di visualizzare finestre di dialogo o altre finestre nell'implementazione di `GetCustomUI` . In caso contrario, la barra multifunzione personalizzata potrebbe non funzionare correttamente. Se è necessario eseguire codice per l'inizializzazione del componente aggiuntivo VSTO, aggiungere il codice al gestore eventi `ThisAddIn_Startup` .|  
|`OnLoad`|Assegna il parametro <xref:Microsoft.Office.Core.IRibbonControl> al campo `Ribbon` . Applicazioni di Microsoft Office chiamano questo metodo quando si carica la barra multifunzione personalizzata. È possibile usare questo campo per aggiornare dinamicamente la barra multifunzione personalizzata. Per altre informazioni, vedere l'articolo tecnico [personalizzare l'interfaccia utente della barra multifunzione di Office (2007) per gli sviluppatori (parte 1 di 3)](/previous-versions/office/developer/office-2007/aa338202(v=office.12)).|  
|`GetResourceText`|Chiamato dal metodo `GetCustomUI` per ottenere il contenuto del file XML della barra multifunzione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Procedura dettagliata: Creare una scheda personalizzata utilizzando XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)  
