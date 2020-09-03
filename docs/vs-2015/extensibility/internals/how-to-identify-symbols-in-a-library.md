---
title: 'Procedura: identificare i simboli in una libreria | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f154c63940189f1a6035246fb7f72ec27be677f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191865"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Procedura: Identificare i simboli in una libreria
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gli strumenti di esplorazione dei simboli visualizzano le visualizzazioni gerarchiche dei simboli. I simboli rappresentano spazi dei nomi, oggetti, classi, membri di classe e altri elementi del linguaggio.  
  
 Ogni simbolo nella gerarchia può essere identificato dalle informazioni di navigazione passate dalla libreria dei simboli a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Gestione oggetti tramite le interfacce seguenti:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 La posizione del simbolo nella gerarchia distingue un simbolo. Consente agli strumenti di esplorazione simboli di passare a un simbolo specifico. Il percorso univoco completo del simbolo determina la posizione. Ogni elemento del percorso è un nodo. Il percorso inizia con il nodo di primo livello e termina con il simbolo specifico. Se, ad esempio, il metodo M1 è un membro della classe C1 e C1 si trova nello spazio dei nomi N1, il percorso completo del metodo M1 è N1. C1. M1. Questo percorso contiene tre nodi: N1, C1 e M1.  
  
 Le informazioni di navigazione consentono al [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestore oggetti di individuare, selezionare e lasciare selezionati i simboli nella gerarchia. Consente lo spostamento da uno strumento di esplorazione a un altro. Quando si usa **Visualizzatore oggetti** per visualizzare i simboli in un [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] progetto, è possibile fare clic con il pulsante destro del mouse su un metodo e avviare lo strumento **Visualizzatore chiamate** per visualizzare il metodo in un grafico delle chiamate.  
  
 Due form descrivono la posizione dei simboli. Il formato canonico è basato sul percorso completo del simbolo. Rappresenta una posizione univoca del simbolo nella gerarchia. È indipendente dallo strumento di esplorazione dei simboli. Per ottenere le informazioni sul formato canonico, il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestore di oggetti chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodo. Il form di presentazione descrive la posizione del simbolo all'interno di uno strumento specifico di esplorazione dei simboli. La posizione del simbolo è relativa alla posizione di altri simboli nella gerarchia. Un simbolo specificato può includere diversi percorsi di presentazione, ma solo un percorso canonico. Se, ad esempio, la classe C1 viene ereditata dalla classe C2 ed entrambe le classi si trovano nello spazio dei nomi N1, il **Visualizzatore oggetti** Visualizza la struttura ad albero gerarchica seguente:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Il percorso canonico della classe C2, in questo esempio, è N1 + C2. Il percorso di presentazione di C2 include i nodi C1 e "basi e interfacce": N1 + C1 + "basi e interfacce" + C2.  
  
 Per ottenere le informazioni sul form di presentazione, il gestore di oggetti chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metodo.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identificazione di un simbolo nella gerarchia  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Per ottenere informazioni sui moduli canonici e di presentazione  
  
1. Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     Il gestore di oggetti chiama questo metodo per ottenere l'elenco di nodi contenuti nel percorso canonico del simbolo.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2. Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     Il gestore di oggetti chiama questo metodo per ottenere l'elenco di nodi contenuti nel percorso di presentazione del simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto degli strumenti per l'esplorazione di simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Procedura: registrare una libreria con gestione oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Procedura: Esporre gli elenchi dei simboli forniti dalla libreria al gestore degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
