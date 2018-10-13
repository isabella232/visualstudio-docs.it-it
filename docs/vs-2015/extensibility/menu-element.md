---
title: Menu Element | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9326364e6182441fc3da095cd1cd36a7cb2ed207
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242267"
---
# <a name="menu-element"></a>Elemento Menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definisce una voce di menu. Questi sono i sei tipi di menu: contesto, Menu, MenuController, MenuControllerLatched, sulla barra degli strumenti e ToolWindowToolbar.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|  
|priority|Facoltativo. Valore numerico che specifica la posizione relativa di un menu in un gruppo di menu.|  
|ToolbarPriorityInBand|Facoltativo. Valore numerico che specifica la posizione relativa di una barra degli strumenti in una banda quando la finestra è ancorata.|  
|tipo|Facoltativo. Valore enumerato che specifica il genere dell'elemento.<br /><br /> Se non è presente, il tipo predefinito è Menu.<br /><br /> Contesto<br /> Menu di scelta rapida che viene visualizzato quando un utente fa una finestra. Un menu di scelta rapida presenta le caratteristiche seguenti:<br /><br /> -Non usa i campi padre e la priorità quando il menu deve essere visualizzato come menu di scelta rapida.<br />-Può essere utilizzato come un sottomenu e anche come un menu di scelta rapida. In questo caso, i campi ID gruppo sia priorità vengono rispettati.<br />-È non è sempre disponibile.<br /><br /> Un menu di scelta rapida viene visualizzato solo quando vengono soddisfatte le condizioni seguenti:<br /><br /> : Viene visualizzata la finestra che lo ospita.<br />-Il gestore del mouse nel pacchetto VSPackage rileva un pulsante destro del mouse sulla finestra e quindi chiama un metodo che gestisce il comando.<br />-Menu di scelta rapida viene visualizzato quando si chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> metodo (l'approccio consigliato) o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> (metodo).<br /><br /> Menu<br /> Fornisce un menu di scelta rapida. Un menu a tendina presenta le caratteristiche seguenti:<br /><br /> -Rispetta l'elemento padre nella relativa definizione.<br />-Deve avere un gruppo padre o un CommandPlacement a un gruppo.<br />-Può essere un sottomenu in qualsiasi altro tipo di menu.<br />-Viene visualizzata automaticamente ogni volta che viene visualizzato il menu padre.<br />-Non richiede l'implementazione di VSPackage codice affinché venga visualizzato.<br /><br /> MenuController<br /> Fornisce un menu di scelta rapida di pulsante di menu combinato, che viene in genere usato nelle barre degli strumenti. Un menu MenuController presenta le caratteristiche seguenti:<br /><br /> -Devono essere contenuti in un altro menu tramite padre o CommandPlacement.<br />-Rispetta l'elemento padre nella relativa definizione.<br />-Può contenere qualsiasi tipo di menu padre.<br />-Viene automaticamente reso disponibile ogni volta che viene visualizzato il menu padre.<br />-Non richiede il supporto a livello di codice per rendere il menu visualizzato.<br /><br /> Un comando dal menu di pulsante di menu combinato viene visualizzato sul pulsante di menu. Il comando visualizzato ha una delle caratteristiche seguenti:<br /><br /> -È l'ultimo comando che è stato usato il comando viene ancora visualizzato e attivo.<br />-È il primo comando visualizzato.<br /><br /> MenuControllerLatched<br /> Fornisce un menu di scelta rapida di pulsante di menu combinato per cui un comando può essere specificato come la selezione predefinita contrassegnando il comando come impostare un latch.<br /><br /> Un latch è un comando che è contrassegnato nel menu di scelta come selezionata, in genere visualizzando un segno di spunta. Un comando può essere contrassegnato come impostare un latch in caso affermativo l'OLECMDF_LATCHED flag impostato su di esso in un'implementazione del `QueryStatus` metodo di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Un menu MenuControllerLatched presenta le caratteristiche seguenti:<br /><br /> -Devono essere contenuti in un altro menu attraverso un gruppo padre o CommandPlacement.<br />-Rispetta l'elemento padre nella relativa definizione.<br />-Può contenere qualsiasi tipo di menu padre.<br />-Viene resa disponibile ogni volta che viene visualizzato il menu padre.<br />-Non richiede il supporto a livello di codice per rendere il menu visualizzato.<br /><br /> Un comando dal menu di pulsante di menu combinato viene visualizzato sul pulsante di menu. Il comando visualizzato ha una delle caratteristiche seguenti:<br /><br /> -È il primo comando visualizzato che viene associato.<br />-È il primo comando visualizzato.<br /><br /> ToolBar<br /> Fornisce una barra degli strumenti. Una barra degli strumenti presenta le caratteristiche seguenti:<br /><br /> -Ignora l'elemento padre nella relativa definizione.<br />-Impossibile stabilire un sottomenu di un gruppo, non lo è nemmeno usando CommandPlacement.<br />-È possibile essere sempre visualizzato facendo clic **barre degli strumenti** nel **visualizzazione** menu.<br />-Può essere visualizzato tramite un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-Non richiede alcun codice per la sua creazione. Per un esempio su come creare una barra degli strumenti, vedere [aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Fornisce una barra degli strumenti che è collegato a una finestra degli strumenti specifici, esattamente come una barra degli strumenti è collegato all'ambiente di sviluppo.<br /><br /> -Ignora l'elemento padre nella relativa definizione.<br />-Impossibile stabilire un sottomenu di un gruppo, non lo è nemmeno usando CommandPlacement.<br />-Viene visualizzata solo quando viene visualizzata la finestra degli strumenti che ospita la barra degli strumenti e il pacchetto VSPackage aggiunge in modo esplicito la barra degli strumenti alla finestra degli strumenti. Questa operazione viene in genere eseguita quando la finestra degli strumenti viene creata ottenendo la proprietà dell'host della barra degli strumenti (come rappresentata dai <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfaccia) dal frame della finestra degli strumenti e quindi chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> (metodo).|  
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Padre|Facoltativo. L'elemento padre della voce di menu.|  
|CommandFlag|Obbligatorio. Visualizzare [comando elemento Commandflag](../extensibility/command-flag-element.md). I valori CommandFlag validi per un menu di scelta sono come segue:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **DontCache**<br />-   **DynamicVisibility** -questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|Stringhe|Obbligatorio. Visualizzare [stringhe elemento](../extensibility/strings-element.md). L'elemento figlio `ButtonText` elemento deve essere definito.|  
|Annotazione|Commento facoltativo.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un pacchetto VSPackage.|  
  
## <a name="example"></a>Esempio  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)