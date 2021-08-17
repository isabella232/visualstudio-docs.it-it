---
title: Elemento VisibilityItem | Microsoft Docs
description: L'elemento VisibilityItem determina la visibilità statica di comandi e barre degli strumenti. Le voci identificano un comando o un menu e un contesto dell'interfaccia utente del comando associato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 95a3cdaddd10cefabaa166e045f5b2f4b1a8d517
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078624"
---
# <a name="visibilityitem-element"></a>VisibilityItem - elemento
`VisibilityItem`L'elemento determina la visibilità statica di comandi e barre degli strumenti. Ogni voce identifica un comando o un menu e anche un contesto dell'interfaccia utente del comando associato. Visual Studio rileva comandi, menu e barre degli strumenti e la relativa visibilità, senza caricare i pacchetti VSPackage che li definiscono. L'IDE usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo per determinare se un contesto dell'interfaccia utente del comando è attivo.

 Dopo il caricamento del pacchetto VSPackage, Visual Studio si aspetta che la visibilità del comando sia determinata dal VSPackage anziché da `VisibilityItem` . Per determinare la visibilità del comando, è possibile implementare il gestore eventi o il metodo , a seconda di come <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> è stato implementato il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> comando.

 Un comando o un menu con un `VisibilityItem` elemento viene visualizzato solo quando il contesto associato è attivo. È possibile associare un singolo comando, menu o barra degli strumenti a uno o più contesti dell'interfaccia utente dei comandi includendo una voce per ogni combinazione di contesto di comando. Se un comando o un menu è associato a più contesti dell'interfaccia utente dei comandi, il comando o il menu è visibile quando uno dei contesti dell'interfaccia utente dei comandi associati è attivo.

 `VisibilityItem`L'elemento si applica solo a comandi, menu e barre degli strumenti, non ai gruppi. Un elemento che non dispone di un elemento `VisibilityItem` correlato è visibile ogni volta che il menu padre è attivo.

## <a name="syntax"></a>Sintassi

```xml
<VisibilityItem
  guid="cmdGuidMyProductCommands"
  id="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID dell'identificatore del comando GUID/ID.|
|id|Obbligatorio. ID dell'identificatore del comando GUID/ID.|
|contesto|Obbligatorio. Contesto dell'interfaccia utente in cui è visibile il comando.|
|Condition|facoltativo. Vedere [Attributi condizionali.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementi figlio
 Nessuno

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[VisibilityConstraints - elemento](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`L'elemento determina la visibilità statica di gruppi di comandi e barre degli strumenti.|

## <a name="remarks"></a>Commenti
 I contesti dell'interfaccia utente Visual Studio standard sono definiti nel file di installazione di *Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h, nonché nelle classi <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> e <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> . Nella classe è definito un set più completo di contesti dell'interfaccia <xref:Microsoft.VisualStudio.VSConstants> utente.

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
- [VisibilityConstraints - elemento](../extensibility/visibilityconstraints-element.md)
- [Visual Studio tabella dei comandi (. Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
