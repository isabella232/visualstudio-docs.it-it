---
title: Elemento VisibilityItem | Microsoft Docs
description: L'elemento VisibilityItem determina la visibilità statica dei comandi e delle barre degli strumenti. Le voci identificano un comando o un menu e un contesto dell'interfaccia utente del comando associato.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 637fea7d203e58c59f85794eeb0f8894eb62e777
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863894"
---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
L' `VisibilityItem` elemento determina la visibilità statica dei comandi e delle barre degli strumenti. Ogni voce identifica un comando o un menu e anche un contesto dell'interfaccia utente del comando associato. Visual Studio rileva i comandi, i menu e le barre degli strumenti e la relativa visibilità, senza caricare i pacchetti VSPackage che li definiscono. L'IDE usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo per determinare se un contesto dell'interfaccia utente del comando è attivo.

 Dopo il caricamento del pacchetto VSPackage, Visual Studio prevede che la visibilità del comando sia determinata dal pacchetto VSPackage anziché da `VisibilityItem` . Per determinare la visibilità del comando, è possibile implementare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore eventi o il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo, a seconda della modalità di implementazione del comando.

 Un comando o un menu con un `VisibilityItem` elemento viene visualizzato solo quando il contesto associato è attivo. È possibile associare un singolo comando, un menu o una barra degli strumenti a uno o più contesti dell'interfaccia utente del comando includendo una voce per ogni combinazione di contesto di comando. Se un comando o un menu è associato a più contesti dell'interfaccia utente del comando, il comando o il menu è visibile quando uno dei contesti dell'interfaccia utente del comando associato è attivo.

 L' `VisibilityItem` elemento si applica solo a comandi, menu e barre degli strumenti, non a gruppi. Un elemento che non dispone di un elemento correlato `VisibilityItem` è visibile ogni volta che il relativo menu padre è attivo.

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
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore del comando GUID/ID.|
|contesto|Obbligatorio. Contesto dell'interfaccia utente in cui il comando è visibile.|
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio
 Nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|L' `VisibilityConstraints` elemento determina la visibilità statica di gruppi di comandi e barre degli strumenti.|

## <a name="remarks"></a>Commenti
 I contesti dell'interfaccia utente di Visual Studio standard vengono definiti nel file \VisualStudioIntegration\Common\Inc\vsshlids.h del *percorso di installazione di Visual Studio SDK*, nonché nelle <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classi e. Nella classe viene definito un set più completo di contesti dell'interfaccia utente <xref:Microsoft.VisualStudio.VSConstants> .

## <a name="example"></a>Esempio

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
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
- [Tabella comandi di Visual Studio (. File vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
