---
title: Elemento VisibilityItem | Microsoft Docs
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
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c592ac89146f3bc9c26e3c6b1ba11d7fcb277516
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847825"
---
# <a name="visibilityitem-element"></a>Elemento VisibilityItem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il `VisibilityItem` elemento determina la visibilità statica di comandi e le barre degli strumenti. Ogni voce identifica un comando o menu, nonché un contesto dell'interfaccia utente di comando associato. Visual Studio rileva comandi, menu e barre degli strumenti e la visibilità, senza caricare i pacchetti VSPackage che li definiscono. L'IDE Usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodo per determinare se un contesto dell'interfaccia utente del comando è attivo.  
  
 Dopo che il VSPackage viene caricato, Visual Studio si presuppone la visibilità di comandi deve essere determinato dal pacchetto VSPackage anziché `VisibilityItem`. Per determinare la visibilità del comando, è possibile implementare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore dell'evento o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo, a seconda del modo in cui è stato implementato il comando.  
  
 Un comando o un menu dotato di un `VisibilityItem` elemento viene visualizzato solo quando il contesto associato è attivo. È possibile associare un singolo comando, menu o sulla barra degli strumenti con uno o più contesti dell'interfaccia utente di comando includendo una voce per ogni combinazione di comandi al contesto. Se un comando o il menu di scelta è associato a più contesti dei comandi dell'interfaccia utente, quindi il comando o il menu è visibile quando uno dei contesti dell'interfaccia utente di comando associato è attivo.  
  
 Il `VisibilityItem` elemento si applica solo ai comandi, menu e barre degli strumenti, non ai gruppi. Un elemento che non è correlata una `VisibilityItem` elemento è visibile ogni volta che menu padre corrispondente è attivo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
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
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando/ID GUID.|  
|contesto|Obbligatorio. Contesto dell'interfaccia utente in cui il comando è visibile.|  
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 nessuno  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Il `VisibilityConstraints` elemento determina la visibilità statica dei gruppi di comandi e le barre degli strumenti.|  
  
## <a name="remarks"></a>Note  
 I contesti dell'interfaccia utente di Visual Studio standard definiti nel *percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h file nonché come il <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> e <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classi. Un set più completo dei contesti dell'interfaccia utente è definito nel <xref:Microsoft.VisualStudio.VSConstants> classe.  
  
## <a name="example"></a>Esempio  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

