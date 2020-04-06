---
title: Elemento Menu Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8dc4731f95e31781f6b10704d7cb14dc83e96d7a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702594"
---
# <a name="menu-element"></a>Elemento di menu
Definisce una voce di menu. Questi sono i sei tipi di menu: Context, Menu, MenuController, MenuControllerLatched, Toolbar e ToolWindowToolbar.

## <a name="syntax"></a>Sintassi

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
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
|guid|Obbligatorio. GUID dell'identificatore di comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore di comando GUID/ID.|
|priority|Facoltativa. Valore numerico che specifica la posizione relativa di un menu in un gruppo di menu.|
|ToolbarPriorityInBandToolbarPriorityInBand|Facoltativa. Valore numerico che specifica la posizione relativa di una barra degli strumenti in una banda quando la finestra è ancorata.|
|type|Facoltativa. Valore enumerato che specifica il tipo di elemento.<br /><br /> Se non è presente, il tipo predefinito è Menu.<br /><br /> Context<br /> Menu di scelta rapida visualizzato quando un utente fa clic con il pulsante destro del mouse su una finestra. Un menu di scelta rapida ha le seguenti caratteristiche:<br /><br /> - Non utilizza i campi **Padre** e **Priorità** quando il menu deve essere visualizzato come menu di scelta rapida.<br />- Può essere utilizzato come un sottomenu e anche come un menu di scelta rapida. In questo caso, vengono rispettati entrambi i campi **ID gruppo** e **Priorità.**<br />- Non è sempre disponibile.<br /><br /> Un menu di scelta rapida viene visualizzato solo quando sono vere le seguenti condizioni:<br /><br /> - Viene visualizzata la finestra che la ospita.<br />- Un gestore del mouse nel pacchetto VSPackage rileva un clic con il pulsante destro del mouse sulla finestra e quindi chiama un metodo che gestisce il comando.- A mouse handler in the VSPackage detects a right-click on the window and then calls a method that handles the command.<br />- Il menu di scelta <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> rapida viene visualizzato chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> il metodo (approccio consigliato) o il metodo .<br /><br /> Menu<br /> Fornisce un menu a discesa. Un menu a discesa ha le seguenti caratteristiche:<br /><br /> - Rispetta il genitore nella sua definizione.<br />- Deve avere un gruppo padre o commandPlacement a un gruppo.- Must have a Parent group, or a CommandPlacement to a group.<br />- Può essere un sottomenu in qualsiasi altro tipo di menu.<br />- Viene visualizzato automaticamente ogni volta che viene visualizzato il relativo menu padre.<br />- Non richiede l'implementazione di codice VSPackage per renderlo visualizzato.- Does not require the implementation of any VSPackage code to make it displayed.<br /><br /> MenuController<br /> Fornisce un menu a discesa dei pulsanti di divisione, che in genere viene utilizzato nelle barre degli strumenti. Un menu MenuController ha le seguenti caratteristiche:<br /><br /> - Deve essere contenuto in un altro menu tramite Parent o CommandPlacement.- Must be contained in another menu through Parent or CommandPlacement.<br />- Rispetta il genitore nella sua definizione.<br />- Può avere qualsiasi tipo di menu come suo genitore.<br />- Viene automaticamente reso disponibile ogni volta che viene visualizzato il relativo menu padre.<br />- Non richiede il supporto a livello di codice per visualizzare il menu.<br /><br /> Sul pulsante del menu del menu di comando viene visualizzato un comando del menu del pulsante di divisione. Il comando visualizzato presenta una delle seguenti caratteristiche:<br /><br /> - È l'ultimo comando utilizzato se il comando è ancora visualizzato e abilitato.<br />- È il primo comando visualizzato.<br /><br /> MenuControllerLatched<br /> Fornisce un menu a discesa dei pulsanti di divisione per il quale è possibile specificare un comando come selezione predefinita contrassegnando il comando come latched.<br /><br /> Un comando agposto è un comando contrassegnato nel menu come selezionato, in genere visualizzando un segno di spunta. Un comando può essere contrassegnato come latched se dispone del `QueryStatus` flag OLECMDF_LATCHED <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> impostato su di esso in un'implementazione del metodo dell'interfaccia. Un menu MenuControllerLatched presenta le caratteristiche seguenti:A MenuControllerLatched menu has the following characteristics:<br /><br /> - Deve essere contenuto in un altro menu tramite un gruppo padre o CommandPlacement.- Must be contained in another menu through a Parent group or CommandPlacement.<br />- Rispetta il genitore nella sua definizione.<br />- Può avere qualsiasi tipo di menu come suo genitore.<br />- Viene reso disponibile ogni volta che viene visualizzato il relativo menu padre.<br />- Non richiede il supporto a livello di codice per visualizzare il menu.<br /><br /> Sul pulsante del menu del menu di comando viene visualizzato un comando del menu del pulsante di divisione. Il comando visualizzato presenta una delle seguenti caratteristiche:<br /><br /> - È il primo comando visualizzato che è aggrovigliato.<br />- È il primo comando visualizzato.<br /><br /> Barra degli strumenti<br /> Fornisce una barra degli strumenti. Una barra degli strumenti ha le seguenti caratteristiche:<br /><br /> - Ignora l'elemento padre nella relativa definizione.<br />- Non può essere creato un sottomenu di alcun gruppo, nemmeno utilizzando CommandPlacement.- Cannot be made a submenu of any group, even by using CommandPlacement.<br />- Può sempre essere visualizzato scegliendo **Barre degli strumenti** dal menu **Visualizza.**<br />- Può essere visualizzato utilizzando un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />- Non richiede alcun codice per crearlo.- Does not require any code to create it. Per un esempio su come creare una barra [degli strumenti,](../extensibility/adding-a-toolbar.md)vedere Aggiungere una barra degli strumenti .<br /><br /> Barra degli strumenti<br /> Fornisce una barra degli strumenti associata a una finestra degli strumenti specifica, proprio come una barra degli strumenti è associata all'ambiente di sviluppo.<br /><br /> - Ignora l'elemento padre nella relativa definizione.<br />- Non può essere creato un sottomenu di alcun gruppo, nemmeno utilizzando CommandPlacement.- Cannot be made a submenu of any group, even by using CommandPlacement.<br />- Viene visualizzato solo quando viene visualizzata la finestra degli strumenti che ospita la barra degli strumenti e il pacchetto VSPackage aggiunge in modo esplicito la barra degli strumenti alla finestra degli strumenti. Questa operazione viene in genere eseguita quando la finestra degli strumenti <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> viene creata ottenendo la proprietà <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> host della barra degli strumenti (come rappresentato dall'interfaccia) dalla cornice della finestra degli strumenti e quindi chiamando il metodo .|
|Condizione|Facoltativa. Consultate [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Parent|Facoltativa. Elemento padre della voce di menu.|
|CommandFlag (Flag di comando)|Obbligatorio. Consultate [Elemento flag di comando](../extensibility/command-flag-element.md). I valori CommandFlag validi per un menu sono i seguenti:<br /><br /> -   **AlwaysCreate (Crea always)**<br />-   **DefaultAncorato**<br />-   **DefaultInvisible** - Questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **Proprietà DontCache**<br />-   **DynamicVisibility** - Questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **IconaTesto**<br />-   **NoCustomize**<br />-   **NotInTBList (informazioni in stato di inademazione**<br />-   **NoToolbarChiudi**<br />-   **Modifiche al testo**<br />-   **TextIsAnchorCommand**|
|Stringhe|Obbligatorio. Consultate [l'elemento Strings](../extensibility/strings-element.md). L'elemento figlio `ButtonText` deve essere definito.|
|Annotazione|Commento facoltativo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un pacchetto VSPackage.|

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
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
