---
title: 'Procedura: Identificare i simboli in una libreria Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708009"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Procedura: identificare i simboli in una libreriaHow to: Identify symbols in a library
Gli strumenti di esplorazione dei simboli visualizzano viste gerarchiche dei simboli. I simboli rappresentano spazi dei nomi, oggetti, classi, membri di classe e altri elementi del linguaggio.

 Ogni simbolo nella gerarchia può essere identificato dalle informazioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di navigazione passate dalla libreria di simboli al gestore di oggetti tramite le interfacce seguenti:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 La posizione del simbolo nella gerarchia distingue un simbolo. Consente agli strumenti di esplorazione dei simboli di passare a un simbolo specifico. Il percorso univoco e completo del simbolo determina la posizione. Ogni elemento nel percorso è un nodo. Il percorso inizia con il nodo di primo livello e termina con il simbolo specifico. Ad esempio, se il metodo M1 è un membro della classe C1 e C1 è nello spazio dei nomi N1, il percorso completo del metodo M1 è N1. C1. M1. Questo percorso contiene tre nodi: N1, C1 e M1.

 Le informazioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] navigazione consentono al gestore di oggetti di individuare, selezionare e mantenere selezionati i simboli nella gerarchia. Permette di navigare da uno strumento di navigazione all'altro. Durante l'utilizzo **del Visualizzatore oggetti** per esplorare i simboli in un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetto, è possibile fare clic con il pulsante destro del mouse su un metodo e avviare lo strumento Browser **chiamate** per visualizzare il metodo in un grafico delle chiamate.

 Due forme descrivono la posizione del simbolo. La forma canonica si basa sul percorso completo del simbolo. Rappresenta una posizione univoca del simbolo nella gerarchia. È indipendente dallo strumento di esplorazione dei simboli. Per ottenere le informazioni sul [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modulo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> canonico, il gestore di oggetti chiama il metodo. Il modulo di presentazione descrive la posizione del simbolo all'interno di uno specifico strumento di esplorazione dei simboli. La posizione del simbolo è relativa alla posizione di altri simboli nella gerarchia. Un determinato simbolo può avere diversi percorsi di presentazione, ma solo un percorso canonico. Ad esempio, se la classe C1 viene ereditata dalla classe C2 ed entrambe le classi si trovano nello spazio dei nomi N1, nel **Visualizzatore oggetti** viene visualizzato la seguente struttura gerarchica:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Il percorso canonico della classe C2, in questo esempio, è N1 e C2. Il percorso di presentazione di C2 include i nodi C1 e "Bases and Interfaces": N1 - C1 - "Bases and Interfaces" - C2.

 Per ottenere le informazioni sul modulo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> di presentazione, il gestore di oggetti chiama il metodo.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Per ottenere informazioni canoniche e sui moduli di presentazione

1. Implementare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.

     Il gestore di oggetti chiama questo metodo per ottenere l'elenco dei nodi contenuti nel percorso canonico del simbolo.

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

     Il gestore di oggetti chiama questo metodo per ottenere l'elenco dei nodi contenuti nel percorso di presentazione del simbolo.

## <a name="see-also"></a>Vedere anche
- [Supporta gli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Procedura: registrare una libreria con il gestore di oggettiHow to: Register a library with the object manager](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Procedura: esporre elenchi di simboli forniti dalla libreria al gestore di oggettiHow to: Expose lists of symbols provided by the library to the object manager](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
