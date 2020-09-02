---
title: Elemento menu | Microsoft Docs
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
ms.openlocfilehash: 020098a3026f600629b8ab186431a1d2d5d7795a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "87453652"
---
# <a name="menu-element"></a>Elemento menu
Definisce una voce di menu. Questi sono i sei tipi di menu: context, menu, MenuController, MenuControllerLatched, Toolbar e ToolWindowToolbar.

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

### <a name="attributes"></a>Attributes

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore del comando GUID/ID.|
|priority|facoltativo. Valore numerico che specifica la posizione relativa di un menu in un gruppo di menu.|
|ToolbarPriorityInBand|facoltativo. Valore numerico che specifica la posizione relativa di una barra degli strumenti in una banda quando la finestra è ancorata.|
|type|facoltativo. Valore enumerato che specifica il tipo di elemento.<br /><br /> Se non è presente, il tipo predefinito è menu.<br /><br /> Context<br /> Menu di scelta rapida che viene visualizzato quando un utente fa clic con il pulsante destro del mouse su una finestra. Un menu di scelta rapida presenta le caratteristiche seguenti:<br /><br /> -Non usa i campi **padre** e **priorità** quando il menu viene visualizzato come menu di scelta rapida.<br />-Può essere usato come sottomenu e anche come menu di scelta rapida. In questo caso, vengono rispettati sia l' **ID gruppo** che i campi di **priorità** .<br />-Non è sempre disponibile.<br /><br /> Viene visualizzato un menu di scelta rapida solo quando sono soddisfatte le condizioni seguenti:<br /><br /> : Viene visualizzata la finestra che lo ospita.<br />-Un gestore del mouse nel pacchetto VSPackage rileva un clic con il pulsante destro del mouse sulla finestra, quindi chiama un metodo che gestisce il comando.<br />-Il menu di scelta rapida viene visualizzato chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> Metodo (approccio consigliato) o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> metodo.<br /><br /> Menu<br /> Fornisce un menu a discesa. Un menu A discesa presenta le caratteristiche seguenti:<br /><br /> -Rispetta l'elemento padre nella relativa definizione.<br />-Deve avere un gruppo padre o un CommandPlacement a un gruppo.<br />-Può essere un sottomenu in qualsiasi altro tipo di menu.<br />-Viene visualizzato automaticamente ogni volta che viene visualizzato il menu padre.<br />-Non richiede l'implementazione di un codice VSPackage per renderlo visibile.<br /><br /> MenuController<br /> Fornisce un menu a discesa con pulsante di menu combinato, che in genere viene utilizzato nelle barre degli strumenti. Un menu MenuController presenta le caratteristiche seguenti:<br /><br /> -Deve essere contenuto in un altro menu tramite Parent o CommandPlacement.<br />-Rispetta l'elemento padre nella relativa definizione.<br />-Può avere qualsiasi tipo di menu come padre.<br />-Viene reso automaticamente disponibile ogni volta che viene visualizzato il menu padre.<br />-Non richiede il supporto programmatico per fare in modo che il menu venga visualizzato.<br /><br /> Sul pulsante di menu viene visualizzato un comando del menu di menu combinato. Il comando visualizzato presenta una delle caratteristiche seguenti:<br /><br /> -È l'ultimo comando che è stato usato se il comando è ancora visualizzato e attivato.<br />-È il primo comando visualizzato.<br /><br /> MenuControllerLatched<br /> Fornisce un menu a discesa per il quale è possibile specificare un comando come selezione predefinita contrassegnando il comando come bloccato.<br /><br /> Un comando a latch è un comando contrassegnato nel menu come selezionato, in genere visualizzando un segno di spunta. Un comando può essere contrassegnato come bloccato se dispone del flag di OLECMDF_LATCHED impostato in un'implementazione del `QueryStatus` metodo dell' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Un menu MenuControllerLatched presenta le caratteristiche seguenti:<br /><br /> -Deve essere contenuto in un altro menu tramite un gruppo padre o CommandPlacement.<br />-Rispetta l'elemento padre nella relativa definizione.<br />-Può avere qualsiasi tipo di menu come padre.<br />-Viene reso disponibile ogni volta che viene visualizzato il menu padre.<br />-Non richiede il supporto programmatico per fare in modo che il menu venga visualizzato.<br /><br /> Sul pulsante di menu viene visualizzato un comando del menu di menu combinato. Il comando visualizzato presenta una delle caratteristiche seguenti:<br /><br /> -È il primo comando visualizzato che è bloccato.<br />-È il primo comando visualizzato.<br /><br /> Barra degli strumenti<br /> Fornisce una barra degli strumenti. Una barra degli strumenti presenta le caratteristiche seguenti:<br /><br /> -Ignora l'elemento padre nella relativa definizione.<br />-Non può essere costituito da un sottomenu di alcun gruppo, neanche usando CommandPlacement.<br />-È possibile visualizzare sempre facendo clic sulle **barre degli strumenti** dal menu **Visualizza** .<br />-Può essere visualizzato usando un [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-Non richiede alcun codice per crearlo. Per un esempio su come creare una barra degli strumenti, vedere [aggiungere una barra degli strumenti](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Fornisce una barra degli strumenti collegata a una finestra degli strumenti specifica, così come una barra degli strumenti è collegata all'ambiente di sviluppo.<br /><br /> -Ignora l'elemento padre nella relativa definizione.<br />-Non può essere costituito da un sottomenu di alcun gruppo, neanche usando CommandPlacement.<br />-Viene visualizzato solo quando viene visualizzata la finestra degli strumenti che ospita la barra degli strumenti e il pacchetto VSPackage aggiunge esplicitamente la barra degli strumenti alla finestra degli strumenti. Questa operazione viene in genere eseguita quando la finestra degli strumenti viene creata ottenendo la proprietà host della barra degli strumenti (come rappresentata dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfaccia) dalla cornice della finestra degli strumenti e quindi chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metodo.|
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Parent|facoltativo. Elemento padre della voce di menu.|
|CommandFlag|Obbligatorio. Vedere [elemento del flag di comando](../extensibility/command-flag-element.md). I valori CommandFlag validi per un menu sono i seguenti:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** : questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **DontCache**<br />-   **DynamicVisibility** : questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **IconAndText**<br />-   **Nocustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TEXTCHANGES al**<br />-   **TextIsAnchorCommand**|
|Stringhe|Obbligatorio. Vedere [elemento Strings](../extensibility/strings-element.md). `ButtonText`È necessario definire l'elemento figlio.|
|Annotazione|Commento facoltativo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Menu (elemento)](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un VSPackage.|

## <a name="example"></a>Esempio

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"/>
  <CommandFlag>AlwaysCreate</CommandFlag>
  <Strings>
    <ButtonText>Edit Widget</ButtonText>
  </Strings>
</Menu>
```

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
