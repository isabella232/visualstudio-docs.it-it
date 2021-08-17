---
title: Elemento Menu | Microsoft Docs
description: L'elemento Menu definisce una voce di menu. I tipi di menu sono Context, Menu, MenuController, MenuControllerLatched, Toolbar e ToolWindowToolbar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: edcfbaf05cc9590f020eb72d7bd0f7b5002d194b3f56ab7cab0127c3a5df1c0f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388549"
---
# <a name="menu-element"></a>Elemento Menu
Definisce una voce di menu. Questi sono i sei tipi di menu: Contesto, Menu, MenuController, MenuControllerLatched, Barra degli strumenti e ToolWindowToolbar.

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
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore del comando GUID/ID.|
|priority|facoltativo. Valore numerico che specifica la posizione relativa di un menu in un gruppo di menu.|
|ToolbarPriorityInBand|facoltativo. Valore numerico che specifica la posizione relativa di una barra degli strumenti in una banda quando la finestra è ancorata.|
|tipo|facoltativo. Valore enumerato che specifica il tipo di elemento.<br /><br /> Se non è presente, il tipo predefinito è Menu.<br /><br /> Contesto<br /> Menu di scelta rapida visualizzato quando un utente fa clic con il pulsante destro del mouse su una finestra. Un menu di scelta rapida presenta le caratteristiche seguenti:<br /><br /> - Non usa i **campi Padre** **e Priorità** quando il menu deve essere visualizzato come menu di scelta rapida.<br />- Può essere usato come sottomenu e anche come menu di scelta rapida. In questo caso, vengono **rispettati entrambi i campi ID** gruppo e Priorità. <br />- Non è sempre disponibile.<br /><br /> Un menu di scelta rapida viene visualizzato solo quando si verificano le condizioni seguenti:<br /><br /> - Viene visualizzata la finestra che la ospita.<br />- Un gestore del mouse nel pacchetto VSPackage rileva un clic con il pulsante destro del mouse sulla finestra e quindi chiama un metodo che gestisce il comando.<br />- Il menu di scelta rapida viene visualizzato chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> metodo (approccio consigliato) o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> metodo .<br /><br /> Menu<br /> Fornisce un menu a discesa. Un menu a discesa presenta le caratteristiche seguenti:<br /><br /> - Rispetta l'elemento Padre nella relativa definizione.<br />- Deve avere un gruppo Padre o commandPlacement per un gruppo.<br />- Può essere un sottomenu in qualsiasi altro tipo di menu.<br />- Viene visualizzato automaticamente ogni volta che viene visualizzato il menu padre.<br />- Non richiede l'implementazione di codice VSPackage per visualizzarlo.<br /><br /> MenuController<br /> Fornisce un menu a discesa con pulsante di divisione, che viene in genere usato nelle barre degli strumenti. Un menu MenuController presenta le caratteristiche seguenti:<br /><br /> - Deve essere contenuto in un altro menu tramite Padre o CommandPlacement.<br />- Rispetta l'elemento Padre nella relativa definizione.<br />- Può avere qualsiasi tipo di menu come padre.<br />- Viene reso disponibile automaticamente ogni volta che viene visualizzato il menu padre.<br />- Non richiede il supporto a livello di codice per visualizzare il menu.<br /><br /> Nel pulsante di menu viene visualizzato un comando dal menu del pulsante di divisione. Il comando visualizzato ha una delle caratteristiche seguenti:<br /><br /> - È l'ultimo comando usato se il comando è ancora visualizzato e abilitato.<br />- È il primo comando visualizzato.<br /><br /> MenuControllerLatched<br /> Fornisce un menu a discesa con pulsante di divisione per il quale è possibile specificare un comando come selezione predefinita contrassegnando il comando come latch.<br /><br /> Un comando con latch è un comando contrassegnato nel menu come selezionato, in genere visualizzando un segno di spunta. Un comando può essere contrassegnato come latch se ha il flag OLECMDF_LATCHED impostato su di esso in un'implementazione `QueryStatus` del metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> dell'interfaccia . Un menu MenuControllerLatched presenta le caratteristiche seguenti:<br /><br /> - Deve essere contenuto in un altro menu tramite un gruppo padre o CommandPlacement.<br />- Rispetta l'elemento Padre nella relativa definizione.<br />- Può avere qualsiasi tipo di menu come padre.<br />- Viene reso disponibile ogni volta che viene visualizzato il menu padre.<br />- Non richiede il supporto a livello di codice per visualizzare il menu.<br /><br /> Nel pulsante di menu viene visualizzato un comando dal menu del pulsante di divisione. Il comando visualizzato ha una delle caratteristiche seguenti:<br /><br /> - È il primo comando visualizzato a essere latch.<br />- È il primo comando visualizzato.<br /><br /> Barra degli strumenti<br /> Fornisce una barra degli strumenti. Una barra degli strumenti presenta le caratteristiche seguenti:<br /><br /> - Ignora l'elemento Padre nella relativa definizione.<br />- Non può essere reso un sottomenu di qualsiasi gruppo, nemmeno usando CommandPlacement.<br />- Può essere sempre visualizzato scegliendo Barre **degli strumenti** **dal** menu Visualizza.<br />- Può essere visualizzato usando un [elemento VisibilityItem.](../extensibility/visibilityitem-element.md)<br />- Non richiede codice per crearlo. Per un esempio su come creare una barra degli strumenti, vedere [Aggiungere una barra degli strumenti](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Fornisce una barra degli strumenti collegata a una finestra degli strumenti specifica, così come una barra degli strumenti è collegata all'ambiente di sviluppo.<br /><br /> - Ignora l'elemento Padre nella relativa definizione.<br />- Non può essere reso un sottomenu di qualsiasi gruppo, nemmeno usando CommandPlacement.<br />: viene visualizzato solo quando viene visualizzata la finestra degli strumenti che ospita la barra degli strumenti e il pacchetto VSPackage aggiunge in modo esplicito la barra degli strumenti alla finestra degli strumenti. Questa operazione viene in genere eseguita quando la finestra degli strumenti viene creata ottenendo la proprietà host della barra degli strumenti (come rappresentata dall'interfaccia ) dalla cornice della finestra degli strumenti e quindi chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metodo .|
|Condition|facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Padre|facoltativo. Elemento padre della voce di menu.|
|CommandFlag|Obbligatorio. Vedere [Elemento flag di comando](../extensibility/command-flag-element.md). I valori commandFlag validi per un menu sono i seguenti:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible:** questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **DontCache**<br />-   **DynamicVisibility:** questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **Modifiche di testo**<br />-   **TextIsAnchorCommand**|
|Stringhe|Obbligatorio. Vedere [Elemento Strings](../extensibility/strings-element.md). `ButtonText`L'elemento figlio deve essere definito.|
|Annotazione|Commento facoltativo.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu implementati da un vspackage.|

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
- [Visual Studio file della tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
