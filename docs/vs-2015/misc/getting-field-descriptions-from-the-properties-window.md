---
title: Descrizioni dei campi dalla finestra delle proprietà | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 5c7ae9cd659fb317ff74639fa20659296e126d04
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526021"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Descrizioni dei campi dalla finestra Proprietà
Nella parte inferiore della finestra **Proprietà** è disponibile un'area per la descrizione che visualizza informazioni relative al campo della proprietà selezionata. Questa funzionalità è attivata per impostazione predefinita. Se si vuole nascondere il campo della descrizione, fare clic con il pulsante destro del mouse nella finestra **Proprietà** e fare clic su **Descrizione**. In questo modo viene anche rimosso il segno di spunta accanto al titolo **Descrizione** nella finestra del menu. È possibile visualizzare di nuovo il campo con la stessa procedura per riattivare il campo **Descrizione** .  
  
 Le informazioni nel campo della descrizione derivano da <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Per ogni metodo, interfaccia, coclasse e così via può esistere un attributo `helpstring` non localizzato nella libreria dei tipi. Il **delle proprietà** finestra Recupera la stringa da <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Per specificare stringhe della Guida localizzate  
  
1.  Aggiungere l'attributo `helpstringdll` all'istruzione library nella libreria dei tipi (`typelib`).  
  
    > [!NOTE]
    >  Questo passaggio è facoltativo se la libreria dei tipi è inclusa in un file di libreria di oggetti (con estensione olb).  
  
2.  Specificare gli attributi `helpstringcontext` per le stringhe. È anche possibile specificare attributi `helpstring` .  
  
     Questi attributi sono distinti dagli attributi `helpfile` e `helpcontext` , contenuti negli argomenti della Guida nei file effettivi con estensione chm.  
  
 Per recuperare le informazioni di descrizione da visualizzare per il nome della proprietà evidenziata, la **delle proprietà** finestra chiamate <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> per la proprietà è selezionata, specificando il valore desiderato `lcid` attributo per il stringa di output. Internamente <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> trova il file DLL specificato nel `helpstringdll` attributo e le chiamate `DLLGetDocumentation` su tale file con estensione dll con il contesto specificato e `lcid` attributo.  
  
 La firma e l'implementazione di `DLLGetDocumentation` sono:  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 La funzione `DLLGetDocumentation` deve essere un'esportazione definita nel file con estensione def per la DLL.  
  
 Internamente, viene creato un file con estensione olb che è in effetti una DLL. Questa DLL contiene una sola risorsa, il file della libreria dei tipi (con estensione tlb) e una funzione esportata, `DLLGetDocumentation`.  
  
 Nel caso dei file con estensione olb, l'attributo `helpstringdll` è facoltativo perché si tratta dello stesso file che contiene il file con estensione tlb.  
  
 Per recuperare le stringhe da visualizzare nel riquadro **Descrizione** , quindi, è necessario come minimo specificare l'attributo `helpstring` nella libreria dei tipi. Se si vuole localizzare le stringhe, è necessario specificare l'attributo facoltativo `helpstringdll` e l'attributo obbligatorio `helpstringcontext` , quindi implementare `DLLGetDocumentation`.  
  
 Non è necessario implementare altre interfacce quando si recuperano le informazioni localizzate tramite l'attributo `helpstringcontext` dell'istruzione IDL e `DLLGetDocumentation`.  
  
 Un altro modo per ottenere il nome localizzato e la descrizione di una proprietà è implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Per altre informazioni sull'implementazione di questo metodo, vedere [proprietà Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Interfacce e properties Window Fields](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Estensione delle proprietà](../extensibility/internals/extending-properties.md)   
 [helpstringdll](http://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [HelpString](http://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](http://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [HelpContext](http://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [HelpFile](http://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](http://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)