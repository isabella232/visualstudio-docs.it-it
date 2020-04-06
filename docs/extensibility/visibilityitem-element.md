---
title: Elemento VisibilityItem . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698154"
---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
L'elemento `VisibilityItem` determina la visibilità statica di comandi e barre degli strumenti. Ogni voce identifica un comando o un menu e anche un contesto dell'interfaccia utente del comando associato. Visual Studio rileva i comandi, i menu e le barre degli strumenti e la relativa visibilità, senza caricare i package VS che li definiscono. L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> utilizza il metodo per determinare se un contesto dell'interfaccia utente di comando è attivo.

 Dopo il VSPackage viene caricato, Visual Studio prevede che la visibilità del comando venga determinata dal pacchetto VSPackage anziché dal `VisibilityItem`file . Per determinare la visibilità del comando, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> è possibile <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> implementare il gestore eventi o il metodo, a seconda di come è stato implementato il comando.

 Un comando o un `VisibilityItem` menu che dispone di un elemento viene visualizzato solo quando il contesto associato è attivo. È possibile associare un singolo comando, menu o barra degli strumenti a uno o più contesti dell'interfaccia utente dei comandi includendo una voce per ogni combinazione di contesto di comando. Se un comando o un menu è associato a più contesti dell'interfaccia utente dei comandi, il comando o il menu è visibile quando uno dei contesti dell'interfaccia utente dei comandi associati è attivo.

 L'elemento `VisibilityItem` si applica solo ai comandi, ai menu e alle barre degli strumenti, non ai gruppi. Un elemento che non `VisibilityItem` dispone di un elemento correlato è visibile ogni volta che il relativo menu padre è attivo.

## <a name="syntax"></a>Sintassi

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID dell'identificatore di comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore di comando GUID/ID.|
|contesto|Obbligatorio. Contesto dell'interfaccia utente in cui è visibile il comando.|
|Condizione|Facoltativa. Consultate [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio
 nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|L'elemento `VisibilityConstraints` determina la visibilità statica di gruppi di comandi e barre degli strumenti.|

## <a name="remarks"></a>Osservazioni
 I contesti dell'interfaccia utente standard di Visual Studio sono definiti nel percorso di installazione di *Visual Studio SDK,* ovvero nel file e <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> Un set più completo di contesti <xref:Microsoft.VisualStudio.VSConstants> dell'interfaccia utente è definito nella classe.

## <a name="example"></a>Esempio

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)
- [Tabella dei comandi di Visual Studio (. Vsct) File](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
